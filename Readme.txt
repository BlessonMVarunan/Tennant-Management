You are maintaining an existing Tenant Management Portal.

The uploaded ZIP is the current master version. Do not rebuild the application from scratch. Do not replace working modules unnecessarily. Make only the requested change while preserving all existing features, stored data, responsive design, and data structure.

PROJECT PURPOSE

This is a browser-based tenant, shop, rent-payment, interaction, and version-history portal. It must work on desktop and mobile.

CURRENT APPLICATION STRUCTURE

The application uses separate files for:

- HTML page structure
- CSS styling
- Default tenant data
- Application startup
- Navigation
- Dashboard rendering
- Tenant and shop management
- Rent-payment management
- Interaction management
- Analytics
- Version history
- Browser storage

Keep the application modular. Do not move everything back into one index.html file.

DATA PROTECTION RULES

1. Existing tenant, shop, payment, interaction, building, and version-history data must not be deleted, overwritten, duplicated, or corrupted.

2. Keep permanent IDs for tenants and records. Do not use editable shop names or unit numbers as permanent identifiers.

3. Existing saved browser data must remain compatible with the updated version.

4. If the data structure must change:
   - Increase the schema version.
   - Add a migration function.
   - Preserve all existing values.
   - Do not silently reset the application to default data.

5. Make a deep copy of before-and-after values before recording an update.

6. Do not clear browser storage during startup.

7. Do not restore default data when valid saved data already exists.

8. Default information should load only for a first-time user who has no saved application data.

9. Before altering storage logic, verify that existing stored data still loads correctly.

DEFAULT INFORMATION

- Existing tenant, shop, payment, interaction, and version-history information must load when the application is opened for the first time.
- All existing shops belong to “Blesson Complex.”
- Returning users must see their latest saved information, not the default information.
- New buildings created later must remain available.

BUILDING MANAGEMENT

When registering a new tenant, the user must choose:

1. Add to an existing building.
2. Add to a new building.

Requirements:

- “Blesson Complex” must be available as an existing building.
- Existing building names must be generated from saved application data.
- If “New Building” is selected, show a field for the new building name.
- Do not change existing shops to the newly created building.
- Building filters must update after a new building is saved.
- Do not force all future buildings back to Blesson Complex during application startup.

SHOPS AND UNITS

The Shops & Units screen must:

- Work on desktop and mobile.
- List all shops and tenants.
- Support building filtering.
- Support shop and tenant searching.
- Show a “View Details” button for each shop.
- Not directly show an edit button in the list.

When “View Details” is selected:

- Open a read-only details popup.
- Show building, unit, tenant, business, phone, monthly rent, advance, area, meter ID, key date, rent decision date, due day, and notes.
- Provide a separate “Edit Details” button.
- Editing must start only after the user deliberately selects “Edit Details.”
- Saving an edit must preserve existing payment history.
- Saving an edit must create a version-history entry.

The “Register / Transfer Tenant” button must:

- Open correctly from both desktop and mobile.
- Support registering a new tenant.
- Support using an existing building or creating a new building.
- Validate required fields.
- Preserve historical information.
- Create a version-history entry.

RENT-PAYMENT MANAGEMENT

The Add Rent popup must include:

- Editor/user name.
- Shop or unit.
- Billing month.
- Amount paid.
- Payment status: PAID, PARTIAL, or PENDING.
- Optional payment attachment.
- Save and Cancel buttons.

Rent-save requirements:

- Rent must save for November 2026 and all future months.
- A newly added month must automatically appear in the month selectors.
- Saving must work with or without an attachment.
- Amount must be a valid number and cannot be negative.
- A confirmation message must appear after a successful save.
- The payment must remain after the page is reloaded.
- An existing payment for the same shop and month may be updated.
- Updating a payment must record the previous and new values.
- Saving a payment must create a version-history entry with user and timestamp.

ATTACHMENT REQUIREMENT

This browser-only version may record:

- Attachment filename.
- Payment record linked to the attachment name.
- User who selected it.
- Update timestamp.

Do not claim that the actual file is permanently uploaded unless a real backend or file-storage connection exists.

MONTH AND DASHBOARD RULES

The month controls must be dynamically generated. Do not hard-code a short fixed list of months.

Billing-month data relationship:

- October 2026 dashboard view shows September 2026 rent.
- November 2026 dashboard view shows October 2026 rent.
- December 2026 dashboard view shows November 2026 rent.
- Continue this relationship for all months and years.

The dashboard month selector should clearly display:

“November 2026, showing October 2026 rent”

Months containing saved payment information must remain selectable.

In the Add Rent popup:

- Identify months that already have payment data.
- Display an indicator such as “data available.”
- Include previous, current, and future months.
- When rent is saved for a new month, refresh the month list automatically.
- Do not require editing HTML every month.

DASHBOARD

The dashboard must retain:

- Payment LED grid.
- Total units.
- Units paid.
- Units pending.
- Open issues.
- Building filter.
- Tenant and shop search.
- Payment status.
- Amount paid.
- Amount due.
- Add Rent action.
- Add Interaction action.
- Desktop table.
- Mobile card view.

LED status:

- Green: paid.
- Orange: partial.
- Red: pending or unpaid.

The displayed status and totals must use the correct billing month according to the previous-month rule.

INTERACTIONS

The application must retain:

