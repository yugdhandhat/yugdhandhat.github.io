import React from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button";

const products = [ { name: "Golden Pearl Button", image: "https://via.placeholder.com/300x200?text=Golden+Pearl+Button", description: "Elegant golden pearl button perfect for fancy garments." }, { name: "Crystal Dome Button", image: "https://via.placeholder.com/300x200?text=Crystal+Dome+Button", description: "Sparkling crystal dome button for high-end fashion wear." }, { name: "Vintage Floral Button", image: "https://via.placeholder.com/300x200?text=Vintage+Floral+Button", description: "Antique style floral button with a classy look." } ];

export default function JaiJashubaiGarments() { return ( <div className="min-h-screen bg-gray-50 p-6"> <header className="text-center mb-8"> <div className="flex justify-center mb-4"> <img src="/mnt/data/file-KUzxwn8Dbq9CYEB7mceXny" alt="Jai Jashubai Logo" className="h-20" /> </div> <h1 className="text-4xl font-bold">Jai Jashubai Garment and Accessories</h1> <p className="text-lg text-gray-700"> Shop No 109, Haribhai Mistri Chawl, near Milan Bridge, Kothu Wadi, Santacruz (West), Mumbai, Maharashtra 400054 </p> <p className="mt-2 text-gray-600">Your destination for fancy buttons and garment accessories</p> </header>

<section className="grid grid-cols-1 md:grid-cols-3 gap-6 mb-12">
    {products.map((product, index) => (
      <Card key={index} className="shadow-md">
        <img
          src={product.image}
          alt={product.name}
          className="w-full h-48 object-cover rounded-t-2xl"
        />
        <CardContent className="p-4">
          <h2 className="text-xl font-semibold mb-2">{product.name}</h2>
          <p className="text-gray-700 mb-4">{product.description}</p>
          <Button className="w-full">Inquire</Button>
        </CardContent>
      </Card>
    ))}
  </section>

  <section className="mb-12 text-center">
    <h2 className="text-2xl font-semibold mb-4">Find Us Here</h2>
    <div className="w-full h-96">
      <iframe
        title="Jai Jashubai Garment and Accessories Location"
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3769.226268087238!2d72.83649977499185!3d19.1413548503736!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3be7c9029a1140c1%3A0x73504c408f3c0d2e!2sHaribhai%20Mistri%20Chawl%2C%20Khotwadi%2C%20Santacruz%20West%2C%20Mumbai%2C%20Maharashtra%20400054!5e0!3m2!1sen!2sin!4v1713951245173!5m2!1sen!2sin"
        width="100%"
        height="100%"
        allowFullScreen=""
        loading="lazy"
        referrerPolicy="no-referrer-when-downgrade"
        className="rounded-2xl shadow-md"
      ></iframe>
    </div>
  </section>

  <footer className="text-center text-gray-700">
    <p className="text-lg font-semibold mb-2">Contact on WhatsApp:</p>
    <p>Vinod Patel - <a href="https://wa.me/917498277077" className="text-green-600 underline">7498277077</a></p>
    <p>Keyur Patel - <a href="https://wa.me/917506310750" className="text-green-600 underline">7506310750</a></p>
  </footer>
</div>

); }

