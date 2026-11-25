CHARMÉRA STUDIO — SUPABASE INTEGRATION PACKAGE

Included:
- index.html + script.js: storefront loads products from Supabase and submits orders through a validated database function.
- admin.html + admin.js: email/password Supabase Auth login, product management, customer order dashboard, status updates, invoice print.
- supabase-config.js: project URL and admin email. Paste your Supabase publishable key here.
- supabase_setup.sql: RLS policies and secure customer order RPC.

IMPORTANT SETUP — DO THESE IN ORDER
1. Open supabase-config.js and replace PASTE_YOUR_SUPABASE_PUBLISHABLE_KEY_HERE with the project's PUBLIC publishable/anon key. Never put a secret/service_role key in this file.
2. In Supabase SQL Editor, run supabase_setup.sql once. It removes the old broad public insert policies and installs stricter policies. It assumes the exact existing table/column names from the supplied schema CSV.
3. In Supabase Authentication > Users, confirm the admin user email is exactly khdekarsanika746@gmail.com and that you know its password. The browser admin login checks this exact email.
4. In Supabase Authentication > URL Configuration, Site URL should be https://harmonious-custard-7ae58d.netlify.app and Redirect URLs should include the site root and /admin.html.
5. Upload all files in this folder to Netlify, replacing the old deployed files. Do not upload only admin.js or only index.html.
6. Test product viewing, admin sign-in, add/edit/delete product, customer checkout, stock decrement and order status update. Use a low-cost/test product and verify data in Supabase before advertising the store.

LIMITATIONS / HONEST STATUS
- This package uses Pay on delivery only. It does NOT implement UPI/GPay/PhonePe online payment verification.
- It does not implement courier integration or delivery tracking.
- Customer checkout currently uses simple browser prompts; these can be upgraded to a styled checkout form later.
- Product image input accepts an image URL; Supabase Storage upload is not implemented.
- The admin email allowlist is enforced by both client checks and database RLS. Do not add other admin users without updating policies deliberately.
- SQL function is security-definer and validates price/stock server-side. Review it before production. Keep the public publishable key only in frontend; never expose secret/service_role keys.
