# CSS Learning Notes

## Table of Contents
- [What is CSS?](#what-is-css)
- [Basic CSS Syntax](#basic-css-syntax)
- [Types](#types)
- [Units](#units)
- [Selectors](#selectors)
- [Colors](#Colors)
- [Background](#backgrounds)
- [Fonts](#fonts)


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


**CSS Fonts - အပြည့်စုံဆုံးလမ်းညွှန် (Complete Guide)**

`font-family` သည် စာသား၏ ဖောင့်အမျိုးအစားကို သတ်မှတ်သည်။

```css
body {
  font-family: Arial, Helvetica, sans-serif;
}
.inline-code {
  font-family: 'Courier New', Courier, monospace;
}
```

ဖောင့်နာမည်တွင် space ပါပါက ကိုးကားချက်သုံးရန် လိုအပ်သည်။ `serif` (အဆွယ်ပါ)၊ `sans-serif` (အဆွယ်မပါ)၊ `monospace` (စာလုံးအကျယ်တူ)၊ `cursive` (လက်ရေးပုံစံ)၊ `fantasy` (အလှဖောင့်) ဟူ၍ generic family ငါးမျိုးရှိသည်။

```css
.serif-example {
  font-family: 'Times New Roman', Times, serif;
}
.sans-example {
  font-family: Arial, Helvetica, sans-serif;
}
.mono-example {
  font-family: 'Courier New', Courier, monospace;
}
.cursive-example {
  font-family: 'Brush Script MT', cursive;
}
.fantasy-example {
  font-family: 'Copperplate', Papyrus, fantasy;
}
```

---

`font-size` သည် ဖောင့်၏ အရွယ်အစားကို သတ်မှတ်သည်။

```css
p {
  font-size: 16px;
  font-size: 1rem;
  font-size: 1.2em;
  font-size: 80%;
  font-size: larger;
  font-size: x-small;
  font-size: medium;
  font-size: large;
}
```

`px` (pixel) သည် အကြွင်းမဲ့တန်ဖိုး။ `rem` သည် root element (html) ၏ font-size ပေါ်မူတည် (ပုံမှန် 1rem = 16px)။ `em` သည် parent element ပေါ်မူတည်။ `%` သည် ရာခိုင်နှုန်း။ `vw` သည် viewport width ၏ ရာခိုင်နှုန်း (responsive typography အတွက် အသုံးဝင်)။

```css
.responsive-title {
  font-size: 5vw;
}
```

---

`font-weight` သည် ဖောင့်၏ အထူကို သတ်မှတ်သည်။

```css
p {
  font-weight: normal;
  font-weight: bold;
  font-weight: bolder;
  font-weight: lighter;
  font-weight: 100;
  font-weight: 200;
  font-weight: 300;
  font-weight: 400;
  font-weight: 500;
  font-weight: 600;
  font-weight: 700;
  font-weight: 800;
  font-weight: 900;
}
```

`normal` = 400၊ `bold` = 700။ `bolder` နှင့် `lighter` သည် parent ၏ weight ပေါ်မူတည်၍ အလိုအလျောက် တိုးလျော့ပေးသည်။ ဖောင့်တစ်ခုစီတွင် ရနိုင်သော weight အကုန်မပါဝင်နိုင်ပါ။

---

`font-style` သည် ဖောင့်ကို စောင်းအောင်ပြုလုပ်သည်။

```css
em {
  font-style: italic;
  font-style: oblique;
  font-style: oblique 10deg;
  font-style: normal;
}
```

`italic` သည် စာလုံးပုံစံပါသော စောင်းခြင်း၊ `oblique` မှာ စာလုံးပုံစံမပါဘဲ စောင်းခြင်း (ဒီဂရီသတ်မှတ်နိုင်သည်)။

---

`font-stretch` သည် ဖောင့်၏ အကျယ်အဝန်းကို သတ်မှတ်သည်။

```css
p {
  font-stretch: normal;
  font-stretch: condensed;
  font-stretch: expanded;
  font-stretch: ultra-condensed;
  font-stretch: extra-condensed;
  font-stretch: semi-condensed;
  font-stretch: semi-expanded;
  font-stretch: extra-expanded;
  font-stretch: ultra-expanded;
  font-stretch: 75%;
}
```

ဖောင့်အများစုတွင် ဤ feature ကို မပံ့ပိုးနိုင်ပါ။ ရာခိုင်နှုန်းတန်ဖိုး (50% မှ 200% အတွင်း) လည်းသုံးနိုင်သည်။

---

`font-variant` သည် စာလုံးပုံစံကွဲများအတွက်ဖြစ်သည်။

```css
h2 {
  font-variant: small-caps;
  font-variant: normal;
  font-variant: all-small-caps;
  font-variant: titling-caps;
}
```

`small-caps` သည် စာလုံးအသေးများကို အကြီးပုံစံဖြင့် အရွယ်အစားသေးအောင်ပြောင်း။ `all-small-caps` သည် စာလုံးအားလုံးကို အကြီးပုံစံသေးသွားအောင်ပြောင်း။

---

`line-height` သည် စာကြောင်းနှစ်ကြောင်းကြား ဒေါင်လိုက်နေရာလွတ်ဖြစ်သည်။

```css
body {
  line-height: 1.5;
  line-height: 24px;
  line-height: 150%;
  line-height: normal;
}
```

ယူနစ်မပါသော နံပါတ် (ဥပမာ 1.5) သည် အကောင်းဆုံးဖြစ်ပြီး လက်ရှိ font-size ၏ 1.5 ဆဟု အဓိပ္ပာယ်ရသည်။

---

`letter-spacing` (character spacing သို့မဟုတ် tracking) သည် စာလုံးများကြား နေရာလွတ်ဖြစ်သည်။

```css
h1 {
  letter-spacing: 2px;
  letter-spacing: 0.1em;
  letter-spacing: normal;
}
```

`word-spacing` သည် စာလုံးများကြား မဟုတ်ဘဲ စကားလုံးများကြား နေရာလွတ်ဖြစ်သည်။

```css
p {
  word-spacing: 4px;
  word-spacing: 0.2em;
  word-spacing: normal;
}
```

---

`text-align` သည် စာသား၏ အနေအထားကို သတ်မှတ်သည်။

```css
.left {
  text-align: left;
}
.center {
  text-align: center;
}
.right {
  text-align: right;
}
.justify {
  text-align: justify;
}
```

`justify` သည် ဘယ်ညာညီညာစွာ ဖြန့်ခင်းပေးသည်။ `text-align-last` က နောက်ဆုံးစာကြောင်းကို သီးသန့်သတ်မှတ်ပေးသည်။

```css
.justify-last-center {
  text-align: justify;
  text-align-last: center;
}
```

---

`text-transform` သည် စာသား၏ အကြီးအသေးကို ပြောင်းလဲပေးသည်။

```css
.uppercase {
  text-transform: uppercase;
}
.lowercase {
  text-transform: lowercase;
}
.capitalize {
  text-transform: capitalize;
}
.normal-case {
  text-transform: none;
}
```

`uppercase` အကုန်အကြီး၊ `lowercase` အကုန်အသေး၊ `capitalize` စကားလုံးတိုင်း၏ ပထမစာလုံးကို အကြီး။

---

`text-decoration` သည် စာသားအောက်မျဉ်း၊ အပေါ်မျဉ်း၊ ဖြတ်မျဉ်းတို့အတွက်ဖြစ်သည်။

```css
.underline {
  text-decoration: underline;
}
.overline {
  text-decoration: overline;
}
.line-through {
  text-decoration: line-through;
}
.no-underline {
  text-decoration: none;
}
.combined {
  text-decoration: underline wavy red;
}
```

`text-decoration` ကို style (solid, wavy, dotted, dashed)၊ color နှင့် thickness သတ်မှတ်နိုင်သည်။

---

`text-shadow` သည် စာသားအတွက် အရိပ်ထည့်ပေးသည်။

```css
.shadow {
  text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
}
.multiple-shadow {
  text-shadow: 2px 2px 4px rgba(0,0,0,0.3), -2px -2px 4px rgba(255,255,255,0.5);
}
.no-shadow {
  text-shadow: none;
}
```

အစဉ် - horizontal offset (x)၊ vertical offset (y)၊ blur radius၊ color။

---

**Shorthand ရေးနည်း**

`font` property တစ်ခုတည်းဖြင့် အထက်ပါ တန်ဖိုးများစွာကို တစ်ပြိုင်နက် သတ်မှတ်နိုင်သည်။ အစဉ်မှာ `font-style` → `font-variant` → `font-weight` → `font-stretch` → `font-size/line-height` → `font-family`

```css
p {
  font: italic small-caps bold condensed 16px/1.5 Arial, sans-serif;
}
body {
  font: 16px/1.6 'Segoe UI', Roboto, sans-serif;
}
```

`font-size` နှင့် `font-family` ကို မဖြစ်မနေ ထည့်ပေးရမည်။

---

**@font-face (ကိုယ်ပိုင် ဖောင့်တင်ရန်)**

```css
@font-face {
  font-family: 'MyCustomFont';
  src: url('myfont.woff2') format('woff2'),
       url('myfont.woff') format('woff');
  font-weight: normal;
  font-style: normal;
  font-display: swap;
}

body {
  font-family: 'MyCustomFont', Arial, sans-serif;
}
```

`src` တွင် format အမျိုးမျိုးထည့်ရန် အကြံပြုသည် (woff2, woff, ttf)။ `font-display` ကို အောက်တွင် ရှင်းပြထားသည်။

---

**font-display (ဖောင့်တင်ပုံစနစ်)**

`@font-face` အတွင်း သုံးသော property ဖြစ်သည်။

```css
@font-face {
  font-family: 'MyFont';
  src: url('myfont.woff2');
  font-display: swap;
}
```

တန်ဖိုးများ - `auto` (browser ဆုံးဖြတ်သည်)၊ `block` (ဖောင့်မရောက်မချင်း စာသားမပြ)၊ `swap` (အရံဖောင့်နဲ့ပြပြီး ဖောင့်ရောက်ရင် ပြောင်း)၊ `fallback` (swap နှင့်တူသော်လည်း ခဏသာစောင့်)၊ `optional` (ရောက်ရင် ကောင်း၊ မရောက်ရင် အရံအတိုင်းထား)။ `swap` သည် performance အတွက် အကောင်းဆုံးဖြစ်သည်။

---

**Variable Fonts (စိတ်ကြိုက် အထူ၊ အကျယ်၊ စောင်း)**

ဝဘ်ဖောင့်တစ်ခုတည်းတွင် weight, width, slant စသည်တို့ကို စဉ်ဆက်မပြတ် သတ်မှတ်နိုင်သည်။

```css
@font-face {
  font-family: 'MyVariableFont';
  src: url('variablefont.woff2') format('woff2-variations');
  font-weight: 100 900;
  font-stretch: 50% 200%;
}

body {
  font-family: 'MyVariableFont', sans-serif;
  font-weight: 450;
  font-stretch: 75%;
}
```

Google Fonts တွင် variable fonts များရှိသည်။ ဥပမာ - `https://fonts.googleapis.com/css2?family=Roboto+Flex:wght@100..900&display=swap`

---

**Web Safe Fonts (လုံခြုံသောဖောင့်များ)**

ဤဖောင့်များသည် Windows, Mac, Linux အားလုံးနီးပါးတွင် ရှိသည်။

```css
/* Serif */
font-family: Georgia, 'Times New Roman', Times, serif;

/* Sans-serif */
font-family: Arial, Helvetica, sans-serif;
font-family: 'Trebuchet MS', 'Lucida Sans Unicode', sans-serif;
font-family: Verdana, Geneva, sans-serif;

/* Monospace */
font-family: 'Courier New', Courier, monospace;
font-family: 'Lucida Console', Monaco, monospace;
```

---

**System Font Stack (ပြည့်စုံသော version)**

```css
/* ခေတ်မီ system font stack - အကုန်လုံးအတွက် */
body {
  font-family: system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', 'Noto Sans', 'Liberation Sans', Arial, sans-serif;
}

/* Apple အတွက် */
.mac-font {
  font-family: -apple-system, 'San Francisco', Helvetica, sans-serif;
}

/* Windows အတွက် */
.windows-font {
  font-family: 'Segoe UI', 'Segoe UI Variable', 'Tahoma', sans-serif;
}

/* Linux အတွက် */
.linux-font {
  font-family: 'Ubuntu', 'Cantarell', 'Noto Sans', 'DejaVu Sans', sans-serif;
}
```

`system-ui` သည် ခေတ်အဆက်ဆက်အတွက် အကောင်းဆုံးဖြစ်သည်။

---

**Google Fonts အသုံးပြုနည်း (အသေးစိတ်)**

HTML ဖိုင်၏ `<head>` အတွင်းတွင် ထည့်ပါ။

```html
<link href="https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300;0,400;0,700;1,400&family=Roboto:wght@400;700&display=swap" rel="stylesheet">
```

ထို့နောက် CSS ဖိုင်တွင်

```css
body {
  font-family: 'Open Sans', sans-serif;
  font-weight: 400;
}
h1 {
  font-family: 'Roboto', sans-serif;
  font-weight: 700;
  font-style: normal;
}
```

`ital` ဖြင့် italic ပုံစံမျိုးကိုပါ ရွေးချယ်နိုင်သည်။ `display=swap` ကို အမြဲထည့်ရန် အကြံပြုသည်။

---

**Responsive Typography (အဆင့်မြင့်)**

```css
html {
  font-size: 16px;
}

@media (max-width: 768px) {
  html {
    font-size: 15px;
  }
}

@media (max-width: 480px) {
  html {
    font-size: 14px;
  }
}

/* clamp() ကိုသုံး၍ fluid typography */
h1 {
  font-size: clamp(1.5rem, 5vw, 3rem);
}
p {
  font-size: clamp(0.875rem, 2vw, 1.125rem);
}
```

`clamp(min, preferred, max)` သည် viewport အရွယ်အလိုက် အလိုအလျောက် ပြောင်းလဲပေးပြီး အနိမ့်ဆုံးနှင့် အမြင့်ဆုံးကို သတ်မှတ်ပေးသည်။

---

**အကောင်းဆုံး အလေ့အကျင့်များ (Best Practices - အပြည့်အစုံ)**

```css
/* Global Reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* Root settings */
html {
  font-size: 16px;
  scroll-behavior: smooth;
}

/* Base body */
body {
  font-family: system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  line-height: 1.6;
  color: #111;
  background-color: #fff;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* Headings */
h1, h2, h3, h4, h5, h6 {
  line-height: 1.2;
  margin-bottom: 0.5rem;
  font-weight: 600;
}

h1 { font-size: 2.5rem; }
h2 { font-size: 2rem; }
h3 { font-size: 1.75rem; }
h4 { font-size: 1.5rem; }
h5 { font-size: 1.25rem; }
h6 { font-size: 1rem; }

/* Paragraphs and text */
p {
  font-size: 1rem;
  margin-bottom: 1rem;
}

a {
  color: #0066cc;
  text-decoration: none;
}
a:hover {
  text-decoration: underline;
}

small, .text-small {
  font-size: 0.875rem;
}

/* Utility classes */
.text-center { text-align: center; }
.text-right { text-align: right; }
.text-justify { text-align: justify; }
.text-bold { font-weight: 700; }
.text-light { font-weight: 300; }
.text-italic { font-style: italic; }
.text-uppercase { text-transform: uppercase; }
.text-lowercase { text-transform: lowercase; }
.text-capitalize { text-transform: capitalize; }
.letter-spacing-wide { letter-spacing: 0.05em; }
.letter-spacing-narrow { letter-spacing: -0.02em; }

/* Responsive headings */
@media (max-width: 768px) {
  h1 { font-size: 2rem; }
  h2 { font-size: 1.75rem; }
  h3 { font-size: 1.5rem; }
  h4 { font-size: 1.25rem; }
  html { font-size: 15px; }
}

@media (max-width: 480px) {
  html { font-size: 14px; }
}
```

---

**အကျဉ်းချုပ် (Summary)**

- `font-family`: ဖောင့်အမျိုးအစား (fallback ထည့်ပါ)
- `font-size`: `rem` ကိုသုံးပါ (1rem = 16px)
- `font-weight`: `bold` (၇၀၀) သို့မဟုတ် `normal` (၄၀၀)
- `font-style`: `italic` သို့ `normal`
- `font-stretch`: `condensed` သို့ `expanded` (ပံ့ပိုးမှုနည်း)
- `font-variant`: `small-caps`
- `line-height`: unit မပါသော နံပါတ် (၁.၄ မှ ၁.၆)
- `letter-spacing`: စာလုံးကြားနေရာ (ရှားရှားပါးပါးသုံး)
- `text-align`: `left`, `center`, `right`, `justify`
- `text-transform`: `uppercase`, `lowercase`, `capitalize`
- `text-decoration`: `underline`, `overline`, `line-through`
- `text-shadow`: အရိပ်ထည့်ရန်
- `@font-face`: ကိုယ်ပိုင်ဖောင့်တင်ရန်
- `font-display: swap`: web font အတွက် performance အကောင်းဆုံး
- Variable fonts: ဖောင့်တစ်ခုတည်းဖြင့် weight, width, slant အမျိုးမျိုး
- Responsive: media queries နှင့် `clamp()` ကိုသုံးပါ
- System font stack: `system-ui` သို့မဟုတ် `-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif`