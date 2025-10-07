# GOIT-JS-HW-08 🚀

Two-thirds of the JavaScript course is complete—let's keep going! 💪

Let's look back and remember the important topics covered in Module 8.

After studying the theoretical materials, you now:

-   ✅ Know the stages of the event lifecycle and understand what event bubbling is.
-   ✅ Know how to determine where an event occurred and how to stop its propagation.
-   ✅ Know how to use patterns when working with events (throttling, debouncing, event delegation).
-   ✅ Know the basic features of libraries and how to connect them.
-   ✅ Know what destructuring is.
-   ✅ Understand how to use the "Parameter Object" pattern.
-   ✅ Know how to destructure objects and arrays.

It's time to put this knowledge into practice!

## 🎯 Goal — Image Gallery

Create an image gallery with the ability to click on its items and view the full-size image in a modal window. Watch the demo video of the gallery.

![gif](./images/homework-video-1.gif)

Creating a gallery is a complex task that should be broken down into several simpler subtasks, each bringing you closer to the final goal. This process is called **task decomposition**.

---

### **Step 1: Gallery Layout**

It's logical to start by creating a container where we will add the gallery items. To do this, add the gallery container tag to the HTML code — an unordered list with the class `gallery`.

```html
<ul class="gallery"></ul>
```

### **Step 2: Image Array**

You will need data to create the gallery items. Add this array of objects to your JavaScript file. Each object represents one gallery item.

-   `preview` — a link to the small version of the image for the gallery card.
-   `original` — a link to the large version of the image for the modal window.
-   `description` — a text description of the image for the `alt` attribute of the small image and the title of the large image in the modal.

```js
const images = [
  {
    preview:
      "[https://cdn.pixabay.com/photo/2019/05/14/16/43/rchids-4202820__480.jpg](https://cdn.pixabay.com/photo/2019/05/14/16/43/rchids-4202820__480.jpg)",
    original:
      "[https://cdn.pixabay.com/photo/2019/05/14/16/43/rchids-4202820_1280.jpg](https://cdn.pixabay.com/photo/2019/05/14/16/43/rchids-4202820_1280.jpg)",
    description: "Hokkaido Flower",
  },
  {
    preview:
      "[https://cdn.pixabay.com/photo/2019/05/14/22/05/container-4203677__340.jpg](https://cdn.pixabay.com/photo/2019/05/14/22/05/container-4203677__340.jpg)",
    original:
      "[https://cdn.pixabay.com/photo/2019/05/14/22/05/container-4203677_1280.jpg](https://cdn.pixabay.com/photo/2019/05/14/22/05/container-4203677_1280.jpg)",
    description: "Container Haulage Freight",
  },
  {
    preview:
      "[https://cdn.pixabay.com/photo/2019/05/16/09/47/beach-4206785__340.jpg](https://cdn.pixabay.com/photo/2019/05/16/09/47/beach-4206785__340.jpg)",
    original:
      "[https://cdn.pixabay.com/photo/2019/05/16/09/47/beach-4206785_1280.jpg](https://cdn.pixabay.com/photo/2019/05/16/09/47/beach-4206785_1280.jpg)",
    description: "Aerial Beach View",
  },
  {
    preview:
      "[https://cdn.pixabay.com/photo/2016/11/18/16/19/flowers-1835619__340.jpg](https://cdn.pixabay.com/photo/2016/11/18/16/19/flowers-1835619__340.jpg)",
    original:
      "[https://cdn.pixabay.com/photo/2016/11/18/16/19/flowers-1835619_1280.jpg](https://cdn.pixabay.com/photo/2016/11/18/16/19/flowers-1835619_1280.jpg)",
    description: "Flower Blooms",
  },
  {
    preview:
      "[https://cdn.pixabay.com/photo/2018/09/13/10/36/mountains-3674334__340.jpg](https://cdn.pixabay.com/photo/2018/09/13/10/36/mountains-3674334__340.jpg)",
    original:
      "[https://cdn.pixabay.com/photo/2018/09/13/10/36/mountains-3674334_1280.jpg](https://cdn.pixabay.com/photo/2018/09/13/10/36/mountains-3674334_1280.jpg)",
    description: "Alpine Mountains",
  },
  {
    preview:
      "[https://cdn.pixabay.com/photo/2019/05/16/23/04/landscape-4208571__340.jpg](https://cdn.pixabay.com/photo/2019/05/16/23/04/landscape-4208571__340.jpg)",
    original:
      "[https://cdn.pixabay.com/photo/2019/05/16/23/04/landscape-4208571_1280.jpg](https://cdn.pixabay.com/photo/2019/05/16/23/04/landscape-4208571_1280.jpg)",
    description: "Mountain Lake Sailing",
  },
  {
    preview:
      "[https://cdn.pixabay.com/photo/2019/05/17/09/27/the-alps-4209272__340.jpg](https://cdn.pixabay.com/photo/2019/05/17/09/27/the-alps-4209272__340.jpg)",
    original:
      "[https://cdn.pixabay.com/photo/2019/05/17/09/27/the-alps-4209272_1280.jpg](https://cdn.pixabay.com/photo/2019/05/17/09/27/the-alps-4209272_1280.jpg)",
    description: "Alpine Spring Meadows",
  },
  {
    preview:
      "[https://cdn.pixabay.com/photo/2019/05/16/21/10/landscape-4208255__340.jpg](https://cdn.pixabay.com/photo/2019/05/16/21/10/landscape-4208255__340.jpg)",
    original:
      "[https://cdn.pixabay.com/photo/2019/05/16/21/10/landscape-4208255_1280.jpg](https://cdn.pixabay.com/photo/2019/05/16/21/10/landscape-4208255_1280.jpg)",
    description: "Nature Landscape",
  },
  {
    preview:
      "[https://cdn.pixabay.com/photo/2019/05/17/04/35/lighthouse-4208843__340.jpg](https://cdn.pixabay.com/photo/2019/05/17/04/35/lighthouse-4208843__340.jpg)",
    original:
      "[https://cdn.pixabay.com/photo/2019/05/17/04/35/lighthouse-4208843_1280.jpg](https://cdn.pixabay.com/photo/2019/05/17/04/35/lighthouse-4208843_1280.jpg)",
    description: "Lighthouse Coast Sea",
  },
];
```

