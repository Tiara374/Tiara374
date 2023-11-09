<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Zodiac Vibes</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f4f4f4;
        }
        #horoscope-form {
            margin-bottom: 20px;
        }
        #reading {
            margin-top: 20px;
            padding: 10px;
            background-color: #fff;
            border-radius: 5px;
        }
    </style>
</head>
<body>

<h1>Zodiac Vibes</h1>

<!-- Horoscope form where the user can select their zodiac sign and day -->
<form id="horoscope-form">
    <label for="sign">Your Zodiac Sign:</label>
    <select id="sign" name="sign">
        <option value="aries">Aries</option>
        <option value="taurus">Taurus</option>
        <option value="gemini">Gemini</option>
        <option value="cancer">Cancer</option>
        <option value="leo">Leo</option>
        <option value="virgo">Virgo</option>
        <option value="libra">Libra</option>
        <option value="scorpio">Scorpio</option>
        <option value="sagittarius">Sagittarius</option>
        <option value="capricorn">Capricorn</option>
        <option value="aquarius">Aquarius</option>
        <option value="pisces">Pisces</option>
    </select>
    
    <label for="day">Day:</label>
    <select id="day" name="day">
        <option value="today">Today</option>
        <option value="yesterday">Yesterday</option>
        <option value="tomorrow">Tomorrow</option>
    </select>

    <button type="submit">Get Horoscope</button>
</form>

<!-- The div where the horoscope will be displayed -->
<div id="reading"></div>

<script>
// JavaScript to handle the form submission and fetch the horoscope
document.getElementById("horoscope-form").addEventListener("submit", function(event){
    event.preventDefault(); // Prevent the form from submitting the traditional way
    let sign = document.getElementById("sign").value;
    let day = document.getElementById("day").value;
    getHoroscope(sign, day); // Call the function to get the horoscope
});

function getHoroscope(sign, day) {
    let apiUrl = 'https://aztro.sameerkumar.website/'; // API endpoint

    // Details for the POST request
    let options = {
        method: 'POST',
        headers: {
            'Content-Type': 'application/x-www-form-urlencoded'
        },
        body: `sign=${sign}&day=${day}`
    };

    // Fetch the horoscope from the Aztro API
    fetch(apiUrl, options)
        .then(response => response.json())
        .then(data => {
            // Update the page with the horoscope description
            document.getElementById("reading").innerText = data.description;
        })
        .catch(error => {
            // If an error occurs, log it and update the page with an error message
            console.error('Error:', error);
            document.getElementById("reading").innerText = "An error occurred while fetching your horoscope.";
        });
}
</script>

</body>
</html>
