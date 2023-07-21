### 1. Write a JavaScript program that adds a new item to the list whenever a user inputs a text into the input field and clicks the button.

#### index.html

```
<!DOCTYPE html>
<html>
<head>
  <title>Adding a list item</title>
</head>
<body>
  <div>
    <input type="text" id="inputField">
    <button id="add">Add Item to List</button>
  </div>
  <ul id="list"></ul>

  <script src="script.js"></script>
</body>
</html>
```

#### script.js

```
const lists = document.getElementById('list');
const inputField = document.getElementById('inputField');
const add = document.getElementById('add');

add.addEventListener('click', ()=>{
  const input = inputField.value;
  const list_ele = document.createElement('li');
  list_ele.textContent = input;
  lists.appendChild(list_ele)
  inputField.value = '';

})
```

### 2. Write a JS function to change the font size,bg-color, and font-family for the paragraph in the HTML snippet below on clicking the button

```
const contentP = document.getElementById("text");
const button = document.getElementById("jsstyle");
button.addEventListener("click", () => {
  contentP.style.fontFamily = "Arial";
  contentP.style.backgroundColor="red";
  contentP.style.fontSize= "20px";
});
```

### 3. Write a JavaScript program that calculates the area of a rectangle when the user inputs the width and height into two input fields and clicks a button.

#### index.html

```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Rectangle Area Calculator</title>
</head>
<body>
  <h1>Rectangle Area Calculator</h1>
  <label for="length">Length:</label>
  <input type="number" step="any" id="length" placeholder="Enter length">

  <label for="breadth">Breadth:</label>
  <input type="number" step="any" id="breadth" placeholder="Enter breadth">

  <button id="calculate">Calculate Area</button>

  <p id="area"></p>

  <script src="script.js"></script>
</body>
</html>
```

#### script.js

```
const len = document.getElementById("length")
const brd = document.getElementById("breadth")

const area = document.getElementById("area")

const btn = document.getElementById("calculate")


btn.addEventListener('click', ()=>{
    const prod = len.value * bth.value
    area.textContent = `The area of rectangle is ${prod}`
})
```

### 4. Write a JavaScript program that displays an alert message to the user when they submit a form.

```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Form Alert</title>
</head>
<body>
  <h1>Form</h1>
  <label for="name">Name</label>
  <input type="text" step="any" id="name" placeholder="Enter name">
  <br>
  <label for="age">Age</label>
  <input type="text" step="any" id="age" placeholder="Enter roll no.">
  <br>
  <button id="submit" onclick="showAlert()">Submit</button>

  <script>
   function showAlert(){
    alert("Form submitted!");
   }
  </script>
</body>
</html>
```

### 5. Write a JavaScript program that displays an alert message to the user when they resize the browser window.

```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Resize Alert</title>
</head>
<body>
  <script>
   window.addEventListener("resize", ()=>{
    alert("Window resized!");
   });
  </script>
</body>
</html>
```

### 6. Write a JavaScript program that uses AJAX to fetch and display data from a text file when the user clicks on a button.

This is my text file ajax_practise.txt:

```
Hi my name is sarthak Tiwari !
This file is fetched using ajax.
```

This is the js program which uses AJAX to fetch practise.txt

```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Fetch Text File with Ajax</title>
</head>
<body>
  <button id="btn">Fetch Text</button>
  <p id="test"></p>

  <script>
    const btn = document.getElementById("btn");

    btn.addEventListener('click', ()=>
    {
        var httpReq = new XMLHttpRequest();
        httpReq.open("GET", "file:///E:/test.txt", true)

        httpReq.onload = ()=>{
            {
                document.getElementById("test").textContent = this.responseText;

            }
        }

        httpReq.send();
    })
  </script>
</body>
</html>
```

### 7. Write a JavaScript program that uses AJAX to fetch and display an image from an API when the user clicks on a button

```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Fetch and Display Image with AJAX</title>
</head>
<body>
  <button id="fetchImage">Fetch Random Image</button>
  <div id="imageContainer">
    <!-- The fetched image will be displayed here -->
  </div>

  <script>
    // Function to fetch and display the image
    function fetchImage() {
      const imageContainer = document.getElementById("imageContainer");

      // Make an AJAX request using Fetch API
      fetch("https://source.unsplash.com/random")
        .then(response => {
          // Check if the response is successful (status 200)
          if (!response.ok) {
            throw new Error("Failed to fetch image");
          }
          return response.url;
        })
        .then(imageUrl => {
          // Create an <img> element and set the image source
          const imgElement = document.createElement("img");
          imgElement.src = imageUrl;
          imgElement.alt = "Random Image";

          // Add the <img> element to the imageContainer
          imageContainer.innerHTML = "";
          imageContainer.appendChild(imgElement);
        })
        .catch(error => {
          console.error(error);
          imageContainer.innerHTML = "Failed to fetch image.";
        });
    }

    // Attach click event to the button
    const fetchButton = document.getElementById("fetchImage");
    fetchButton.addEventListener("click", fetchImage);
  </script>
</body>
</html>

```
