# Events in JavaScript

### Events in JavaScript are actions or occurrences that happen in the browser, such as user interactions (clicking, typing, scrolling) or system events (loading, resizing). JavaScript provides event handling mechanisms to respond to these actions.

## 1. Event Handling Methods
#### a) Using HTML Attributes (Inline Event)

    <button onclick="alert('Button Clicked!')">Click Me</button>
    
        Not recommended for large applications as it mixes JavaScript with HTML.

#### b) Using JavaScript Event Properties
    
    const btn = document.getElementById("myButton");
    btn.onclick = function() {
        alert("Button Clicked!");
    };
    
        Assigns an event to an element, but overwrites any existing event handlers.

#### c) Using addEventListener (Recommended)

    const btn = document.getElementById("myButton");
    btn.addEventListener("click", function() {
        alert("Button Clicked!");
    });
    
        Allows multiple event listeners on the same element.
    
