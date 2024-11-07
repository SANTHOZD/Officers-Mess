<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mess Office Booking</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 0; padding: 0; background-color: #f4f4f4; }
        header { background: #4CAF50; color: #fff; padding: 20px; text-align: center; }
        .container { padding: 20px; max-width: 800px; margin: auto; }
        .room-type { margin-bottom: 20px; }
        .room-type h2 { color: #333; }
        .room-type p { color: #555; }
        .availability { margin-top: 10px; }
        .availability input { padding: 10px; width: 100%; max-width: 300px; }
        .availability button { padding: 10px 15px; background: #4CAF50; color: #fff; border: none; cursor: pointer; }
        .availability button:hover { background: #45a049; }
        .booking-form { margin-top: 30px; padding: 20px; border: 1px solid #ddd; background: #fff; }
        .booking-form h3 { margin-top: 0; }
        .booking-form label { display: block; margin: 10px 0 5px; }
        .booking-form input, .booking-form select { width: 100%; padding: 8px; margin-bottom: 10px; }
        .booking-form button { width: 100%; padding: 10px; background: #4CAF50; color: #fff; border: none; cursor: pointer; }
        .booking-form button:hover { background: #45a049; }
    </style>
</head>
<body>

<header>
    <h1>Mess Office Booking</h1>
    <p>Accommodation & Food Services</p>
</header>

<div class="container">
    <div class="room-type">
        <h2>Suite Rooms</h2>
        <p>Luxurious suites with air-conditioning, attached bathrooms, and premium amenities.</p>
        <p>Price: $100 per night</p>
        <div class="availability">
            <label for="suite-date">Check Availability:</label>
            <input type="date" id="suite-date">
            <button onclick="checkAvailability('suite')">Check</button>
            <p id="suite-availability"></p>
        </div>
    </div>

    <div class="room-type">
        <h2>Executive Single Rooms</h2>
        <p>Comfortable single rooms with air-conditioning and attached bathrooms.</p>
        <p>Price: $70 per night</p>
        <div class="availability">
            <label for="executive-date">Check Availability:</label>
            <input type="date" id="executive-date">
            <button onclick="checkAvailability('executive')">Check</button>
            <p id="executive-availability"></p>
        </div>
    </div>

    <div class="room-type">
        <h2>Non-Gazetted Officer Non-AC Rooms</h2>
        <p>Affordable non-AC rooms with basic amenities.</p>
        <p>Price: $50 per night</p>
        <div class="availability">
            <label for="nonac-date">Check Availability:</label>
            <input type="date" id="nonac-date">
            <button onclick="checkAvailability('nonac')">Check</button>
            <p id="nonac-availability"></p>
        </div>
    </div>

    <div class="booking-form">
        <h3>Book a Room</h3>
        <form id="booking-form">
            <label for="room-type">Room Type:</label>
            <select id="room-type">
                <option value="suite">Suite Room - $100/night</option>
                <option value="executive">Executive Single Room - $70/night</option>
                <option value="nonac">Non-AC Room - $50/night</option>
            </select>
            
            <label for="checkin-date">Check-In Date:</label>
            <input type="date" id="checkin-date" required>
            
            <label for="checkout-date">Check-Out Date:</label>
            <input type="date" id="checkout-date" required>
            
            <label for="name">Your Name:</label>
            <input type="text" id="name" required>
            
            <label for="email">Email Address:</label>
            <input type="email" id="email" required>
            
            <button type="button" onclick="submitBooking()">Submit Booking</button>
        </form>
        <p id="booking-confirmation"></p>
    </div>
</div>

<script>
const availabilityData = {
        suite: ["2024-11-10", "2024-11-12"], // example unavailable dates
        executive: ["2024-11-15"],
        nonac: ["2024-11-20"]
    };

    function checkAvailability(roomType) {
        const date = document.getElementById(roomType + '-date').value;
        const availability = availabilityData[roomType] || [];
        const availabilityMessage = availability.includes(date) ? "Not available" : "Available";
        document.getElementById(roomType + '-availability').innerText = availabilityMessage;
    }

    function submitBooking() {
        const roomType = document.getElementById("room-type").value;
        const checkin = document.getElementById("checkin-date").value;
        const checkout = document.getElementById("checkout-date").value;
        const name = document.getElementById("name").value;
        const email = document.getElementById("email").value;

        if (!checkin  !checkout  !name || !email) {
            alert("Please fill in all booking details.");
            return;
        }

        document.getElementById("booking-confirmation").innerText = 
            Thank you, ${name}! Your booking for a ${roomType} from ${checkin} to ${checkout} has been submitted. We will contact you at ${email}.;
        
        document.getElementById("booking-form").reset();
    }
</script>

</body>
</html>
