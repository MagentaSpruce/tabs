# tabs
Stand alone tabs component using HTML, CSS, and JavaScript

This tabs component is built using pure HTML, SCSS, and vanilla JavaScript and can be used and modified with ease for different implementations. 
This project helped me to better understand and learn:

1) The fill property for SVG's
2) Nesting
3) DOM manipulation
4) .closest() selector
5) JavaScript coding

This component is in working order with no known bugs. It can be changed and implemented with small changes.

A general walkthrough of the JavaScript is as follows:

To begin with the elements which make up the tab component are selected for.
```JavaScript
const tabs = document.querySelectorAll(".operations__tab");
const tabsContainer = document.querySelector(".operations__tab-container");
const tabsContent = document.querySelectorAll(".operations__content");
```

An event listener is placed on the container. The .closest() selector helps to fix a bug which occurs where clicking on the span element is not picked up by the event listener. By using .closest() it helps the span element find the closest element with .operations__tab. This allows the button to work if it or the span is selected.
```JavaScript
tabsContainer.addEventListener("click", function (e) {
  const clicked = e.target.closest(".operations__tab");}
```

However, clicking between the buttons results in null error because the closest() selector does not find a matching parent with the class of operations__tab. To fix this a gaurd clause is used.
```JavaScript
if (!clicked) return;
```

To institute the active class correctly it must be removed from all three buttons and then activated for the one selected by the click event.
```JavaScript
  tabs.forEach((tab) => tab.classList.remove("operations__tab--active"));

  tabsContent.forEach((content) =>
    content.classList.remove("operations__content--active")
  );

  //ACTIVE TAB
  clicked.classList.add("operations__tab--active");
```

For the content, data-tab attributes were used to correlate between content and buttons. A template literal is used to dynamically insert the datakey attribute. This data-key attribute are in the element clicked where all of its dataset property is stored. Each time a click occurs on a button tab it gets stored in the click variable. The data-tab is read from there. 
```JavaScript
 document
    .querySelector(`.operations__content--${clicked.dataset.tab}`)
    .classList.add("operations__content--active");
```

***End walkthrough.