### **Step 3: Gallery Item Markup**

You have a container for the gallery items and data to create them. Now it's time to populate the gallery with markup.

Use the `images` array and this HTML template for a gallery item to create the item markup in your JavaScript code, and then add all the markup into `ul.gallery`. Do not add any HTML tags other than those in this template.

```html
<li class="gallery-item">
  <a class="gallery-link" href="large-image.jpg">
    <img
      class="gallery-image"
      src="small-image.jpg"
      data-source="large-image.jpg"
      alt="Image description"
    />
  </a>
</li>
```
-   In the `src` attribute of the `<img>` tag, specify a link to the small version of the image.
-   For the `alt` attribute, we use a description of the image.
-   The link to the large image should be stored in the `data-source` attribute on the `<img>` element and specified in the link's `href`.
-   Please note that the image is wrapped in a link with an `href` attribute that points to the image file path. This could cause the image to be downloaded to the user's computer on click. Disable this behavior by default.

### **Step 4: Styling**

Add gallery styling according to the layout.

### **Step 5: Event Delegation**

It's time to add the functionality of listening for clicks on gallery items and getting a link to the large image when clicked. To do this, use the delegation method on `ul.gallery`. For now, when you click on a gallery item, display a link to the large image in the console.

### **Step 6: Library Connection**

The [basicLightbox](https://github.com/electerious/basicLightbox/tree/master) library provides a fully functional modal window that is perfect for our task. Use the [jsdelivr](https://www.jsdelivr.com/package/npm/basiclightbox?path=dist) CDN service and add the links to the library's minified (`.min`) JS and CSS files to your HTML file.

### **Step 7: Modal Window**

Change your code so that when you click on a gallery item, the modal window from the connected library opens. Read the [documentation](https://github.com/electerious/basicLightbox#readme) and [examples](https://basiclightbox.electerious.com/) to learn how to initialize and use the modal window in your code.

### **Step 8: Large Image Display**

Use your code to get a link to a large image to change the value of the `src` attribute of the `<img>` element in the modal window before opening it. Use the ready-made markup for a modal window with an image from the examples in the [basicLightbox](https://basiclightbox.electerious.com/) library.

### **Step 9: Closing from Keyboard**

Add the functionality of closing the modal window after pressing the `Escape` key. Make sure that the keyboard is only listened for while the modal window is open. The [basicLightbox](https://basiclightbox.electerious.com/) library includes a method for programmatically closing a modal window.

---

### **🧑‍🏫 Mentor's Checklist:**

What the mentor will look for when checking the assignment:

-   An image gallery is displayed on the live page from the `images` dataset.
-   The image gallery is styled to match the layout.
-   The data for the gallery is generated dynamically in JS.
-   The event delegation technique is used when listening for clicks on gallery items.
-   Nothing happens when you click between gallery items.
-   The basicLightbox library is connected.
-   When you click on a gallery item, a modal window from the connected library opens with an enlarged version of the clicked image.
-   The functionality of closing the modal window after pressing the `Escape` key is implemented.
-   The keyboard event is only listened for while the modal window is open.