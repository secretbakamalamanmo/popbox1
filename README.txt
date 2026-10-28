POP BOX CAFE — DEMO PROJECT

PROJECT FILES
  customer/index.html       Customer menu and ordering page
  customer/style.css        Customer page styles
  customer/pop-box-logo.jpg Shared cafe logo
  customer/assets/menu/     All supplied menu photos
  staff/index.html          Staff dashboard page
  staff/style.css           Staff dashboard styles
  DEFENSE_GUIDE.md          Short notes about the prototype

There is one HTML page per role. The customer and staff pages have different tasks, so they stay as two clearly named pages. The nested duplicate copies have been removed from this cleaned package.

OPEN THE PAGES
Run the project with VS Code Live Server from this folder (or serve this folder with another local web server):
  Customer: /customer/
  Staff:    /staff/

Use the same browser profile and local server origin for both pages so the demo order data is shared.

PROJECT LIMITS
This is a front-end prototype. Orders and menu availability use browser localStorage; they do not sync between devices. The demo has no production database, authentication, or payment processing. Some product reference-photo fallbacks need an internet connection.
