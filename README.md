# Day-6-Task-6
index.html


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Contact Form</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>

  <div class="container">
    <h1>Contact Us</h1>
    <form id="contactForm" novalidate>
      <label for="name">Name:</label>
      <input type="text" id="name" name="name" />
      <span class="error" id="nameError"></span>

      <label for="email">Email:</label>
      <input type="email" id="email" name="email" />
      <span class="error" id="emailError"></span>

      <label for="message">Message:</label>
      <textarea id="message" name="message" rows="5"></textarea>
      <span class="error" id="messageError"></span>

      <button type="submit">Submit</button>
    </form>

    <div id="successMessage" class="success"></div>
  </div>

  <script src="script.js"></script>
</body>
</html>


style.css
body {
  font-family: Arial, sans-serif;
  background: #f7f7f7;
  margin: 0;
  padding: 40px;
}

.container {
  max-width: 500px;
  margin: auto;
  background: #fff;
  padding: 30px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
  text-align: center;
  color: #333;
}

form {
  display: flex;
  flex-direction: column;
}

label {
  margin-top: 15px;
  font-weight: bold;
}

input, textarea {
  padding: 10px;
  margin-top: 5px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 14px;
}

button {
  margin-top: 20px;
  padding: 10px;
  background-color: #007bff;
  color: white;
  font-size: 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

.error {
  color: red;
  font-size: 13px;
  margin-top: 3px;
}

.success {
  margin-top: 20px;
  color: green;
  font-size: 16px;
  text-align: center;
}


script.js
document.getElementById("contactForm").addEventListener("submit", function (e) {
  e.preventDefault();

  // Clear previous messages
  document.getElementById("nameError").textContent = "";
  document.getElementById("emailError").textContent = "";
  document.getElementById("messageError").textContent = "";
  document.getElementById("successMessage").textContent = "";

  // Input values
  const name = document.getElementById("name").value.trim();
  const email = document.getElementById("email").value.trim();
  const message = document.getElementById("message").value.trim();

  // Validation flag
  let isValid = true;

  // Name validation
  if (name === "") {
    document.getElementById("nameError").textContent = "Name is required.";
    isValid = false;
  }

  // Email validation using regex
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  if (email === "") {
    document.getElementById("emailError").textContent = "Email is required.";
    isValid = false;
  } else if (!emailRegex.test(email)) {
    document.getElementById("emailError").textContent = "Invalid email format.";
    isValid = false;
  }

  // Message validation
  if (message === "") {
    document.getElementById("messageError").textContent = "Message cannot be empty.";
    isValid = false;
  }

  // If all valid
  if (isValid) {
    document.getElementById("successMessage").textContent =
      "Thank you! Your message has been successfully submitted.";
    document.getElementById("contactForm").reset();
  }
});


OUTCOME:-

Client-side validation using JavaScript.

Regex for email format checking.   

Error messages shown below respective fields.

Prevents submission on invalid inputs.

Displays a success message on valid submission.                            

No backend/server needed—fully static.
