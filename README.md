<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Jai Jashubai Garment Accessories</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap');

  /* Reset and base styles */
  * {
    box-sizing: border-box;
  }
  body {
    margin: 0;
    background: linear-gradient(135deg, #f0eafc, #d4c1f9);
    font-family: 'Poppins', sans-serif;
    color: #2f1a6b;
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }
  header {
    padding: 2rem;
    text-align: center;
    background: rgba(63, 41, 125, 0.85);
    color: #fff;
    box-shadow: 0 5px 15px rgba(104, 58, 183, 0.4);
  }
  header h1 {
    font-weight: 600;
    font-size: 2.75rem;
    letter-spacing: 0.11em;
    margin: 0;
    text-transform: uppercase;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
  }
  main {
    flex: 1;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    padding: 3rem 1rem 1.5rem;
    gap: 2.5rem;
    background: linear-gradient(45deg, #faf3ff 0%, #e0d5ff 100%);
  }
  /* Fancy button base styling */
  .button {
    position: relative;
    display: inline-block;
    font-size: 1.15rem;
    font-weight: 600;
    padding: 16px 38px;
    border-radius: 50px;
    cursor: pointer;
    transition: all 0.35s ease;
    text-decoration: none;
    user-select: none;
    box-shadow: 0 6px 16px rgba(104, 58, 183, 0.3);
  }
  /* Button 1: Gradient Glow */
  .btn-glow {
    background: linear-gradient(45deg, #8e2de2, #4a00e0);
    color: #fff;
    border: none;
    box-shadow: 0 0 15px #8e2de2aa;
  }
  .btn-glow:hover, .btn-glow:focus {
    box-shadow:
      0 0 16px #8e2de2ee,
      0 0 25px #4a00e0cc,
      0 0 35px #8e2de2cc;
    transform: scale(1.07);
    outline: none;
  }

  /* Button 2: Neon Outline */
  .btn-neon {
    background: transparent;
    color: #ba68c8;
    border: 2.5px solid #ba68c8;
    overflow: hidden;
  }
  .btn-neon::before {
    content: "";
    position: absolute;
    top: 50%;
    left: -75%;
    width: 200%;
    height: 100%;
    background: linear-gradient(90deg, transparent, #ba68c8, transparent);
    transform: translateY(-50%) skewX(-20deg);
    transition: left 0.45s ease;
    pointer-events: none;
  }
  .btn-neon:hover::before, .btn-neon:focus::before {
    left: 50%;
  }
  .btn-neon:hover, .btn-neon:focus {
    background: #ba68c8;
    color: #fff;
    outline: none;
  }

  /* Button 3: 3D Pressed */
  .btn-3d {
    background: linear-gradient(to bottom, #5f3dc4, #4a2a99);
    color: #efefef;
    border: none;
    box-shadow:
      0 6px #3c2370,
      inset 0 2px rgba(255, 255, 255, 0.15);
    transition: all 0.15s ease-in-out;
  }
  .btn-3d:active {
    box-shadow:
      0 2px #3c2370;
    transform: translateY(4px);
  }
  .btn-3d:hover, .btn-3d:focus {
    background: linear-gradient(to bottom, #7b53e0, #5c3cbb);
    outline: none;
  }

  /* Button 4: Ribbon Style */
  .btn-ribbon {
    color: #fff;
    background: #a64ca6;
    position: relative;
    border: none;
    font-weight: 700;
    padding: 18px 45px 18px 35px;
    transition: background-color 0.3s ease;
  }
  .btn-ribbon::before, .btn-ribbon::after {
    content: "";
    position: absolute;
    border-style: solid;
    pointer-events: none;
  }
  .btn-ribbon::before {
    top: 0; left: 0;
    border-width: 18px 18px 18px 0;
    border-color: transparent #7b3280 transparent transparent;
  }
  .btn-ribbon::after {
    top: 0; right: 0;
    border-width: 18px 0 18px 18px;
    border-color: transparent transparent transparent #7b3280;
  }
  .btn-ribbon:hover, .btn-ribbon:focus {
    background-color: #9a3f9a;
    outline: none;
  }

  /* Button 5: Metallic chrome */
  .btn-metal {
    background: linear-gradient(135deg, #ced4da 0%, #adb5bd 50%, #6c757d 100%);
    color: #212529;
    border: 1px solid #495057;
    font-weight: 600;
    box-shadow: inset 0 2px 6px #fff9, inset 0 -2px 6px #0005;
  }
  .btn-metal:hover, .btn-metal:focus {
    background: linear-gradient(135deg, #adb5bd 0%, #868e96 50%, #495057 100%);
    outline: none;
    color: #f8f9fa;
  }

  /* Contact section styling */
  .contact-section {
    background: #ede7f6cc;
    border-radius: 12px;
    padding: 2rem 3rem;
    margin: 0 auto 3rem auto;
    width: 90%;
    max-width: 480px;
    box-shadow: 0 8px 20px rgba(104, 58, 183, 0.25);
    color: #4a2d7f;
    font-weight: 500;
    text-align: center;
  }
  .contact-section h2 {
    font-size: 1.75rem;
    margin-bottom: 1.2rem;
    font-weight: 600;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    text-shadow: 1px 1px 2px #cfc3ff;
  }
  .contact-list {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  .contact-list li {
    padding: 0.55rem 0;
    font-size: 1.12rem;
    border-bottom: 1px solid #b8a5d6;
  }
  .contact-list li:last-child {
    border-bottom: none;
  }
  /* Phone emoji for a touch of style */
  .phone-icon {
    margin-right: 8px;
  }

  /* Footer */
  footer {
    text-align: center;
    padding: 1.5rem;
    font-size: 0.9rem;
    color: #6b5b9a;
    background: #ede7f6;
    box-shadow: inset 0 1px 3px #bbb;
  }

  /* Responsive scaling for smaller screens */
  @media(max-width: 480px) {
    main {
      padding: 2rem 0.5rem 1rem;
      gap: 1.5rem;
    }
    .button {
      padding: 12px 28px;
      font-size: 1rem;
    }
    .contact-section {
      padding: 1.5rem 1.8rem;
      font-size: 1rem;
    }
    .contact-section h2 {
      font-size: 1.4rem;
      margin-bottom: 0.9rem;
    }
  }
</style>
</head>
<body>
  <header>
    <h1>Jai Jashubai Garment Accessories</h1>
  </header>
  <main>
    <button class="button btn-glow" aria-label="Shop Now">Shop Now</button>
    <button class="button btn-neon" aria-label="Collections">Collections</button>
    <button class="button btn-3d" aria-label="Custom Orders">Custom Orders</button>
    <button class="button btn-ribbon" aria-label="Contact Us">Contact Us</button>
    <button class="button btn-metal" aria-label="About Us">About Us</button>
  </main>
  <section class="contact-section" aria-label="Contact Details">
    <h2>Contact Details</h2>
    <ul class="contact-list">
      <li><span class="phone-icon" aria-hidden="true">📞</span>Vinod Patel: +91 74982 77077</li>
      <li><span class="phone-icon" aria-hidden="true">📞</span>Keyur Patel: +91 75063 10750</li>
    </ul>
  </section>
  <footer>
    &copy; 2024 Jai Jashubai Garment Accessories. All rights reserved.
  </footer>
</body>
</html>
