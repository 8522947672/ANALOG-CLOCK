# ANALOG-CLOCK
In frontend development, an analog clock is a graphical representation of a clock face with hour, minute, and sometimes second hands, typically resembling a traditional clock. It is implemented using HTML, CSS, and JavaScript to create a dynamic and interactive user interface. Here's a breakdown of the components and the general approach for creating an analog clock in frontend development:

### HTML Structure:
The HTML structure will contain the necessary elements for the clock face, hour hand, minute hand, and second hand.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="styles.css">
    <title>Analog Clock</title>
</head>
<body>
    <div class="clock">
        <div class="hand hour"></div>
        <div class="hand minute"></div>
        <div class="hand second"></div>
    </div>
    <script src="script.js"></script>
</body>
</html>
```

### CSS Styles:
The CSS styles are used to position and style the clock and its hands.

```css
body {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
    background-color: #f0f0f0;
}

.clock {
    position: relative;
    width: 200px;
    height: 200px;
    border: 2px solid #333;
    border-radius: 50%;
}

.hand {
    position: absolute;
    transform-origin: 50% 100%;
    background-color: #333;
    transition: transform 0.5s cubic-bezier(0.4, 2.3, 0.3, 1);
}

.hour {
    height: 50px;
    width: 4px;
}

.minute {
    height: 70px;
    width: 2px;
}

.second {
    height: 80px;
    width: 1px;
}
```

### JavaScript Logic:
The JavaScript logic is used to update the rotation of the clock hands based on the current time.

```js
function updateClock() {
    const now = new Date();
    const hours = now.getHours() % 12; // Convert to 12-hour format
    const minutes = now.getMinutes();
    const seconds = now.getSeconds();

    const hourHand = document.querySelector('.hour');
    const minuteHand = document.querySelector('.minute');
    const secondHand = document.querySelector('.second');

    const hourRotation = 360 * (hours / 12) + 360 * (minutes / 60 / 12);
    const minuteRotation = 360 * (minutes / 60) + 360 * (seconds / 60 / 60);
    const secondRotation = 360 * (seconds / 60);

    hourHand.style.transform = `rotate(${hourRotation}deg)`;
    minuteHand.style.transform = `rotate(${minuteRotation}deg)`;
    secondHand.style.transform = `rotate(${secondRotation}deg)`;
}

// Update the clock every second
setInterval(updateClock, 1000);

// Initial update to set the initial position of the hands
updateClock();
```

This JavaScript code calculates the rotation angles for each hand based on the current time and updates the CSS transform property accordingly. The `setInterval` function is used to call the `updateClock` function every second, ensuring that the clock hands move in real-time. The `updateClock` function is also called once initially to set the initial position of the hands when the page loads.

With these HTML, CSS, and JavaScript components, you can create a simple and interactive analog clock in frontend development. You can further enhance the design and add additional features based on your requirements.
