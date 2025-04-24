import React from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button";

const products = [ { name: "Golden Pearl Button", image: "https://via.placeholder.com/300x200?text=Golden+Pearl+Button", description: "Elegant golden pearl button perfect for fancy garments." }, { name: "Crystal Dome Button", image: "https://via.placeholder.com/300x200?text=Crystal+Dome+Button", description: "Sparkling crystal dome button for high-end fashion wear." }, { name: "Vintage Floral Button", image: "https://via.placeholder.com/300x200?text=Vintage+Floral+Button", description: "Antique style floral button with a classy look." } ];

export default function JaiJashubaiGarments() { return ( <div className="min-h-screen bg-gray-50 p-6"> <header className="text-center mb-8"> <h1 className="text-4xl font-bold">Jai Jashubai Garment Accessories</h1> <p className="text-lg text-blue-600 underline"> <a href="https://maps.app.goo.gl/4gu5oUGABgNuHeSJ8" target="_blank" rel="noopener noreferrer"> Visit us on Google Maps </a> </p> <p className="mt-2 text-gray-600">Your destination for fancy buttons and garment accessories</p> </header>

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

  <footer className="text-center text-gray-700">
    <p className="text-lg font-semibold mb-2">Contact on WhatsApp:</p>
    <p>Vinod Patel - <a href="https://wa.me/917498277077" className="text-green-600 underline">7498277077</a></p>
    <p>Keyur Patel - <a href="https://wa.me/917506310750" className="text-green-600 underline">7506310750</a></p>
  </footer>
</div>

); }

