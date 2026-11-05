# Recipe Box

A shared recipe book with Breakfast, Lunch, Dinner and Dessert, photos, ingredient links, star ratings, and TikTok / Instagram / YouTube videos that play right inside each recipe.

- **Website:** GitHub Pages (free)
- **Recipes, photos, videos and sign-in:** Supabase (free)
- **Anyone** can read the recipes. **Anyone with an account** can add recipes. People can only edit or delete their own recipes; the box owner can edit everything.

---

## Setup (about 20 minutes, one time)

You'll need 4 files: `index.html`, `config.js`, `README.md` (this file) go on GitHub. `supabase-setup.sql` goes into Supabase only. Keep it off GitHub, since it has your email in it.

### Part A: Supabase (the database)

1. Go to **supabase.com** and click **Start your project**. Signing in with GitHub is easiest.
2. Click **New project**.
   - Name: `recipe-box`
   - Database password: click **Generate a password** and save it somewhere (you won't need it day to day).
   - Region: **East US** (closest to you)
   - Click **Create new project** and wait a minute or two while it sets up.
3. In the left sidebar, open **SQL Editor**, then click **New query**.
   Open `supabase-setup.sql`, copy everything, paste it in, and click **Run**.
   You should see **Success. No rows returned**. This creates the recipe table, the access rules, photo/video storage, and loads your 5 recipes.
4. In the left sidebar, open **Authentication**, then **Sign In / Providers** (on some screens it's **Providers > Email**).
   - Make sure **Email** is turned on.
   - Turn **off** **Confirm email**, then click **Save**.
   *Why:* Supabase's free email service only sends to you, so friends would never get a confirmation email. With it off, people sign up with an email and password and can start right away.
5. Get your two keys: click the **Connect** button at the top of the project (or go to **Project Settings > API**). Copy:
   - **Project URL** (looks like `https://abcdxyz.supabase.co`)
   - **anon public** key (a long string starting with `eyJ`)

### Part B: GitHub (the website)

6. Go to **github.com**, sign in (or sign up), and click **New** (green button) to create a repository.
   - Repository name: `recipe-box`
   - Choose **Public** (required for free GitHub Pages)
   - Click **Create repository**
7. On the empty repository page, click **uploading an existing file**.
   Drag in `index.html`, `config.js` and `README.md`, then click **Commit changes**.
8. Click `config.js` in your repository, then the **pencil icon** to edit it.
   Replace `YOUR_SUPABASE_URL` and `YOUR_SUPABASE_ANON_KEY` with the two values from step 5 (keep the quotes). Click **Commit changes**.
9. Go to the repository's **Settings > Pages**.
   - Source: **Deploy from a branch**
   - Branch: **main**, folder **/ (root)**, then **Save**
   Wait 1 to 2 minutes and refresh. Your site's address appears at the top, like `https://YOUR-USERNAME.github.io/recipe-box/`.

### Part C: Claim your box

10. Open your site, click **Sign in**, then **Create an account** using **dylan.l.cosmos@gmail.com**.
    Do this **before** sharing the link. That email is the box owner, so registering it first makes sure nobody else can claim it.
11. Share the link with friends. They click **Sign in > Create an account** and can start adding recipes.

---

## Good to know

- **Videos:** Recipes with a TikTok, Instagram or YouTube link as the Source show the video right in the recipe. If a short TikTok link (`tiktok.com/t/...`) won't load, edit the recipe and paste the full link (`tiktok.com/@name/video/123...`). You can also upload your own MP4 clip (up to 50 MB).
- **Recipes with more than one part** (a sauce, crust, filling, marinade, frosting, side…): in the recipe form, click **+ Add another part**. Each part gets its own name, ingredients and steps. When pasting a recipe, put a line like `For the sauce:` or `Crust:` before each part's ingredients and steps and it'll be split up for you.
- **Equipment:** each recipe has an optional Equipment list (one item per line) that shows above the ingredients. When pasting a recipe, a line that says `Equipment` starts that list.
- **Pantry:** click **Pantry** at the top to list what you have on hand, then **What can I make?** to see recipes you have everything for (plus ones you're only 1 or 2 items short on). Each person's pantry is private and follows their account. To turn on syncing, run `pantry-setup.sql` once in Supabase (**SQL Editor > New query**, paste, **Run**). Until then, pantries are saved on each device.
- **Favorites** are saved per device, so everyone keeps their own.
- **"I made this"** works for anyone who's signed in, on any recipe.
- **Free Supabase projects pause after 7 days with no visits.** If the site stops loading recipes, open supabase.com, go to your project and click **Restore**. Visiting the site now and then keeps it awake.
- **Stopping new sign-ups:** In Supabase, go to **Authentication > Sign In / Providers** and turn off **Allow new users to sign up**. Existing accounts keep working.
- **Making changes later:** Edit `index.html` on GitHub (pencil icon) or upload a new version. The site updates within a couple of minutes.
- **The anon key in `config.js` is safe to be public.** The access rules in Supabase decide who can read and change things.
