# Events in JavaScript

### Events in JavaScript are actions or occurrences that happen in the browser, such as user interactions (clicking, typing, scrolling) or system events (loading, resizing). JavaScript provides event handling mechanisms to respond to these actions.

### Quick Sumamry
+ Use addEventListener() for flexibility.
+ Utilize event delegation for efficiency.
+ Understand event propagation (bubbling & capturing).
+ Use preventDefault() to stop unwanted behavior.

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
    

## 2. Common Event Types
### Mouse Events

+ click
+ dblclick
+ mousedown
+ mouseup
+ mousemove
+ mouseenter
+ mouseleave

        document.addEventListener("click", function() {
            console.log("Mouse clicked!");
        });

### Keyboard Events

+ keydown
+ keyup
+ keypress (deprecated)

        document.addEventListener("keydown", function(event) {
            console.log("Key pressed:", event.key);
        });

### Form Events

+ submit
+ change
+ focus
+ blur

        document.getElementById("myForm").addEventListener("submit", function(event) {
            event.preventDefault(); // Prevent form submission
            alert("Form submitted!");
        });

### Window Events

+ load
+ resize
+ scroll
+ beforeunload

        window.addEventListener("resize", function() {
            console.log("Window resized!");
        });

## 3. Event Object (event)

### The event object contains details about the event.

        document.addEventListener("click", function(event) {
            console.log("Clicked at:", event.clientX, event.clientY);
        });

+ event.clientX, event.clientY → Mouse coordinates
+ event.target → The element that triggered the event

## 4. Event Propagation (Bubbling & Capturing)
### Bubbling (Default)
#### Events move from the target element up to the root.

        document.getElementById("child").addEventListener("click", function() {
            alert("Child Clicked!");
        });
        document.getElementById("parent").addEventListener("click", function() {
            alert("Parent Clicked!");
        });

+ Clicking #child triggers both handlers (child first, then parent).

### Capturing (Use { capture: true })

#### Events move from the root down to the target.

        document.getElementById("parent").addEventListener("click", function() {
            alert("Parent Clicked!");
        }, { capture: true });

## 5. Prevent Default Behavior

### Some events (like form submission or link clicks) have default actions.

        document.querySelector("a").addEventListener("click", function(event) {
            event.preventDefault();
            alert("Link click prevented!");
        });

## 6. Removing Event Listeners

        function handleClick() {
            alert("Clicked!");
        }
        button.addEventListener("click", handleClick);
        button.removeEventListener("click", handleClick);

## 7. Event Delegation

### Instead of adding event listeners to multiple child elements, use delegation by attaching a listener to a parent.

        document.getElementById("list").addEventListener("click", function(event) {
            if (event.target.tagName === "LI") {
                alert("List item clicked: " + event.target.textContent);
            }
        });

