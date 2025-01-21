
# Event Propagation, Capturing, and Bubbling

## რა არის Event Propagation?
Event propagation აღწერს პროცესს, რომლის მიხედვითაც Event-ები გადადიან DOM tree-ში. როდესაც Event იწვება, იგი გადადის DOM-ში კონკრეტული რიგით, რომელიც მოიცავს სამ ფაზას:
1. **Capturing ფაზა**: Event გადადის root ელემენტიდან target ელემენტამდე.
2. **Target ფაზა**: Event აღწევს target ელემენტს, სადაც იგი მუშავდება.
3. **Bubbling ფაზა**: Event გადადის DOM-ში უკან, target ელემენტიდან root ელემენტამდე.

---

## Capturing ფაზა
- Event იწყება DOM ხის root ელემენტიდან და გადადის ქვემოთ target ელემენტამდე.
- ამ ფაზის მოსმენა შეიძლება მხოლოდ შემდეგი არგუმენტით `{ capture: true }`.

### მაგალითი:
```javascript
document.getElementById("outer").addEventListener(
  "click",
  () => console.log("Outer (Capturing)"),
  { capture: true }
);
document.getElementById("inner").addEventListener(
  "click",
  () => console.log("Inner (Capturing)"),
  { capture: true }
);
```
**როდესაც ვაჭერთ inner ელემენტს, გამოიცემა:**
```
Outer (Capturing)
Inner (Capturing)
```

---

## Bubbling ფაზა
- Event იწყება target ელემენტიდან და გადადის DOM-ში უკან root ელემენტამდე.
- ეს ფაზა default-ად არის დაყენებული.

### მაგალითი:
```javascript
document.getElementById("outer").addEventListener("click", () => console.log("Outer (Bubbling)"));
document.getElementById("inner").addEventListener("click", () => console.log("Inner (Bubbling)"));
```
**როდესაც ვაჭერთ inner ელემენტს, გამოიცემა:**
```
Inner (Bubbling)
Outer (Bubbling)
```

---

## Event Propagation-ის შეჩერება
შეიძლება მოვლენის propagation-ის შეჩერება შემდეგი მეთოდებით:

### `stopPropagation()`
შეაკავებს Eventს მიმდინარე ფაზაში გაგრძელებისგან.
```javascript
document.getElementById("inner").addEventListener("click", (event) => {
  console.log("Inner Clicked");
  event.stopPropagation();
});
```

---

## Event Delegation
Event delegation არის ტექნიკა, სადაც ერთი event listener ემატება მშობელ ელემენტზე და მას გამოიყენებენ მის შვილებზე მოვლენების დასამუშავებლად.

### მაგალითი:
```javascript
document.getElementById("list").addEventListener("click", (event) => {
  if (event.target.tagName === "LI") {
    console.log("List item clicked:", event.target.textContent);
  }
});
```
ეს ეფექტურია დინამიურად დამატებული შვილი ელემენტებისთვის.

---

## პრაქტიკული მაგალითი
```html
<div id="outer">
  <div id="middle">
    <button id="inner">Click Me</button>
  </div>
</div>
```

### კოდის მაგალითი:
```javascript
document.getElementById("outer").addEventListener("click", () => console.log("Outer"));
document.getElementById("middle").addEventListener("click", () => console.log("Middle"));
document.getElementById("inner").addEventListener("click", () => console.log("Inner"));
```

### შედეგები:
- **Default (Bubbling):**
  ```
  Inner
  Middle
  Outer
  ```

- **`{ capture: true }`-ით:**
  ```
  Outer
  Middle
  Inner
  ```

---

## შეჯამება
| **Term**               | **აღწერა**                                                        |
|------------------------|------------------------------------------------------------------|
| **Event Propagation**  | პროცესი, რომლის მიხედვითაც Event-ები გადიან DOM-ში (capturing, target, bubbling). |
| **Capturing ფაზა**     | Event გადადის root ელემენტიდან target ელემენტამდე.              |
| **Bubbling ფაზა**      | Event გადადის target ელემენტიდან root ელემენტამდე.             |
| **stopPropagation()**  | წყვეტს პროცესის გაგრძელების საშუალებას მიმდინარე ფაზაში.            |
| **Event Delegation**   | მშობელზე listener-ის დამატება, რათა გადმოწეროს Event-ები შვილებზე. |
