## Bugs and Errors | Error handling

სურათი ასახავს ისტორიულ ჩანაწერს, სადაც აღწერილია პირველი "ბაგი" (შეცდომა) კომპიუტერში, რომელიც იპოვეს 1947 წელს, როდესაც ჰარვარდ მარკ II-ის კომპიუტერის შიგნით მართავდნენ მავთულებს და აღმოაჩინეს რეალური მწერი. ეს შემთხვევა ითვლება კომპიუტერული ბაგების ისტორიული წარმოშობის ეტაპად.

გამოყენებული ტერმინი "Bug" (ბაგი) დღემდე გამოიყენება, როგორც კომპიუტერული პროგრამების ან სისტემების შეცდომის აღსანიშნავად.

## Strict Mode

Strict Mode ("use strict";) არის JavaScript-ის რეჟიმი, რომელიც ააქტიურებს მკაცრ წესებს კოდის შესასრულებლად. იგი ამცირებს შეცდომების ალბათობას, რომლებიც ჩვეულებრივ არ იქნებოდა და ხელს უწყობს უფრო უსაფრთხო და ხარისხიან კოდს.

**მაგალითები:**

1. Undefined Variable in Loop:

```js
function canYouSpotTheProblem() {
  "use strict";
  for (counter = 0; counter < 10; counter++) {
    // Error because counter is not defined
    console.log("Happy happy");
  }
}
canYouSpotTheProblem();
// → ReferenceError: counter is not defined
```

**აღწერა:** Strict Mode-ში, თუ შევქმნით ცვლადს var, let, ან const-ის გარეშე, გვექნება ReferenceError. აქ counter არ არის დეკლარირებული, ამიტომ ხდება შეცდომა.

2. Calling a Constructor Function Without `new:`

```js
function Person(name) {
  this.name = name;
}
let ferdinand = Person("Ferdinand"); // Forgot 'new'
console.log(name);
// → Ferdinand
```

**აღწერა:** თუ კონსტრუქტორ ფუნქციას ვიძახებთ new-ის გარეშე, Strict Mode-ში არ იქნება შეცდომა, მაგრამ შეგვეძლება დაგენერირებული ობიექტის ფროფერთის მნიშვნელობაზე პირდაპირი წვდომა.

3. Strict Mode with Constructor and `new:`

```js
"use strict";
function Person(name) {
  this.name = name;
}
let ferdinand = Person("Ferdinand"); // Forgot 'new'
// → TypeError: Cannot set property 'name' of undefined
```

**აღწერა:** Strict Mode-ში, როდესაც არ გამოიყენებთ new კონსტრუქტორ ფუნქციასთან, this გამოდის undefined, რაც იწვევს TypeError-ს, რადგან არ შეიძლება მნიშვნელობის მიღება undefined-ზე. ასევე, ობიექტის ფროფერთის ვერ მივწვდებით პირდაპირ.

## Types

ჯავასკრიფტში არ შეგვიძლია ცვლადებისთვის ტიპების გაწერა, მაგალითად არ შეგვიძლია განვსზღვროთ რომ რაიმე ცვლადი უნდა იყოს რიცხვითი ტიპის და როცა სტრინგს მივანიჭებთ, ერორი დაარტყას. საშუალო და დიდ პროექტებში ეს არც თუ ისე კომფორტულია, რადგან შეიძლება არმოვაჩინოთ ბევრი ხარვეზი, რომელიც ერორს არ არტყავს და მოგვიწიოს პრობლემის ძებნა. ერორები კი სულაც არაა ცუდი, პირიქით, ისინი გვეუბნებიან სად გვაქვს შეცდომები.

მაქსიმუმ შეგვიძლია ტიპები კომენტარის სახით განვსაზღვროთ:

```js
const age = 20; // age: number

// parameter: number
function foo(parameter) {
    ...
}
```

**Typescript**

თუმცა არსებობს Typescript, სადაც შეგვიძლია ტიპების განსაზღვრა. Typescript-იც იგივე ჯავასკიფტია, სადაც უბრალოდ დამატებით ტიპების განსაზღვრა შეგვიძლია. (მას React-ის ნაწილში გავივლით):

