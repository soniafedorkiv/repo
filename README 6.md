# DOM

1. На [HTML-сторінці](task1.html) є ненумерований список з id="list", який складається із 5 елементів. У модальному вікні необхідно послідовно вивести вміст:

   1 першого елемента списку

   2 останнього елемента списку

   3 другого елемента списку

   4 четвертого елемента списку

   5 третього елемента списку

   let list = document.getElementsById("list");
let listItems = list.getElementsByTagName("li");
let firstListItem = listItems[0];
let firstListItemText = firstListItem.textContent;
alert("Element 1:" + firstListItem.textContext);
let lastListItem = listItems[1];
alert("Element 5: " + lastListItem.textContent);
let secondListItem = listItems[1];
alert("Element 2: " + secondListItem.textContent);
let fourthListItem = listItems[3];
alert("Element 4: " + fourthListItem.textContent);
let thirdListItem = listItems[2];
alert("Element 3: " + thirdListItem.textContent); 

2. Для [HTML-сторінці](task2.html). Напишіть скріпт, який за допомогою засобів DOM простилізує сторінку так як показано на картинці.
   
   ![](task2.png)
   .stylishH1 {
  font-size: 40px;
  color: black;
  font-weight: bold;
  background-color: green;
}
   let h1Element = document.getElementByTagName("h1")
   h1Element.classList.add("stylishH1");

   .stylishP1 {
  font-size: 20px;
  color: black;
  font-weight: bold;
}
let p1Element = document.getElementById("p1")
   p1Element.classList.add("stylishP1");

.stylishP2 {
  font-size: 20px;
  color: red;
  font-weight: normal;
}
let p2Element = document.getElementById("p2")
   p2Element.classList.add("stylishP2");

   .stylishP3 {
  font-size: 20px;
  color: black;
  font-weight: normal;
  text-decoration: underline;
}
let p3Element = document.getElementById("p3")
   p3Element.classList.add("stylishP3");

.stylishP4 {
  font-size: 20px;
  color: black;
  font-weight: normal;
 font-style: italic;
}
let p4Element = document.getElementById("p4")
   p4Element.classList.add("stylishP4");

.listHorizontal {
  writing-mode: horizontal-tb; 
}
let list = document.getElementById("myList")
   p4Element.classList.add("listHorizontal");
3. Напишіть скріпт, який за допомогою засобів DOM створить для порожньої HTML-сторінки таку структуру з тегів і їх атрибутів.

```html
<body>
  <main class="mainClass check item">
     <div id="myDiv">
         <p>First paragraph</p>
     </div>
 </main>
</body>
```
let htmlElement = document.documentElement;
let body = document.createElement("body");
let main = document.createElement("main");
main.className = "mainClass check item";
let myDiv = document.createElement("div");
myDiv.id = "myDiv";
let paragraph = document.createElement("p");
paragraph.textContent = "First paragraph";
myDiv.appendChild(paragraph);
main.appendChild(myDiv);
body.appendChild(main);
document.documentElement.appendChild(body);

4. До [HTML-сторінки](task4.html) додати скрипт, яки реалізує вивід даних із полів при кліку на кнопку "Надіслати" в `<div class="out"></div>`.
<script>
  function showData() {
    const inputs = document.querySelectorAll('.arr');
    const output = document.querySelector('.out');

    let outputText = '<h2>Дані масиву:</h2><ul>';

    inputs.forEach((input) => {
      const dataForm = input.getAttribute('data-form');
      const value = input.value;
      outputText += `<li><strong>${dataForm}:</strong> ${value}</li>`;
    });

    outputText = '</ul>';

    output.innerHTML = outputText;
  }
</script>
5. З [HTML-сторінки](task5.html):

   1. вибрати всі теги із класом circle;
   2. перебрати кожен елемент, і вибрати його data-anim значення;
   3. вибране значення додати як клас за допомогою classList до цього елемента;
   4. перевірити чи застосувались анімації.
   document.addEventListener("DOMContentLoaded", function() {
  const circles = document.querySelectorAll(".circle");}
  circles.forEach(circle => {
    const dataAnimValue = circle.getAttribute("data-anim");}
    circle.classList.add(dataAnimValue);
    const styles = window.getComputedStyle(circle);
    const animationName = styles.animationName;

6. До [HTML-сторінки](task6.html) дадати скрипт який буде розраховувати ціну в залежності від вибраного кольору (можна використати `data-price` атрибути градієнтів або кольорів). Придумати додаткові варіації параметрів, які можуть впливати на ціну, реалізувати логіку для них.
const colors = document.querySelectorAll('.color');
let totalPrice = 189.99;
function calculateTotalPrice() {
  let selectedColor = null;
  for (const color of colors) {
    if (color.classList.contains('active')) {
      selectedColor = color;
      break;
    }
  }
  const additionalPrice = parseInt(selectedColor.getAttribute('data-price') || 0);
  const total = totalPrice + additionalPrice;
  document.getElementById('outprice').textContent = total.toFixed(2);
}
for (const color of colors) {
  color.addEventListener('click', () => {
    for (const otherColor of colors) {
      otherColor.classList.remove('active');
    }
    color.classList.add('active');
    calculateTotalPrice();
  });
} 

