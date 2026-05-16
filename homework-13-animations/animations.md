# Homework 13 — ანიმაციების იდეები (Figma Ecommerce Dark Theme)

ეს ფაილი არის “იდეების ბანკი”: რომელი ანიმაციები უხდება ამ ტიპის ecommerce გვერდს და როგორ გააკეთო ისინი მხოლოდ CSS-ით.

## 1) ზოგადი წესები (UX)

- **ხანმოკლე და რბილი:** hover-ებზე ხშირად საკმარისია `150ms–300ms`.
- **დაამთავრე `transform/opacity`-ით:** ეს უფრო “smooth” და performant არის, ვიდრე `top/left/width` ცვლილებები.
- **ფოკუსიც გაითვალისწინე:** `:focus-visible` სტილიც დაამატე, რომ კლავიატურით ნავიგაციაც კარგი იყოს.
- **Reduced motion:** თუ გინდა “სწორი” მიდგომა, დაამატე:
  - `@media (prefers-reduced-motion: reduce) { * { animation: none; transition: none; } }`

---

## 2) Header / Nav

### 2.1 Nav ლინკების Hover (transition)
იდეა: `background-color`, `color` და ოდნავ `transform: translateY(-1px)` hover-ზე.

რეკომენდაცია:
- გამოიყენე `transition: background-color .2s ease, color .2s ease, transform .2s ease;`

### 2.2 “Shop now” ღილაკის გარშემო ტრიალებადი border
იდეა: `::before` ან `::after` ელემენტზე გააკეთე “ring”, რომელიც `rotate()`-ით ტრიალებს.

სწრაფი მიმართულება:
- ღილაკს მიეცი `position: relative; overflow: hidden;`
- `::before` გააკეთე `position: absolute; inset: -2px;`
- ring-ს მიეცი `animation: spin 2s linear infinite;`
- `@keyframes spin { to { transform: rotate(360deg); } }`

დამატებითი “პრემიუმ” ეფექტი:
- ring-ზე გამოიყენე `conic-gradient(...)`, რომ რეალურად “ფერის ბრუნვა” გამოჩნდეს.

---

## 3) კატეგორიები (All/Mens/Womens/Kids)

### 3.1 Hover background + underline
იდეა: hover-ზე ოდნავ შეცვალე `background-color` და ქვემოთ “გაიზარდოს” underline.

სწრაფი მიმართულება:
- underline გააკეთე `::after`-ით (`height: 2px; width: 0;`)
- hover-ზე `width: 100%` + `transition`

---

## 4) Product Cards

### 4.1 სურათის zoom-in (scale)
იდეა: hover-ზე `transform: scale(1.1)` და სურათს ჰქონდეს `transition`.

რეკომენდაცია:
- სურათის wrapper-ს მიეცი `overflow: hidden; border-radius` (თუ მაკეტშია), რომ გაბერვა ლამაზად “ჩაიჭრას”.
- `transition: transform .25s ease;`

### 4.2 Card lift (ჩრდილი + აწევა)
იდეა: ქარდზე `translateY(-4px)` + ოდნავ უფრო ძლიერი shadow.

რეკომენდაცია:
- `transition: transform .2s ease, box-shadow .2s ease;`

---

## 5) FAQ

### 5.1 Tab hover (background transition)
იდეა: FAQ ტაბებზე (All/Ordering/Shopping/Returns/Support) hover-ზე `background-color` + `color`.

### 5.2 FAQ item hover (text color)
იდეა: თითოეულ კითხვაზე hover-ზე ტექსტი ოდნავ “გაანათე” (Dark theme-ზე ძალიან უხდება).

დამატებითი იდეა:
- პატარა აიქონი (მაგ: `+` ან `chevron`) hover-ზე ოდნავ დაატრიალე `rotate(10deg)` ან გადმოწიე `translateX(4px)`.

---

## 6) Footer

### 6.1 Social icons float (infinite)
იდეა: აიქონები “მოცურავდნენ” ზემოთ-ქვემოთ.

რეკომენდაცია:
- `animation: float 2s ease-in-out infinite;`
- თითო აიქონს მიეცი პატარა `animation-delay`, რომ ერთდროულად არ “ხტოდნენ”.
- `@keyframes float { 0%,100% { transform: translateY(0); } 50% { transform: translateY(-6px); } }`

### 6.2 Footer links hover (scale + color)
იდეა: (Home, Products) hover-ზე `scale(1.1)` + `color` ცვლილება.

რეკომენდაცია:
- `display: inline-block;` (რომ scale-მა იმუშაოს “სუფთად”)
- `transition: transform .2s ease, color .2s ease;`

---

## 7) სურვილისამებრ (ძალიან უხდება ecommerce-ს)

- **Page load reveal:** Header/hero ნაწილს გაუკეთე `opacity` + `translateY` და `animation` 400–700ms.
- **Button press:** `:active`-ზე `transform: scale(0.98)` (მოკლე).
- **Glow on hover:** dark theme-ზე `box-shadow` “glow” ეფექტი მცირე ინტენსივობით.

