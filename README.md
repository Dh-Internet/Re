<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DishHome Internet Callback</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f8f8f8;
            margin: 0;
            padding: 20px;
        }
        .container {
            max-width: 500px;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            margin: auto;
        }
        img {
            max-width: 100%;
            height: auto;
        }
        .form-group {
            margin: 15px 0;
        }
        input {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background: red;
            color: white;
            padding: 10px 15px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background: darkred;
        }
        .call-now {
            display: block;
            margin-top: 20px;
            background: green;
            text-decoration: none;
            color: white;
            padding: 10px 15px;
            border-radius: 5px;
            font-size: 16px;
        }
        .thank-you {
            display: none; /* Hidden by default */
            font-size: 24px;
            color: green;
            margin-top: 20px;
        }
    </style>
    <script>
        window.onload = function() {
            // Extract URL parameters
            const urlParams = new URLSearchParams(window.location.search);
            const name = urlParams.get('name');
            const phone = urlParams.get('phone');

            // Auto-fill the form fields if parameters exist
            if (name) {
                document.getElementById('name').value = name;
            }
            if (phone) {
                document.getElementById('phone').value = phone;
            }

            // Handle form submission
            const form = document.getElementById('callback-form');
            form.addEventListener('submit', function(event) {
                event.preventDefault(); // Prevent the default form submission

                // Show the "Thank You" message
                document.getElementById('thank-you').style.display = 'block';

                // Redirect to WhatsApp with the filled form data
                const whatsappLink = `https://api.whatsapp.com/send?phone=9705054001&text=Full%20Name:%20${encodeURIComponent(document.getElementById('name').value)}%0APhone%20Number:%20${encodeURIComponent(document.getElementById('phone').value)}`;
                window.open(whatsappLink, '_blank');

                // Close the window after 3 seconds
                setTimeout(function() {
                    window.close();
                }, 3000); // 3000 milliseconds = 3 seconds
            });
        }
    </script>
</head>
<body>
    <div class="container">
        <img src="sabina1.png" alt="Promotional Offer">
        <h2>Request a Call Back</h2>
        <form id="callback-form" action="https://api.whatsapp.com/send" method="GET" target="_blank">
            <div class="form-group">
                <label for="name">Full Name:</label>
                <input type="text" id="name" name="text" required>
            </div>
            <div class="form-group">
                <label for="phone">Phone Number:</label>
                <input type="tel" id="phone" name="phone" required>
            </div>
            <button type="submit">Submit</button>
        </form>
        <div id="thank-you" class="thank-you">Thank You! We will contact you shortly.</div>
        <a href="tel:9705054001" class="call-now">📞 Call Now: 9705054001</a>
    </div>
</body>
</html>

