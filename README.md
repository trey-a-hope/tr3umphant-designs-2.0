# Tr3umPHant Designs 2.0

The second version of Trey Hope's graphic design portfolio: a single animated landing page where visitors learn about Tr3umPHant Designs, flip through flyers, logos and illustrations, and request a custom design. It replaces the multi-page [website-tr3umphant-designs](https://github.com/trey-a-hope/website-tr3umphant-designs) site from 2014.

It's built on the [Creative](https://startbootstrap.com/theme/creative) one-page Bootstrap theme from Start Bootstrap, with an AngularJS-driven portfolio and a PHP mail endpoint added.

## Features

- **One-page layout** with smooth-scrolling nav (About, Services, Author, Portfolio, Contact), a shrinking header (`js/cbpAnimatedHeader.js`) and WOW.js bounce-in animations on scroll.
- **About and Services** sections pitching the service ("Visual Perfection at Your Fingertips!") with four selling points: graphics, two-day turnaround, affordable prices and "Q.O.E." (Quality Over Everything).
- **Meet the Author** section with Trey's photo, social links and a skills list (design, development, IDEs, frameworks).
- **Portfolio** with three tiles, View Flyers, View Logos and View Illustrations. Clicking a tile uses AngularJS (`ng-click`/`ng-show` in the `Graphic-Display` controller) to reveal that gallery from `img/flyers/`, `img/logos/` or `img/illustrations/`, with a Hide button to collapse it.
- **Design request form**: name, email, phone, design type with prices (Illustration $35, Flyer $30, Logo $25), a date-needed picker, optional image upload and a description. Payment is "discussed after completion".
- **Contact section** with phone and email links.
- **Background music**: a hidden, looping `<audio>` element plays `media/onAndOn.mp3`.

## How it works

- `index.php` is the live page. `index.html` is an earlier copy of the same page without the AJAX submit handler.
- AngularJS 1.3 (from the Google CDN) bootstraps the `Tr3umPHant` app defined in `js/app.js`, which only drives the portfolio tabs.
- The request form's **Submit** button posts the serialized form to `send.php` with jQuery `$.post` and shows the response in a `#success` div.
- `js/creative.js` wires up page scrolling, the navbar, FitText and WOW animations.

## Tech stack

- HTML, Bootstrap 3 and the Start Bootstrap Creative theme (`css/creative.css`, source in `less/`)
- AngularJS 1.3.14 and jQuery (with jQuery Easing and FitText)
- WOW.js and animate.css for scroll animations
- bootstrap-datetimepicker for the date field
- Font Awesome icons
- PHP (`send.php`) for email

## Getting started

### Prerequisites

- PHP with a working `mail()` setup to receive form submissions.

### Running locally

```bash
git clone https://github.com/trey-a-hope/tr3umphant-designs-2.0.git
cd tr3umphant-designs-2.0
php -S localhost:8000
```

Open <http://localhost:8000/index.php>.

## Project structure

```
tr3umphant-designs-2.0/
├── index.php        # Live one-page site with AJAX form submit
├── index.html       # Earlier static copy of the page
├── send.php         # Mail endpoint called by the request form
├── js/app.js        # AngularJS module and portfolio controller
├── js/creative.js   # Theme behavior: scrolling, navbar, animations
├── css/             # Bootstrap, Creative theme, animate.css, datetimepicker
├── less/            # Theme LESS sources
├── img/             # Header, author photo, tile images and portfolio folders
├── media/           # Background music (onAndOn.mp3, holup.mp3)
└── font-awesome/, fonts/
```

## Known limitations

- `send.php` is still a stub: it ignores the submitted fields and emails a fixed "First line of text" test message. The real handler is commented out at the top of the file and needs to be finished before the request form is useful.
- The image upload field isn't sent by `$.post(...serialize())`, since serialization skips file inputs.
- `js/app.js` contains an unused date picker controller and leftover sample data.
- Autoplaying background audio is blocked by most modern browsers.
- jQuery is also loaded from `http://code.jquery.com/jquery-latest.js` over plain HTTP.

## License

The Creative theme is © Iron Summit Media Strategies and released under the Apache 2.0 license (see [`LICENSE`](LICENSE)). The portfolio artwork belongs to Trey Hope.