```js
let age: number = 20;

function foo(parameter: number) {}
```

## Testing

შეგვიძლია დავწეროთ ცალკე ტესტის ფუნქციები, რათა შევამოწმოთ, რამდენად სწორად მუშაობს ჩვენი პროგრამა:

```js
function test(label, body) {
  if (!body()) console.log(`Failed: ${label}`);
}

test("convert Latin text to uppercase", () => {
  return "hello".toUpperCase() == "HELLO"; // დიდი ასოები
});

test("convert Greek text to uppercase", () => {
  return "Χαίρετε".toUpperCase() == "ΧΑΊΡΕΤΕ"; // გაორმაგება
});
```

უფრო კომპლექსური ტესტების მრატივად საწერად და ვიზუალური ნაწილისთვის გამოიყენენბა Jest ბიბლიოთეკა.

## Debugging

როდესაც პროგრამაში გვაქვს ბაგი, ანუ ერორი არაა, მაგრამ არასწორ პასუხს ვიღებეთ, გვიწევს კოდის გარჩევა. ამ დროს შეგვიძლია გამოვიეყენოთ VS Code-ში ჩაშენებული Debugger:

```js
function numberToString(n, base = 10) {
  let result = "",
    sign = "";
  if (n < 0) {
    sign = "-";
    n = -n;
  }
  do {
    result = String(n % base) + result;
    n /= base;
  } while (n > 0);
  return sign + result;
}
console.log(numberToString(13, 2));
```

შესწორენბული კოდი:

```js
function numberToString(n, base = 10) {
  let result = "",
    sign = "";
  if (n < 0) {
    sign = "-";
    n = -n;
  }
  do {
    result = String(n % base) + result;
    n /= base;
  } while (n > 0);
  return sign + result;
}
console.log(numberToString(13, 2));
```

## Error Propagation - შეცდომების გადაცემა

JavaScript-ში შეცდომის გადაცემა ეხება იმ პროცესს, თუ როგორ იკვეთება და გადაეცემა შეცდომები ან პრობლემები ფუნქციების შესრულებისას. თქვენს კოდში შეცდომის დამუშავება გამოიყენება პოტენციური პრობლემების შესაფასებლად, როგორიცაა არასწორი ინფუთი ან ცარიელი მასივი.

მოდით, განვიხილოთ თითოეული ფუნქცია, რომ გავიგოთ, როგორ ხდება შეცდომების დამუშავება:

```js
function promptNumber(question) {
  let result = Number(prompt(question)); // შეყვანილი მონაცემის ციფრად გარდაქმნა
  if (Number.isNaN(result))
    return null; // თუ შედეგი არ არის ვალიდური ციფრი, დაბრუნდება null
  else return result; // თუ გარდაქმნა წარმატებით მოხდა, დაბრუნდება ციფრი
}

console.log(promptNumber("How many trees do you see?"));
```

- პრობლემა: prompt() ფუნქცია აბრუნებს სტრიქონს, რომელიც შემდეგ გარდაიქმნება ციფრად Number()-ის საშუალებით.
- შეცდომის დამუშავება: თუ გარდაქმნა ვერ მოხდება (მაგალითად, მომხმარებელი ჩაწერს არასასურველ მონაცემებს), Number.isNaN(result) შეამოწმებს, არის თუ არა შედეგი NaN. თუ ეს ასეა, ფუნქცია აბრუნებს null-ს, რაც ნიშნავს შეცდომას. თუ გარდაქმნა წარმატებულია, ფუნქცია აბრუნებს ციფრს.
- შეცდომის გადაცემა: არასწორ მონაცემებზე ფუნქცია აბრუნებს null-ს, რაც ცხადყოფს, რომ შეცდომა მოხდა.

**მეორე მაგალითი:**

```js
function lastElement(array) {
  if (array.length == 0) {
    // თუ მასივი ცარიელია
    return { failed: true }; // დაბრუნდება ობიექტი, რომელიც მიუთითებს შეცდომაზე
  } else {
    return { value: array[array.length - 1] }; // დაბრუნდება მასივის უკანასკნელი ელემენტი
  }
}
```

