<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Jai Jashubai Billing</title>
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
</head>
<body class="bg-gray-100 p-4">
  <div class="max-w-4xl mx-auto bg-white shadow-md rounded p-6">
    <div class="flex items-center justify-between mb-6">
      <div class="flex items-center">
        <img src="logo.png" alt="Logo" class="h-16 w-16 mr-4">
        <h1 class="text-2xl font-bold">Jai Jashubai Garment and Accessories</h1>
      </div>
      <button onclick="downloadPDF()" class="bg-green-500 text-white px-4 py-2 rounded">Download Bill</button>
    </div><form id="billForm">
  <input type="hidden" name="billId" id="billId">
  <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
    <input type="text" name="receiver" placeholder="Receiver Name" class="border p-2 rounded" required />
    <input type="text" name="contact" placeholder="WhatsApp Number (with country code)" class="border p-2 rounded" required />
  </div>

  <div class="mt-4">
    <label class="block font-semibold mb-2">Items</label>
    <div id="itemsList" class="space-y-2">
      <div class="grid grid-cols-4 gap-2">
        <input type="text" placeholder="Item" class="border p-1 rounded" required>
        <input type="text" placeholder="Size/Color" class="border p-1 rounded">
        <input type="number" step="1" placeholder="Qty" class="border p-1 rounded" required>
        <input type="number" step="0.01" placeholder="Price" class="border p-1 rounded" required>
      </div>
    </div>
    <button type="button" onclick="addItem()" class="mt-2 text-sm text-blue-600">+ Add Item</button>
  </div>

  <button type="submit" class="mt-6 bg-blue-600 text-white px-4 py-2 rounded">Save Bill</button>
</form>

<div id="billPreview" class="mt-10 hidden">
  <h2 class="text-xl font-bold mb-4">Bill Preview</h2>
  <div class="border p-4 rounded bg-gray-50">
    <div id="previewContent"></div>
    <p class="mt-4 italic text-right">Signed: Jai Jashubai Garment and Accessories</p>
    <div class="mt-4 flex gap-4">
      <button onclick="downloadPDF()" class="bg-green-500 text-white px-4 py-2 rounded">Download PDF</button>
      <button onclick="sendWhatsApp()" class="bg-teal-500 text-white px-4 py-2 rounded">Send via WhatsApp</button>
    </div>
  </div>
</div>

<div class="mt-10">
  <h2 class="text-lg font-bold mb-2">Search Saved Bills</h2>
  <input type="text" id="searchInput" placeholder="Enter Receiver Name" class="border p-2 w-full rounded mb-2" oninput="searchBills()">
  <ul id="searchResults" class="space-y-2"></ul>
