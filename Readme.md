# CSS Learning Notes

## Table of Contents
- [What is CSS?](#what-is-css)
- [Basic CSS Syntax](#basic-css-syntax)
- [Types](#types)
- [Units](#units)
- [Selectors](#selectors)
- [Colors](#Colors)
- [Background](#background)
## What is CSS?
**CSS (Cascading Style Sheets)** က web page ရဲ့ style နဲ့ layout ကို control လုပ်တဲ့ language ဖြစ်ပါတယ်။  
HTML က content structure (ခေါင်းစဉ်, paragraph, image...) ကို သတ်မှတ်ပေးပြီး, CSS က အဲ့ဒီ content တွေကို ဘယ်လိုမြင်ရမလဲဆိုတာကို သတ်မှတ်ပေးပါတယ်။

ဥပမာ-
- စာသားအရောင်ပြောင်းခြင်း
- font size ကြီး/ငယ် ပြောင်းခြင်း
- background color ထည့်ခြင်း
- element တွေကို ဘယ်/ညာ/အလယ် တည်နေရာချခြင်း
- mobile, tablet, desktop အလိုက် responsive design ပြုလုပ်ခြင်း

တစ်ကြိမ် style rules ရေးထားပြီး pages အများကြီးမှာ ပြန်အသုံးချနိုင်တာကြောင့် website design ကို သန့်ရှင်းလွယ်ကူပြီး ထိန်းသိမ်းရ လွယ်ကူစေပါတယ်။

## Basic CSS Syntax
CSS syntax ကို အခြေခံအားဖြင့် အောက်ပါပုံစံနဲ့ရေးပါတယ်။

```css
selector {
  property: value;
}
```

### Syntax Breakdown
- **selector**: style သက်ရောက်စေချင်တဲ့ HTML element ကိုရွေးတာ (ဥပမာ `h1`, `.btn`, `#header`)
- **property**: ဘာကိုပြောင်းမလဲဆိုတာ (ဥပမာ `color`, `font-size`, `margin`)
- **value**: ဘယ်တန်ဖိုးသတ်မှတ်မလဲဆိုတာ (ဥပမာ `blue`, `20px`, `10px`)

### Example
```css
p {
  color: green;
  font-size: 18px;
}
```

အထက်က code မှာ `p` tag အားလုံးရဲ့ စာသားအရောင်ကို စိမ်းရောင်ထားပြီး စာလုံးအရွယ်အစားကို `18px` သတ်မှတ်ထားတာဖြစ်ပါတယ်။

## Types
CSS ကို သုံးပုံသုံးနည်း အဓိက 3 မျိုးရှိပါတယ် -

### 1) Inline CSS
HTML element တစ်ခုထဲမှာပဲ `style` attribute နဲ့ တိုက်ရိုက်ရေးသုံးတာပါ။

```html
<h1 style="color: blue;">Hello</h1>
```

- တစ်ခုချင်းစီမြန်မြန်ပြင်ချင်တဲ့အခါ အသုံးဝင်
- Project ကြီးလာရင် maintain လုပ်ရခက်

### 2) Internal CSS
HTML file ထဲက `<head>` အတွင်း `<style>` tag နဲ့ရေးသုံးတာပါ။

```html
<style>
  p {
    color: red;
  }
</style>
```

- Page တစ်ခုတည်းအတွက် style စုပြီးရေးနိုင်
- Multi-page website အတွက် ပြန်အသုံးချနိုင်မှုနည်း

### 3) External CSS
CSS ကို `.css` file သီးသန့်ထားပြီး HTML နဲ့ link ချိတ်သုံးတာပါ။

```html
<link rel="stylesheet" href="style.css" />
```

```css
/* style.css */
body {
  font-family: Arial, sans-serif;
}
```

- အများဆုံးအသုံးများပြီး best practice ဖြစ်တယ်
- Reusable ဖြစ်ပြီး website အကြီးအတွက် ထိန်းသိမ်းရလွယ်

## Units
CSS Units ဆိုတာ size, spacing, width, height, font-size စတဲ့ value တွေကို တိုင်းတာဖို့ အသုံးပြုတဲ့ measurement system ဖြစ်ပါတယ်။

Units ကို အဓိကအားဖြင့် 2 မျိုးခွဲနိုင်ပါတယ် -
- **Absolute Units** (တိတိကျကျ တန်ဖိုးတည်ငြိမ်)
- **Relative Units** (parent/root/screen size ပေါ်မူတည်ပြီး ပြောင်းလဲ)

### 1) Absolute Units
Absolute units တွေက screen size ပြောင်းလဲရင်လည်း value မပြောင်းဘူး။

- `px` (pixels) - web မှာအများဆုံးသုံး
- `pt` (points) - print design တွေမှာပိုများ
- `cm`, `mm`, `in` - physical size units (web မှာတော်တော်ရှား)

```css
h1 {
  font-size: 32px;
}

.box {
  width: 300px;
  padding: 20px;
}
```

**ဘယ်အချိန်သုံးမလဲ**
- Pixel-perfect control လိုတဲ့ component မျိုး
- border thickness, icon size လို fixed ဖြစ်သင့်တဲ့နေရာ

### 2) Relative Units
Relative units တွေက parent element, root font size, viewport size အပေါ်မူတည်ပြီး ပြောင်းလဲတတ်လို့ responsive design အတွက်ကောင်းပါတယ်။

#### `em`
Element ရဲ့ parent font-size ကိုအခြေခံပြီးတွက်တယ်။

```css
.card {
  font-size: 20px;
}

.card p {
  font-size: 1.2em; /* 24px */
}
```

#### `rem`
Root element (`html`) ရဲ့ font-size ကိုအခြေခံတယ်။ Project-wide consistency အတွက် အရမ်းအသုံးဝင်တယ်။

```css
html {
  font-size: 16px;
}

h2 {
  font-size: 2rem; /* 32px */
}
```

#### `%`
Parent element ရဲ့ size အပေါ်မူတည်တယ်။

```css
.container {
  width: 80%;
}
```

#### `vw` and `vh`
Viewport width/height အပေါ်အခြေခံတယ်။
- `1vw` = screen width ရဲ့ 1%
- `1vh` = screen height ရဲ့ 1%

```css
.hero {
  height: 100vh;
}

.title {
  font-size: 5vw;
}
```

### Quick Guide (Best Practice)
- **font-size** အတွက် `rem` သုံးရင် maintain လုပ်ရလွယ်
- **component spacing** (margin/padding) အတွက် `rem` သို့ `em` သုံးလို့ကောင်း
- **fixed size** လိုတဲ့နေရာမှာ `px` သုံး
- **responsive layout** အတွက် `%`, `vw`, `vh` တွေဖြည့်သုံး

### Example Mix
```css
html {
  font-size: 16px;
}

.wrapper {
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 1.5rem;
}

h1 {
  font-size: 2.5rem;
}

p {
  font-size: 1rem;
  line-height: 1.6;
}
```

## Selectors
CSS Selector ဆိုတာ HTML elements တွေထဲက ဘယ် element ကို style သက်ရောက်မလဲဆိုတာ ရွေးပေးတဲ့ pattern ဖြစ်ပါတယ်။

### 1) Element Selector
Tag name ကို တိုက်ရိုက်ရွေးတယ်။

```css
h1 {
  color: navy;
}
```

### 2) Class Selector (`.`)
Class name တူတဲ့ elements အားလုံးကိုရွေးတယ်။

```css
.btn {
  background-color: teal;
  color: white;
}
```

### 3) ID Selector (`#`)
ID တစ်ခုတည်းရှိတဲ့ element ကိုရွေးတယ်။

```css
#header {
  background: #f4f4f4;
}
```

### 4) Universal Selector (`*`)
Elements အားလုံးကိုရွေးတယ်။

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

### 5) Grouping Selector (`,`)
Selector မျိုးစုံကို တစ်ကြိမ်တည်း style ပေးနိုင်တယ်။

```css
h1, h2, h3 {
  font-family: Arial, sans-serif;
}
```

### 6) Descendant Selector (space)
Parent အောက်က child/inner elements တွေကိုရွေးတယ်။

```css
.card p {
  color: #333;
}
```

### 7) Child Selector (`>`)
Direct child ဖြစ်တဲ့ element ကိုပဲရွေးတယ်။

```css
nav > a {
  text-decoration: none;
}
```

### 8) Attribute Selector (`[]`)
Attribute ရှိတဲ့ element တွေကိုရွေးတယ်။

```css
input[type="text"] {
  border: 1px solid #ccc;
}
```

### 9) Pseudo-class Selector (`:`)
Element state (hover, focus, first-child...) အပေါ်မူတည်ရွေးတယ်။

```css
a:hover {
  color: red;
}
```

### 10) Pseudo-element Selector (`::`)
Element အစိတ်အပိုင်းတစ်ခုကိုရွေးတယ်။

```css
p::first-letter {
  font-size: 2rem;
}
```

### Quick Tips
- Reusable style တွေအတွက် `class` ကိုပိုသုံးပါ
- `id` ကို unique element တစ်ခုအတွက်ပဲသုံးပါ
- Selector ကို ရှည်လွန်းမထားဘဲ ဖတ်လို့လွယ်အောင်ရေးပါ

--- 

## Colors

CSS တွင် အရောင်များကို သတ်မှတ်ရန် နည်းလမ်းများစွာ ရှိပါသည်။ ဤတွင် အဓိက နည်းလမ်း (၆) မျိုးကို လေ့လာနိုင်ပါသည်။

### 1) Color Names (အရောင်အမည်များ)

CSS တွင် အရောင် ၁၄၀ ကျော်အတွက် ကြိုတင်သတ်မှတ်ထားသော အမည်များရှိပါသည်။

```css
.element {
  color: red;
  background-color: blue;
  border-color: tomato;
}
```

### 2) Hexadecimal (Hex) Colors

 **#** သင်္ကေတနှင့် စတင်ပြီး နောက်မှ ဂဏန်း (၆) လုံးပါဝင်သည်။

* ပထမ ၂ လုံး - အနီရောင် (Red)

* အလယ် ၂ လုံး - အစိမ်းရောင် (Green)

* နောက်ဆုံး ၂ လုံး - အပြာရောင် (Blue)


```css
.element {
  color: #FF0000;  /* အနီရောင် */
  background-color: #00FF00; /* အစိမ်းရောင် */
  border-color: #0000FF; /* အပြာရောင် */
  /* အတိုကောက်ပုံစံ */
  color: #F00; /* #FF0000 နှင့် အတူတူပင် */
}
```

- Hex တန်ဖိုးများမှာ 00 မှ FF အထိဖြစ်ပြီး 00 မှောင်ဆုံး၊ FF လင်းဆုံးဖြစ်သည်။


### 3) RGB Colors

rgb(red, green, blue) ပုံစံဖြင့် သတ်မှတ်ပြီး တန်ဖိုးတစ်ခုလျှင် ၀ မှ ၂၅၅ အထိဖြစ်သည်။

```css 
.element {
  color: rgb(255, 0, 0);     /* အနီရောင် */
  background-color: rgb(0, 255, 0); /* အစိမ်းရောင် */
  border-color: rgb(0, 0, 255); /* အပြာရောင် */
}
```

RGBA (RGB with Alpha - ပွင့်လင်းမှု)

ပွင့်လင်းမှုအတွက် alpha တန်ဖိုး (၀ မှ ၁ အတွင်း) ထည့်နိုင်သည်။

```css
.element {
  background-color: rgba(255, 0, 0, 0.5); /* အနီရောင် ၅၀% ပွင့်လင်း */
  color: rgba(0, 0, 0, 0.8); /* အနက်ရောင် ၈၀% ပွင့်လင်း */
}
```

### 4) HSL Colors
HSL ဆိုသည်မှာ Hue (အရောင်သွေး), Saturation (အရောင်ပြင်းအား), Lightness (အလင်းရောင်) ကို ဆိုလိုသည်။

```css
.element {
  color: hsl(0, 100.00%, 51.00%);     /* အနီရောင် */
  background-color: hsl(120, 100%, 50%); /* အစိမ်းရောင် */
  border-color: hsl(240, 100%, 50%); /* အပြာရောင် */
}
```

- **Hue**: ၀ မှ ၃၆၀ အတွင်း (၀ = အနီ၊ ၁၂၀ = အစိမ်း၊ ၂၄၀ = အပြာ)

- **Saturation**: ၀% (မီးခိုးရောင်) မှ ၁၀၀% (အရောင်အပြည့်)

- **Lightness**: ၀% (အနက်ရောင်) မှ ၁၀၀% (အဖြူရောင်)

HSLA (HSL with Alpha)

```css
.element {
  background-color: hsla(200, 80%, 50%, 0.3); /* အပြာစိမ်းရောင် ၃၀% ပွင့်လင်း */
}
```


### 5) Current Color Keyword

currentColor သည် လက်ရှိ element ၏ color ပစ္စည်းတန်ဖိုးကို ပြန်သုံးနိုင်သည်။

```css
.element {
  color: blue;
  border: 2px solid currentColor; /* border သည် blue ဖြစ်မည် */
  box-shadow: 0 0 5px currentColor; /* shadow သည် blue ဖြစ်မည် */
}

```
### 6) Transparent Keyword

transparent သည် လုံးဝပွင့်လင်းသောအရောင်ဖြစ်သည်။

```css
.element {
  background-color: transparent; /* နောက်ခံပွင့်လင်း */
  border-color: transparent; /* ဘောင်လိုင်းမမြင်ရ */
}
```
---

## Backgrounds

CSS Backgrounds သည် element များ၏ နောက်ခံကို လှပစွာ ဒီဇိုင်းဆွဲရန် အင်မတန်အသုံးဝင်သော feature များဖြစ်သည်။

---

### 1) Background 

element ၏ နောက်ခံအရောင်ကို သတ်မှတ်ရန် အသုံးပြုသည်။

```css
.element {
  background-color: lightblue;
  background-color: #3498db;
  background-color: rgb(52, 152, 219);
  background-color: rgba(52, 152, 219, 0.5); /* ပွင့်လင်းမှုပါရှိ */
  background-color: hsl(204, 70%, 50%);
  background-color: transparent; /* ပွင့်လင်း (ပုံမှန်) */
}
```

### 2) background-image (နောက်ခံပုံ)

နောက်ခံအနေနဲ့ ပုံတစ်ပုံကို ထည့်သွင်းရန်။

```css
.element {
  /* တစ်ခုတည်းသော ပုံ */
  background-image: url('image.jpg');
  
  /* ပုံများစွာ (အပေါ်ဆုံးက အရင်မြင်ရ) */
  background-image: url('top-image.png'), url('background-image.jpg');
  
  /* gradient များ */
  background-image: linear-gradient(red, blue);
  background-image: radial-gradient(circle, red, yellow, green);
}
```

### 3) background-repeat (ပုံထပ်ခြင်း)

နောက်ခံပုံကို ဘယ်လိုထပ်ရမလဲ သတ်မှတ်သည်။

```css
.element {
  background-image: url('pattern.png');
  
  background-repeat: repeat;        /* ပုံမှန် - ဘယ်ညာ အပေါ်အောက် ထပ် */
  background-repeat: repeat-x;     /* အလျားလိုက်သာ ထပ် */
  background-repeat: repeat-y;     /* ဒေါင်လိုက်သာ ထပ် */
  background-repeat: no-repeat;     /* လုံးဝမထပ်ဘူး */
  background-repeat: space;         /* နေရာချိန်ညှိပြီး ထပ် */
  background-repeat: round;         /* အရွယ်အစားချိန်ညှိပြီး ထပ် */
}

```

### 4) background-position (နေရာချခြင်း)

နောက်ခံပုံရဲ့ စတင်သည့်နေရာကို သတ်မှတ်သည်။

```css
.element {
  background-image: url('image.jpg');
  background-repeat: no-repeat;
  
  /* အဓိက တန်ဖိုးများ */
  background-position: left;            /* ဘယ်ဘက် */
  background-position: right;           /* ညာဘက် */
  background-position: center;          /* အလယ် */
  background-position: top;             /* အပေါ် */
  background-position: bottom;          /* အောက် */
  
  /* တွဲသုံးခြင်း */
  background-position: top left;        /* အပေါ်ဘယ် */
  background-position: top right;       /* အပေါ်ညာ */
  background-position: bottom center;   /* အောက်အလယ် */
  
  /* ရာခိုင်နှုန်းနဲ့ သတ်မှတ်ခြင်း */
  background-position: 25% 75%;         /* X 25%, Y 75% */
  
  /* pixel နဲ့ သတ်မှတ်ခြင်း */
  background-position: 50px 100px;      /* ဘယ်ဘက်အစွန်းက 50px, အပေါ်အစွန်းက 100px */
}

```


### 5) background-size (အရွယ်အစား)

နောက်ခံပုံရဲ့ အရွယ်အစားကို သတ်မှတ်သည်။

``` css
.element {
  background-image: url('image.jpg');
  background-repeat: no-repeat;
  
  background-size: auto;           /* ပုံမှန်အရွယ်အစား */
  background-size: cover;          /* element တစ်ခုလုံးဖုံးအောင် အချိုးကျချဲ့ */
  background-size: contain;        /* ပုံလုံးမြင်ရအောင် အချိုးကျချဲ့ */
  
  /* တစ်ခုချင်းသတ်မှတ် */
  background-size: 300px 200px;    /* width height */
  background-size: 100% 80%;       /* ရာခိုင်နှုန်း */
  background-size: 50vw 50vh;      /* viewport အလိုက် */
}
```

### 6) background-attachment (တွဲဆက်ပုံ)

နောက်ခံပုံက scroll လုပ်သည့်အခါ ဘယ်လိုပြုမူမလဲ သတ်မှတ်သည်။

```css
.element {
  background-image: url('background.jpg');
  
  background-attachment: scroll;    /* element နဲ့အတူ scroll လုပ် (ပုံမှန်) */
  background-attachment: fixed;     /* viewport မှာ သေ (fixed position) */
  background-attachment: local;     /* element ရဲ့ content နဲ့အတူ scroll */
}
```

### 7) background-clip (ဖုံးအုပ်ဧရိယာ)

နောက်ခံဟာ ဘယ်နေရာအထိ ဖုံးအုပ်သင့်လဲ သတ်မှတ်သည်။

```css
.element {
  background-color: gold;
  
  background-clip: border-box;   /* border အထိ ဖုံး (ပုံမှန်) */
  background-clip: padding-box;  /* padding အထိသာ ဖုံး (border အောက်မပါ) */
  background-clip: content-box;  /* content အထိသာ ဖုံး */
  background-clip: text;         /* စာသားပုံစံအတိုင်းသာ (စာသားအရောင်ပြောင်း) */
}
```

ဥပမာ - text clip

```css
.gradient-text {
  background: linear-gradient(45deg, red, blue);
  background-clip: text;
  color: transparent;
}
```

### 8) background-origin (အစနေရာ)

နောက်ခံပုံရဲ့ စတင်တွက်ချက်သည့်နေရာ။

```css
.element {
  background-image: url('pattern.png');
  background-repeat: no-repeat;
  
  background-origin: border-box;   /* border အစွန်းကနေ စတွက် */
  background-origin: padding-box;  /* padding အစွန်းကနေ စတွက် (ပုံမှန်) */
  background-origin: content-box;  /* content အစွန်းကနေ စတွက် */
}
```
### 9) Shorthand (တစ်ကြောင်းတည်းနဲ့ရေးနည်း)
အားလုံးကို background တစ်ခုတည်းနဲ့ ရေးနိုင်သည်။

```css
.element {
  /* အစဉ်လိုက်: color image repeat position / size attachment origin clip */
  
  background: lightblue url('image.jpg') no-repeat center / cover fixed;
  
  /* သို့မဟုတ် ရိုးရိုး */
  background: #f4f4f4;
  
  /* gradient များ */
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}
```

### 10) Multiple Backgrounds (နောက်ခံမျိုးစုံ)
တစ်ခါတည်း နောက်ခံအများကြီး ထည့်နိုင်သည်။

```css
.element {
  background-image: url('logo.png'), url('pattern.png'), linear-gradient(lightblue, darkblue);
  background-repeat: no-repeat, repeat, no-repeat;
  background-position: center, top left, center;
  background-size: 100px, auto, cover;
}
```

### 11) Gradient Backgrounds (အရောင်ဖျော့များ)

Linear Gradient (မျဉ်းဖြောင့်)

```css
.element {
  /* အရောင်နှစ်ခု */
  background: linear-gradient(red, blue);
  
  /* ဘေးဘက် */
  background: linear-gradient(to right, red, yellow);
  
  /* ထောင့်ဖြတ် */
  background: linear-gradient(45deg, red, orange, yellow, green, blue, indigo, violet);
  
  /* အရောင်ရပ်နားများ */
  background: linear-gradient(red 0%, blue 50%, green 100%);
  
  /* transparency ပါ */
  background: linear-gradient(rgba(0,0,0,0), rgba(0,0,0,1));
}
```

Radial Gradient (စက်ဝိုင်းပုံ)

```css
.element {
  /* ပုံမှန် */
  background: radial-gradient(circle, red, blue);
  
  /* ellipse ပုံ */
  background: radial-gradient(ellipse, red, yellow, green);
  
  /* နေရာသတ်မှတ် */
  background: radial-gradient(circle at top left, red, blue);
  
  /* အရွယ်အစားသတ်မှတ် */
  background: radial-gradient(circle closest-side, red, blue);
}
```
Conic Gradient (စက်ဝိုင်းပတ်)

```css
.element {
  background: conic-gradient(red, yellow, green, blue, red);
  
  /* ဒီဂရီသတ်မှတ် */
  background: conic-gradient(from 90deg, red, blue);
  
  /* pie chart ပုံစံ */
  background: conic-gradient(red 0deg 90deg, blue 90deg 180deg, green 180deg 270deg, yellow 270deg 360deg);
}
```