- Log Interaction.
- Shop selection.
- Interaction date.
- Summary.
- OPEN, IN_PROGRESS, and RESOLVED statuses.
- Notes.
- Optional attachment filename.
- Status filtering.
- Shop searching.
- Desktop table.
- Mobile cards.
- Version-history entry after saving.

ANALYTICS

Retain:

- Payment analytics by shop.
- Building filter.
- 6-month and 12-month views.
- Monthly payment values.
- Row totals.
- Dynamic month calculations based on the current date.
- Desktop and mobile usability.

Do not anchor analytics permanently to October 2026.

VERSION HISTORY

Every meaningful add or update must create a version-history record containing:

- Unique audit ID.
- Timestamp.
- User/editor.
- Action type.
- Entity type.
- Entity ID.
- Clear description.
- Previous values, when applicable.
- New values, when applicable.

Version history must record:

- Tenant registration.
- Tenant update.
- Tenant transfer.
- Building creation.
- Rent addition.
- Rent update.
- Interaction creation.
- Data migration.

The user name is manually entered in this browser-only version. Do not describe it as authenticated identity.

STORAGE

Use browser localStorage for this version.

Maintain:

- Current application data.
- One previous valid version for recovery.
- Schema version.
- Last-updated timestamp.

Do not show JSON Import or Export controls in the user interface unless I explicitly request them in a future change.

MOBILE AND DESKTOP

Desktop requirements:

- Sidebar navigation.
- Full tables.
- Header month selector.
- Filters and action buttons.
- Scrollable analytics where needed.

Mobile requirements:

- Mobile top header.
- Bottom navigation.
- Card views instead of wide tables where practical.
- Touch-friendly buttons.
- Full-width form controls.
- Scrollable LED and analytics tables.
- Modals must fit within the screen and scroll vertically.

Do not fix desktop functionality while breaking mobile functionality, or vice versa.

SECURITY AND CODE QUALITY

- Escape user-provided text before inserting it into generated HTML.
- Validate all required form values.
- Do not use unsafe user values directly inside inline JavaScript.
- Avoid duplicate HTML element IDs.
- Check for missing elements before accessing them.
- Do not introduce undefined function or variable errors.
- Keep business logic separate from rendering where practical.
- Avoid changing unrelated modules.

CHANGE REQUEST

Implement only the following requested change:

[PASTE THE NEW CHANGE HERE]

REQUIRED DEVELOPMENT METHOD

Before editing:

1. Extract the uploaded ZIP.
2. Review all HTML, CSS, and JavaScript files.
3. Identify which modules are affected.
4. Create a backup of the original uploaded version.
5. Do not assume an element or function exists. Verify it first.

After editing, run all of the following:

1. JavaScript syntax validation for every JavaScript file.
2. HTML validation for missing or duplicate IDs.
3. Browser console check for runtime errors.
4. Desktop functional tests.
5. Mobile viewport functional tests.
6. Browser reload and persistence test.
7. Regression test of every protected feature listed below.

MANDATORY REGRESSION TESTS

Application startup:
- Application loads without console errors.
- Default information loads for a first-time user.
- Saved information loads for a returning user.
- Blesson Complex appears.
- Existing tenant and payment information remains intact.

Navigation:
- Every desktop tab opens.
- Every mobile navigation button works.

Dashboard:
- Desktop table renders.
- Mobile cards render.
- LED grid renders.
- Search works.
- Building filter works.
- Statistics render.
- Month selector works.
- October displays September rent.
- November displays October rent.
- December displays November rent.

Rent:
- Add Rent opens.
- A shop can be selected.
- Existing-data months are identified.
- November 2026 can be selected.
- November 2026 payment saves successfully.
- Payment without an attachment saves.
- Payment with an attachment filename saves.
- New payment remains after reload.
- New payment month appears in selectors.
- Existing payment can be updated.
- Version history records the change.

Shops and units:
- Shops & Units opens.
- Search works.
- Building filter works.
- View Details opens.
- Details are initially read-only.
- Edit Details opens.
- Edit saves.
- Existing payments remain after tenant editing.
- Register / Transfer Tenant opens.
- Tenant can be added to Blesson Complex.
- Tenant can be added to a new building.
- New building appears in filters.
- Mobile shop cards work.

Interactions:
- Log Interaction opens.
- Interaction saves.
- Status filter works.
- Search works.
- Mobile interaction cards work.
- Version history is created.

Analytics:
- Analytics opens.
- 6-month view works.
- 12-month view works.
- Building filter works.
- Totals calculate.
- Months are based on current application data.

History:
- History opens.
- User is recorded.
- Timestamp is recorded.
- Action description is recorded.
- Before and after values are preserved when updating records.

DATA-INTEGRITY TEST

Before and after the change, compare:

- Number of tenants.
- Tenant IDs.
- Building names.
- Unit numbers.
- Payment months.
- Payment amounts.
- Interactions.
- Version-history records.

Any difference must be explained by the requested change. Unrelated data changes are not acceptable.

RELEASE REQUIREMENTS

Do not provide the final ZIP merely because the code passes syntax validation.

Provide the ZIP only after:

- Functional browser tests pass.
- Regression tests pass.
- Data-integrity comparison passes.
- Mobile and desktop tests pass.
- The ZIP integrity test passes.

Include a CHANGELOG.md containing:

- Version number.
- Requested change.
- Files modified.
- Bugs fixed.
- Existing features verified.
- Tests run.
- Known limitations.

If any required test cannot be run, clearly state which test was not run. Do not claim that everything was tested when only syntax checking was completed.
