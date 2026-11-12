# Zebra Coffee — website

Specialty coffee shop on Mangilik El 38, Astana, open 24/7.
Team: Yasmina, Dana, Korkem.

**Stack:** HTML5, CSS3, Bootstrap 5.3.3 (CDN), jQuery 3.7.1 (CDN), JavaScript.
No database: the cart and new reviews are saved in the browser (`localStorage`).

## How to open
Open `index.html` in a browser (an internet connection is needed for Bootstrap, jQuery and the fonts).

## Pages
| Page | File | CSS | JS |
|---|---|---|---|
| Home | `index.html` | `css/home.css` | `js/home.js` |
| About | `about.html` | `css/about.css` | `js/about.js` |
| Careers | `career.html` | `css/careers.css` | `js/career.js` |
| Menu | `menu.html` | `css/menu.css` | `js/menu.js` |
| Reviews | `reviews.html` | `css/reviews.css` | `js/reviews.js` |
| Booking | `booking.html` | `css/booking.css` | `js/booking.js` |
| Contacts | `contacts.html` | `css/contacts.css` | `js/contacts.js` |
| Cart | `cart.html` | `css/cart.css` | `js/cart-page.js` |

## Shared files (every page)
- `css/style.css` — colors (`:root` variables), header + menu, buttons, cards, forms, success window, back-to-top, footer.
- `js/data.js` — menu items, sizes, daily specials, `formatPrice()`, `findMenuItem()`, `getTodaySpecial()`.
- `js/cart.js` — cart in `localStorage` (`getCart`, `saveCart`, `addToCart`, `changeQty`, `removeFromCart`, `clearCart`, `updateCartBadge`).
- `js/main.js` — cart number in the menu, "Back to top" button, `showToast()`.
- `js/forms.js` — form checks (`checkName`, `checkEmail`, `checkPhone`, regular expressions), red errors / green fields, `setupForm()`, `showSuccessModal()`.

Script order on a page: jQuery → Bootstrap → `data.js` → `cart.js` → `main.js` → `forms.js` (pages with forms) → the page script.

## What each page does
- **Home:** rotating italic word in the hero, running line, hit cards ("+" adds to cart), mood picker, Night Owls timer (00:00–06:00), today's perk + promo code.
- **About:** story, flip cards with numbers, "How a cup is born", photo gallery in a window, FAQ accordion (open item is teal), link to Careers.
- **Careers:** vacancy cards from an array, "Apply" picks the role in the form, full application form with validation, success window with weekly pay.
- **Menu:** cards from `data.js`, category pills with counters, search with empty state, drink window (size, sugar, flavor, quantity, live price), add to cart + toast.
- **Reviews:** average rating and 5★–1★ bars, filter, sort, first 6 shown + "Show more", review form with star rating; new reviews are saved and appear first.
- **Booking:** zone cards (Main Hall / Window / Quiet Corner), booking form with validation, success window with booking number.
- **Contacts:** address / phone / email cards, 2GIS link, 24/7 block with live Astana clock, enquiry form (reply by email or phone).
- **Cart:** lines with +/− and delete, progress to 10% off from 5 000 ₸, promo code `ZEB-####`, only the bigger discount is applied, pickup form, success window, receipt.

## Forms
Every form has `novalidate`, `event.preventDefault()`, and checks each field on "Send".
After the first click the fields are checked again while typing.
Errors: red border + red text under the field. Correct fields: green border.
When everything is correct, a window shows a number: order `#Z-…`, application `ZC-…`, booking `ZB-…`, review `ZR-…`, message `ZM-…`.
