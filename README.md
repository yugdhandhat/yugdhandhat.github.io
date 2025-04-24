<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Jai Jashubai Billing</title>
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
</head>
<body class="bg-gray-100 p-4">
  <div class="max-w-4xl mx-auto bg-white shadow-md rounded p-6">
    <div class="flex items-center mb-6">
      <img src="logo.png" alt="Logo" class="h-16 w-16 mr-4">
      <h1 class="text-2xl font-bold">Jai Jashubai Garment and Accessories</h1>
    </div><form id="billForm">
  <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
    <input type="text" name="receiver" placeholder="Receiver Name" class="border p-2 rounded" required />
    <input type="text" name="contact" placeholder="Contact (Phone or Email)" class="border p-2 rounded" required />
  </div>

  <div class="mt-4">
    <label class="block font-semibold mb-2">Items</label>
    <div id="itemsList" class="space-y-2">
      <div class="grid grid-cols-4 gap-2">
        <input type="text" placeholder="Item" class="border p-1 rounded" required>
        <input type="text" placeholder="Size/Color" class="border p-1 rounded">
        <input type="number" placeholder="Qty" class="border p-1 rounded" required>
        <input type="number" placeholder="Price" class="border p-1 rounded" required>
      </div>
    </div>
    <button type="button" onclick="addItem()" class="mt-2 text-sm text-blue-600">+ Add Item</button>
  </div>

  <button type="submit" class="mt-6 bg-blue-600 text-white px-4 py-2 rounded">Create Bill</button>
</form>

<div id="billPreview" class="mt-10 hidden">
  <h2 class="text-xl font-bold mb-4">Bill Preview</h2>
  <div class="border p-4 rounded bg-gray-50">
    <div id="previewContent"></div>
    <p class="mt-4 italic text-right">Signed: Jai Jashubai Garment and Accessories</p>
  </div>
</div>

  </div>  <script>
    function addItem() {
      const list = document.getElementById("itemsList");
      const div = document.createElement("div");
      div.className = "grid grid-cols-4 gap-2";
      div.innerHTML = `
        <input type="text" placeholder="Item" class="border p-1 rounded" required>
        <input type="text" placeholder="Size/Color" class="border p-1 rounded">
        <input type="number" placeholder="Qty" class="border p-1 rounded" required>
        <input type="number" placeholder="Price" class="border p-1 rounded" required>
      `;
      list.appendChild(div);
    }

    document.getElementById("billForm").onsubmit = function (e) {
      e.preventDefault();
      const form = new FormData(this);
      const receiver = form.get("receiver");
      const contact = form.get("contact");

      const items = Array.from(document.querySelectorAll("#itemsList > div")).map(div => {
        const inputs = div.querySelectorAll("input");
        return {
          name: inputs[0].value,
          size: inputs[1].value,
          qty: parseInt(inputs[2].value),
          price: parseFloat(inputs[3].value),
        };
      });

      let total = 0;
      let html = `<p><strong>Receiver:</strong> ${receiver}</p><p><strong>Contact:</strong> ${contact}</p><table class='w-full mt-4 text-sm'><thead><tr><th>Item</th><th>Size/Color</th><th>Qty</th><th>Price</th><th>Total</th></tr></thead><tbody>`;
      items.forEach(item => {
        const itemTotal = item.qty * item.price;
        total += itemTotal;
        html += `<tr><td>${item.name}</td><td>${item.size}</td><td>${item.qty}</td><td>${item.price}</td><td>${itemTotal}</td></tr>`;
      });
      html += `</tbody></table><p class='mt-4 font-bold'>Grand Total: ₹${total.toFixed(2)}</p>`;

      document.getElementById("previewContent").innerHTML = html;
      document.getElementById("billPreview").classList.remove("hidden");
    }
  </script></body>
</html>
