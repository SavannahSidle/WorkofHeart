# Work of Heart prototype

## Run
Open index.html in a current browser. There are no external dependencies or build steps. Deployment is not configured by this commit. MICA Digital is not modified.

## Implemented
Responsive storefront, original sample SVG illustrations, product details, search, available filter, shopping bag, CAD subtotal, explanatory checkout preview, and public maker demo. Listings require a photo, description and price. The first sentence becomes the title. Includes edit, delete, sold status, photo resizing, browser-local persistence, JSON backup export and sample reset. Each listing represents one unique piece. Cart state is session-only.

## Limits
This is an interface-study prototype, not a production shop. No authentication, shared database, real payment, order placement, shipping or tax calculation is present. Listings are local to a browser, not published to visitors. Clearing browser storage removes them. Backup export is provided; import is not implemented. Do not enter private or customer data. Maker mode is intentionally public. Native dialogs, labels, focus styles, status announcements, and responsive layouts are included, but accessibility conformance has not been established.

## Manual acceptance tests
- Open the page at desktop and 320px mobile widths. Check zoom and overflow.
- Open Maker demo; add a JPEG, PNG or WebP photo, description and price; save and reload.
- Edit a listing; mark it sold/available; filter; delete it.
- Test missing photo, blank description, invalid prices, invalid file type, oversized photo and unreadable image.
- Close the editor during photo processing; reopen it and check for stale previews.
- Test disabled/full local storage and export a backup.
- Add/remove items from the bag and verify subtotal and unique-item behavior.
- Confirm checkout preview cannot collect payment or place an order.
- Navigate with keyboard; check dialog focus, Escape and focus return. Test a screen reader and actual phone photo selection.

These are test instructions, not claims that interactive browser tests have been executed.

## Manage page
`manage.html` opens directly to Choose photo, Description, Price, Post. `/manage/` also opens this page. The public page is not private merely because it has a noindex tag; write access requires authorization.

The technical GitHub token setup screen has been removed. Devices previously configured with a repository-scoped token retain authorized publishing, editing, sold status, and deletion. An unconfigured device can prepare a photo and details but is explicitly told publishing is not connected; Post never reports success or silently saves a browser-only listing.

Token-free shared publishing for Tracie is NOT configured yet. It requires a connected persistent backend and seller authorization. A Supabase connection has been requested from the site owner. Do not describe the page as a completed token-free publishing system until this is connected and tested with a real shared post.

Existing publishing writes resized images and `listings.json` to the repository. Multi-file commits are not atomic and an interrupted upload may leave an orphaned image. Concurrent writes are rejected rather than overwriting another writer. The storefront remains a sample shop until real listings exist. Its request button does not deliver customer messages.

## Production roadmap
Add authenticated seller access with server-enforced authorization; a shared database and object storage; server-side price/upload validation; hosted payment checkout with secrets kept server-side; verified, idempotent payment webhooks; atomic reservations for unique inventory; order and fulfillment records; merchant contact details and delivery, returns, tax and privacy configuration. Test simultaneous purchases, delayed/failed payments, expired reservations and refunds before accepting money.
