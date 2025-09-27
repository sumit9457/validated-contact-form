# validated-contact-form
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Contact Form with Validation</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f0f4f8;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .form-container {
      background: #fff;
      padding: 25px;
      border-radius: 12px;
      box-shadow: 0px 6px 15px rgba(0,0,0,0.2);
      width: 100%;
      max-width: 400px;
    }
    .form-container h2 {
      text-align: center;
      margin-bottom: 20px;
      color: #333;
    }
    label {
      font-weight: bold;
      display: block;
      margin: 10px 0 5px;
    }
    input, textarea {
      width: 100%;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 14px;
    }
    textarea {
      resize: none;
      height: 100px;
    }
    button {
      margin-top: 15px;
      width: 100%;
      padding: 12px;
      border: none;
      border-radius: 8px;
      background: #4CAF50;
      color: white;
      font-size: 16px;
      cursor: pointer;
    }
    button:hover {
      background: #45a049;
    }
    .error {
      color: red;
      font-size: 13px;
    }
  </style>
</head>
<body>
  <div class="form-container">
    <h2>Contact Us</h2>
    <form id="contactForm">
      <label for="name">Name:</label>
      <input type="text" id="name" name="name" required>

      <label for="email">Email:</label>
      <input type="email" id="email" name="email" required>

      <label for="phone">Phone:</label>
      <input type="tel" id="phone" name="phone" pattern="[0-9]{10}" required placeholder="10-digit number">

      <label for="message">Message:</label>
      <textarea id="message" name="message" required></textarea>

      <div id="errorMsg" class="error"></div>

      <button type="submit">Submit</button>
    </form>
  </div>

  <script>
    document.getElementById("contactForm").addEventListener("submit", function(event){
      event.preventDefault(); // prevent submission until validated
      let name = document.getElementById("name").value.trim();
      let email = document.getElementById("email").value.trim();
      let phone = document.getElementById("phone").value.trim();
      let message = document.getElementById("message").value.trim();
      let errorMsg = document.getElementById("errorMsg");

      if(name === "" || email === "" || phone === "" || message === ""){
        errorMsg.textContent = "⚠️ All fields are required!";
      } else if(!/^[0-9]{10}$/.test(phone)) {
        errorMsg.textContent = "⚠️ Phone must be 10 digits!";
      } else {
        errorMsg.textContent = "";
        alert("Form submitted successfully ✅");
        document.getElementById("contactForm").reset();
      }
    });
  </script>
</body>
</html>

