# জনতার কণ্ঠ — Cloudflare Workers Ready

এই ZIP-টি Cloudflare Workers + OpenNext deployment-এর জন্য root-level করে প্রস্তুত করা হয়েছে।
আগের ZIP-এর `jkwork/` nested folder সরানো হয়েছে।

## গুরুত্বপূর্ণ
এটি Next.js + Supabase server-side application। তাই Cloudflare-এর সাধারণ Pages “drag & drop static files” upload ব্যবহার করবেন না।
Cloudflare Workers deployment ব্যবহার করুন।

## Cloudflare Dashboard
1. Cloudflare → Workers & Pages → Create → Workers → Import from Git / Connect to Git.
2. এই project GitHub-এ upload করুন।
3. Build command:
   `npm run build`
4. Deploy command:
   `npx opennextjs-cloudflare build && npx opennextjs-cloudflare deploy`

অথবা package.json-এর `npm run deploy` ব্যবহার করুন।

## Environment Variables / Secrets
Cloudflare Worker-এর Settings → Variables and Secrets-এ এগুলো দিন:
- SUPABASE_URL
- SUPABASE_ANON_KEY
- SUPABASE_SERVICE_ROLE_KEY (Secret)
- ADMIN_EMAILS
- SITE_URL

`SUPABASE_SERVICE_ROLE_KEY` কখনো public/client-side variable হিসেবে দেবেন না।

## Supabase
আগের README অনুযায়ী Supabase schema/migration চালিয়ে Storage bucket ও tables তৈরি করুন।

## যদি শুধু ZIP দিয়ে Dashboard-এ upload করতে চান
এই project static HTML নয়। ZIP drag-and-drop করলে Next.js server/API/admin features কাজ করবে না।
GitHub → Cloudflare Workers/OpenNext deployment ব্যবহার করাই সঠিক পদ্ধতি।