</div>

  </div>  <script>
    const { jsPDF } = window.jspdf;

    function addItem() {
      const list = document.getElementById("itemsList");
      const div = document.createElement("div");
      div.className = "grid grid-cols-4 gap-2";
      div.innerHTML = `
        <input type="text" placeholder="Item" class="border p-1 rounded" required>
        <input type="text" placeholder="Size/Color" class="border p-1 rounded">
        <input type="number" step="1" placeholder="Qty" class="border p-1 rounded" required>
        <input type="number" step="0.01" placeholder="Price" class="border p-1 rounded" required>
      `;
      list.appendChild(div);
    }

    document.getElementById("billForm").onsubmit = function (e) {
      e.preventDefault();
      const form = new FormData(this);
      const receiver = form.get("receiver");
      const contact = form.get("contact");
      const billId = form.get("billId") || Date.now().toString();

      const items = Array.from(document.querySelectorAll("#itemsList > div")).map(div => {
        const inputs = div.querySelectorAll("input");
        return {
          name: inputs[0].value,
          size: inputs[1].value,
          qty: parseFloat(inputs[2].value),
          price: parseFloat(inputs[3].value),
        };
      });

      const bill = { id: billId, receiver, contact, items, date: new Date().toLocaleString() };
      localStorage.setItem(`bill-${billId}`, JSON.stringify(bill));

      renderBill(bill);
      document.getElementById("billId").value = billId;
    }

    function renderBill(bill) {
      let total = 0;
      let html = `<p><strong>Receiver:</strong> ${bill.receiver}</p><p><strong>Contact:</strong> ${bill.contact}</p><p><strong>Date:</strong> ${bill.date}</p><table class='w-full mt-4 text-sm'><thead><tr><th>Item</th><th>Size/Color</th><th>Qty</th><th>Price</th><th>Total</th></tr></thead><tbody>`;
      bill.items.forEach(item => {
        const itemTotal = item.qty * item.price;
        total += itemTotal;
        html += `<tr><td>${item.name}</td><td>${item.size}</td><td>${item.qty}</td><td>₹${item.price.toFixed(2)}</td><td>₹${itemTotal.toFixed(2)}</td></tr>`;
      });
      html += `</tbody></table><p class='mt-4 font-bold'>Grand Total: ₹${total.toFixed(2)}</p>`;
      document.getElementById("previewContent").innerHTML = html;
      document.getElementById("billPreview").classList.remove("hidden");
    }

    function searchBills() {
      const query = document.getElementById("searchInput").value.toLowerCase();
      const resultList = document.getElementById("searchResults");
      resultList.innerHTML = "";

      Object.keys(localStorage).forEach(key => {
        if (key.startsWith("bill-")) {
          const bill = JSON.parse(localStorage.getItem(key));
          if (bill.receiver.toLowerCase().includes(query)) {
            const li = document.createElement("li");
            li.className = "bg-gray-200 p-2 rounded cursor-pointer";
            li.textContent = `${bill.receiver} - ${bill.date}`;
            li.onclick = () => loadBill(bill);
            resultList.appendChild(li);
          }
        }
      });
    }

    function loadBill(bill) {
      document.querySelector("input[name='receiver']").value = bill.receiver;
      document.querySelector("input[name='contact']").value = bill.contact;
      document.getElementById("billId").value = bill.id;

      const itemsList = document.getElementById("itemsList");
      itemsList.innerHTML = "";
      bill.items.forEach(item => {
        const div = document.createElement("div");
        div.className = "grid grid-cols-4 gap-2";
        div.innerHTML = `
          <input type="text" value="${item.name}" class="border p-1 rounded" required>
          <input type="text" value="${item.size}" class="border p-1 rounded">
          <input type="number" value="${item.qty}" step="1" class="border p-1 rounded" required>
          <input type="number" value="${item.price}" step="0.01" class="border p-1 rounded" required>
        `;
        itemsList.appendChild(div);
      });

      renderBill(bill);
    }

    function downloadPDF() {
      const doc = new jsPDF();
      doc.text("Jai Jashubai Garment and Accessories", 10, 10);
      doc.fromHTML(document.getElementById("previewContent"), 10, 20);
      doc.save("bill.pdf");
    }

    function sendWhatsApp() {
      const receiver = document.querySelector("input[name='receiver']").value;
      const contact = document.querySelector("input[name='contact']").value;
      const items = Array.from(document.querySelectorAll("#itemsList > div"));
      let msg = `Jai Jashubai Garment & Accessories Bill%0AReceiver: ${receiver}%0A`;
      let total = 0;

      items.forEach(div => {
        const [name, size, qty, price] = div.querySelectorAll("input");
        const qtyVal = parseFloat(qty.value);
        const priceVal = parseFloat(price.value);
        const subtotal = qtyVal * priceVal;
        total += subtotal;
        msg += `• ${name.value} (${size.value}) x${qtyVal} @₹${priceVal.toFixed(2)} = ₹${subtotal.toFixed(2)}%0A`;
      });

      msg += `%0AGrand Total: ₹${total.toFixed(2)}%0AThank you!`;
      window.open(`https://wa.me/${contact}?text=${msg}`, '_blank');
    }
  </script></body>
</html>
