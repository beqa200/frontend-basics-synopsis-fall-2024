# დოკუმენტის ობიექტური მოდელი (DOM)

## რა არის DOM?
დოკუმენტის ობიექტის მოდელი (DOM) არის პროგრამირების ინტერფეისი HTML და XML დოკუმენტებისთვის. ის გვერდის სტრუქტურას წარმოადგენს როგორც ობიექტების ხეს, რაც საშუალებას გვაძლევს ვმართოთ მისი შინაარსი, სტრუქტურა და სტილები პროგრამულად.

### ძირითადი მახასიათებლები:
- **ხის სტრუქტურა:** DOM-ი დოკუმენტს წარმოადგენს როგორც იერარქიულ ობიექტების ხეს.
- **პლატფორმაზე დამოუკიდებელი:** მუშაობს სხვადასხვა პროგრამირების ენებსა და პლატფორმებზე.
- **დინამიური განახლებები:** უზრუნველყოფს შინაარსის, ატრიბუტების და სტილების ცვლილებას რეალურ დროში.

---

## DOM-ის კვანძები
DOM-ის ხის ძირითადი ელემენტები არიან კვანძები, რომლებიც სხვადასხვა ტიპისაა:

### საერთო კვანძების ტიპები:
- **ელემენტის კვანძები:** წარმოადგენს HTML ტეგებს, მაგალითად `<div>`, `<p>`.
- **ტექსტის კვანძები:** წარმოადგენს ტექსტს ელემენტებში.
- **ატრიბუტების კვანძები:** წარმოადგენს ელემენტების ატრიბუტებს, მაგალითად `class="example"`.
- **კომენტარის კვანძები:** დოკუმენტის კომენტარებს წარმოადგენს.


---

## DOM-ის მანიპულაცია
DOM-ის მანიპულაცია გულისხმობს მისი ხის პროგრამულად წვდომასა და ცვლილებას.

### ელემენტების წვდომა:
- **ID-ის მიხედვით:**
  ```javascript
  const element = document.getElementById("container");
  ```
- **კლასის სახელით:**
  ```javascript
  const elements = document.getElementsByClassName("example-class");
  ```
- **ტეგის სახელით:**
  ```javascript
  const paragraphs = document.getElementsByTagName("p");
  ```
- **სელექტორით:**
  ```javascript
  const firstElement = document.querySelector("#container p");
  const allElements = document.querySelectorAll(".example-class");
  ```

### ელემენტების ცვლილება:
- **შინაარსის შეცვლა:**
  ```javascript
  element.textContent = "ახალი შინაარსი";
  element.innerHTML = "<strong>მუქი შინაარსი</strong>";
  ```
- **ატრიბუტების შეცვლა:**
  ```javascript
  element.setAttribute("data-info", "value");
  element.removeAttribute("data-info");
  ```
- **სტილის შეცვლა:**
  ```javascript
  element.style.color = "blue";
  element.style.fontSize = "20px";
  ```

---

## Event-ების დამუშავება
Event-ების საშუალებას გვაძლევს ვიმოქმედოთ მომხმარებლის ქმედებებზე და ვუპასუხოთ მათ.

### საერთო Event ტიპები:
- **მაუსის Event-ები:** `click`, `dblclick`, `mouseover`, `mouseout`
- **კლავიატურის Event-ები:** `keydown`, `keyup`, `keypress`
- **ფორმის Event-ები:** `submit`, `change`, `input`

### Event-ის დამატება:
```javascript
const button = document.querySelector("button");
button.addEventListener("click", function () {
  alert("ღილაკი დაჭერილია!");
});
```

### Event-ის წაშლა:
```javascript
button.removeEventListener("click", handlerFunction);
```

---

## DOM-ის ხის დათვალიერება
შეგიძლიათ გადახვიდეთ DOM-ის ხეზე, რათა წვდომა მიიღოთ დაკავშირებულ კვანძებზე.

### საერთო დათვალიერების თვისებები:
- **მშობელი კვანძი:**
  ```javascript
  const parent = element.parentNode;
  ```
- **შვილი კვანძები:**
  ```javascript
  const children = element.childNodes;
  const firstChild = element.firstChild;
  ```
- **დამოკიდებული კვანძები:**
  ```javascript
  const nextSibling = element.nextSibling;
  const previousSibling = element.previousSibling;
  ```

---

## ელემენტების შექმნა და წაშლა

### ელემენტების შექმნა:
```javascript
const newDiv = document.createElement("div");
newDiv.textContent = "გამარჯობა, DOM!";
document.body.appendChild(newDiv);
```

### ელემენტების წაშლა:
```javascript
const elementToRemove = document.getElementById("container");
if (elementToRemove) {
  elementToRemove.remove();
}
```

---

## პრაქტიკული მაგალითი
```html
<div id="app">
  <button id="btn">დააჭირე</button>
  <ul id="list"></ul>
</div>
<script>
  const button = document.getElementById("btn");
  const list = document.getElementById("list");

  button.addEventListener("click", () => {
    const newItem = document.createElement("li");
    newItem.textContent = `ელემენტი ${list.childElementCount + 1}`;
    list.appendChild(newItem);
  });
</script>
```

ეს სკრიპტი დინამიურად ამატებს ელემენტებს სიაში, როდესაც ღილაკს დააჭერთ.