- პრობლემა: ფუნქცია ცდილობს მიიღოს მასივის უკანასკნელი ელემენტი.
- შეცდომის დამუშავება: თუ მასივი ცარიელია (array.length == 0), ფუნქცია აბრუნებს ობიექტს {failed: true}, რომელიც მიუთითებს, რომ ელემენტი არ არსებობს. თუ მასივი არ არის ცარიელი, აბრუნებს ობიექტს, რომელიც შეიცავს უკანასკნელ ელემენტს ({value: array[array.length - 1]}).
- შეცდომის გადაცემა: ცარიელი მასივის შემთხვევაში დაბრუნდება სპეციალური ობიექტი {failed: true}, რომელიც აღნიშნავს შეცდომას ცარიელი მასივის გამო.

## Exceptions - გამონაკლისები

ექსეფშენები JavaScript-ში გამოიყენება, როდესაც გვინდა შევაფასოთ, თუ რა შეიძლება დასრულდეს წარუმატებლად პროგრამაში და როგორ მოვახერხოთ ამის ხელშეწყობა. ეს განსაკუთრებით მნიშვნელოვანია, როცა ვმუშაობთ ასინქრონულ ოპერაციებთან, როგორიცაა მონაცემთა წამოღება ქსელიდან.

მოდით განვიხილოთ მაგალითი:

```js
async function fetchData() {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/posts");
    if (!response.ok) {
      throw new Error("Failed");
    }
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.log(error);
  }
}

fetchData();
```

1. try ბლოკი:

ამ ბლოკში ხდება ქსელთან დაკავშირება fetch-ის გამოყენებით. თუ ეს პროცესები წარმატებით დასრულდება, ფუნქცია განაგრძობს მუშაობას და მოპოვებულ მონაცემებს აბრუნებს.
თუ რამე შეცდომა ხდება (მაგალითად, ქსელის პრობლემა ან პასუხი არ არის "OK"), მაშინ მოხდება throw new Error("Failed"), ისვრის ქმნის ახალ შეცდომის ობიექტს.

2. catch ბლოკი:

თუ try ბლოკში ხდება შეცდომა (მაგალითად, თუ პასუხი არ იყო წარმატებული), catch ბლოკი ამოქმედდება და დაიჭერს ამ შეცდომას.
catch ბლოკში მიღებული იქნება try-ში გასროლილი error, რომელიც შეიცავს ამ შეცდომის ინფორმაციას (მაგალითად, "Failed").

**finally**

შეგვიძლია გვქონდეს finally ბლოკი, რომელშიც ჩაწერილი კოდი ამოქმედდება ნებისმიერ შემთხვევაში. ამ ბლოკში ხდება იმ შეცდომების შესრორება, რომელიც ერორემდე მოხდა. მაგალითად, ქვევითა კოდში, თუ არ არსებობს ის ანგარიში, სადაც თანხა უნდა გადავრიცხოთ, finally ბლოკში ვამოწმებთ როდის შეჩერდა ტრანზაქცია და თუ მეორე ანგარიში არ არსებობს, პირველ ანგრიშში ვაბრუნებთ აღებულ თანხას.

```js
const accounts = {
  a: 100,
  b: 0,
  c: 20,
};

function getAccount() {
  let accountName = prompt("Enter an account name");
  if (!accounts.hasOwnProperty(accountName)) {
    throw new Error(`No such account: ${accountName}`);
  }
  return accountName;
}

function transfer(from, amount) {
  if (accounts[from] < amount) return;
  accounts[from] -= amount;
  accounts[getAccount()] += amount;
}
```

**სწორი ვარიანტი:**

```js
function transfer(from, amount) {
  if (accounts[from] < amount) return;
  let progress = 0;
  try {
    accounts[from] -= amount;
    progress = 1;
    accounts[getAccount()] += amount;
    progress = 2;
  } finally {
    if (progress == 1) {
      accounts[from] += amount;
    }
  }
}
```
