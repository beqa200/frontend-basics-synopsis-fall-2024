# ციკლები - loops

როდესაც გვინდა, რომ რაიმე სახის კონკრეტული ფუნქციონალი რამდენჯერმე გავამეოროთ, მაშინ ვიყენებთ ლუპებს. მაგალითად, როცა გვინდა, რომ გამოვაკონსოლოთ ლუწი რიცხვები 0-დან 20-ის ჩათვლით, არაა საჭირო console.log-ის რამდენჯერმე გამოყენება - მას უბრალოდ ლუპში ჩავსვავთ და ფუნქციონალს გავამეორებთ.

```js
console.log(0);
console.log(2);
console.log(4);
console.log(6);
console.log(8);
console.log(10);
console.log(12);
console.log(14);
console.log(16);
console.log(18);
console.log(20); // ძალიან ცუდი პრაქტიკაა
```

## while loop

როცა გვინდა რომ რაიმე ფუნქციონალი განხორციელდეს მანამ სანამ კონკრეტული არის ჭეშმარიტი, ვიყენებთ while ციკლს:

```js
while (პირობა) {
  ფუნქციონალი;
}
```

პირობაში უნდა გვქონდეს ისეთი გამოსახულება, რომელიც რაღაც მომენტში შეიცვლება და გახდება false, რათა ლუპი შეჩერდეს და არ გვქონდეს უსასრულო ციკლი.

```js
let number = 0;
while (number <= 12) {
  console.log(number);
  number = number + 2;
}
// → 0
// → 2
//   … etcetera
```

```js
let result = 1;
let counter = 0;
while (counter < 10) {
  result = result * 2;
  counter = counter + 1;
}
console.log(result);
// → 1024
```

## do while loop

while ციკლისგან განსხვავებით, რომელიც ჯერ ამოწმებს და მერე აკეთებს, do while ლუპი ჯერ აკეთებს და მერე ამოწმებს პირობას:

```js
do {
  execution;
} while (condition);
```

do while ყველაზე ხშირად შეგიძლიათ გამოიყენოთ ისეთ ამოცანებში, სადაც მომხმარებელს კითხვას ვუსვავთ, იმიტომ რო ჯერ უნდა დავსვათ კითხვა და მერე შევამოწმოთ პასუხი:

```js
let age;
do {
  age = prompt("How old are you?");
} while (age < 18);
console.log("You are adult");
```

while vc do while meme
![alt text](/images/while-vs-do-while.png)

## for loop

for ციკლიც გამოიყენება ფუნქციონალის რამდენჯერმე გასამეორებლად, უბრალოდ კოდის რა ნაწილებსაც ვიყენებდით while-ის ან do while-ის გარეთ, ყველაფერი თავსდება for ციკლში. მრგვალ ფრჩხილებში ჩაწერილი კოდი იყობა სამ ნაწილად - ინიციალიზაცია ანუ ცვლადის შექმნა, პირობა და იტერაცია(ხშირ შემთხვევაში ინკრიმენტი):

```js
for (initialization; condition; increment) {
  execution;
}
```

```js
for (let number = 0; number <= 12; number = number + 2) {
  console.log(number);
}
// → 0
// → 2
//   … etcetera
```

```js
for (let counter = 0; counter < 4; counter = counter + 1) {
  let result = 1;
  result = result * 2;
}
console.log(result);
// → 1024
```

## break

ციკლის გაჩერება შეგვიძლია break-ით:

```js
for (let current = 20; ; current = current + 1) {
  if (current % 7 === 0) {
    console.log(current);
    break;
  }
}
// → 21
```

break შეგვიძლია გამოვიყენოთ ასევე while და do while ლუპებშიც, ისევე როგორც შემდეგი keyword.

## continue

ციკლის იტერაციის გამოსატოვებლად გამოიყენება continue:

```js
for (let i = 0; i <= 20; i++) {
  if (i % 2 === 0) {
    continue;
  }
  console.log(i);
}
// → 1
// → 3
// → 5
// → ...etcetera
```
