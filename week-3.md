# Responsive CSS / Grids / Positions

## Responsive CSS
Responsive დიზაინი უზრუნველყოფს ვებსაიტის ოპტიმალურ მუშაობას სხვადასხვა მოწყობილობებზე, როგორიცაა დესკტოპები, პლანშეტები და მობილური ტელეფონები.

### ძირითადი ელემენტები:

- **Media Queries:**
  საშუალებას გვაძლევს შევცვალოთ სტილები ეკრანის ზომის ან ტიპის მიხედვით.
  ```css
  @media (max-width: 768px) {
    body {
      font-size: 14px;
    }
  }
  ```

- **Fluid Layouts:**
  პროცენტულ ზომებზე დაფუძნებული ელემენტების განლაგება.
  ```css
  .container {
    width: 100%;
    padding: 5%;
  }
  ```

- **Responsive Images:**
  სურათების მასშტაბირება ისე, რომ ის მოერგოს კონტეინერის ზომას.
  ```css
  img {
    max-width: 100%;
    height: auto;
  }
  ```

- **Mobile-First Approach:**
  სტილების განსაზღვრა მობილური მოწყობილობებისთვის და შემდეგ მათი გაფართოება უფრო დიდი ეკრანებისთვის.

## CSS Grids
CSS Grid არის ორი აქსისის მქონე (2D) ლეიაუტ მოდელი(ისევე როგორც Flex), რომელიც განკუთვნილია ელემენტების პოზიციონირებისთვის ჰორიზონტალურად და ვერტიკალურად.

### ძირითადი თვისებები:

- **Grid Container:**
  ```css
  .grid-container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
  }
  ```

- **Grid Items:**
  ```css
  .grid-item {
    background-color: lightgray;
    padding: 20px;
    text-align: center;
  }
  ```

- **Grid Lines:**
  შესაძლებელს ხდის ელემენტების განლაგების კონტროლს.
  ```css
  .item1 {
    grid-column: 1 / 3;
    grid-row: 1 / 2;
  }
  ```

- **Responsive Grids:**
  ```css
  @media (max-width: 768px) {
    .grid-container {
      grid-template-columns: 1fr;
    }
  }
  ```

### გამოყენების მაგალითი:
```html
<div class="grid-container">
  <div class="grid-item">1</div>
  <div class="grid-item">2</div>
  <div class="grid-item">3</div>
  <div class="grid-item">4</div>
  <div class="grid-item">5</div>
  <div class="grid-item">6</div>
</div>
```

## CSS Positions
Positions გამოიყენება ელემენტების ზუსტი პოზიციონირებისთვის ვებსაიტზე.

### ძირითადი მნიშვნელობები:

- **Static (default):** ელემენტები განლაგებულია დოკუმენტის flow-ში ჩვეულებრივად.
  ```css
  .static {
    position: static;
  }
  ```

- **Relative:** ელემენტი განლაგებულია მისი ჩვეულებრივი პოზიციის რელაციურად, თუმცა სხვა ელემენტებზე გავლენას არ ახდენს.
  ```css
  .relative {
    position: relative;
    top: 10px;
    left: 20px;
  }
  ```

- **Absolute:** ელემენტი განლაგებულია უახლოესი რელაციური კონტეინერის მიმართ(თუ ასეთი არაა მაშინ body-ის მიმართ).
  ```css
  .absolute {
    position: absolute;
    top: 50px;
    right: 10px;
  }
  ```

- **Fixed:** ელემენტი ფიქსირებულია ეკრანის კონკრეტულ ადგილას.
  ```css
  .fixed {
    position: fixed;
    bottom: 0;
    left: 0;
  }
  ```

- **Sticky:** ელემენტი რჩება თავის პოზიციაზე, სანამ მისი კონტეინერი იქნება ხილვადი. ამის შემდეგ ის ხდება fixed
  ```css
  .sticky {
    position: sticky;
    top: 0;
  }
  ```

### გამოყენების მაგალითი:
```html
<div class="relative">Relative Position</div>
<div class="absolute">Absolute Position</div>
<div class="fixed">Fixed Position</div>
<div class="sticky">Sticky Position</div>
```

