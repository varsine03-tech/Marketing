# Առաջադրանք Claude Cowork-ի համար. Meta App Review (Instagram/Facebook Direct)

> Պատճենեք ամբողջ տեքստը ներքևի գծից հետո և տվեք Claude Cowork-ին։

---

You are helping Varsine (not a programmer) finish Meta setup so her two Telegram bots can read and answer Instagram/Facebook Direct messages and send a guide to people who comment a keyword. **Talk to her in simple Armenian, one step at a time, and ask for confirmation before anything important.**

Her two brands:
- **Varsine Hovhannisyan** — Facebook Page "Varsine Hovhannisyan", Instagram @varsinne_, site varsine.com, GitHub repo `varsine03-tech/Personal-Agent`
- **AI Mard** — Facebook Page "AI Mard", Instagram @ai.mard_, site aimard.net, GitHub repo `varsine03-tech/AI-Mard`

## Safety rules (always)
- Never write any token, password or secret in chat, in a document or in a screenshot. Paste tokens only into the GitHub "Secrets" field.
- Never delete apps, pages, secrets or data. Never change the payment settings.
- Ask Varsine before uploading any identity or business document, and before pressing any final **Submit** button.
- If a page asks for a document or information you don't have, stop and ask her.

## Part A — New Meta token with messaging permissions (do this first, ~15 min)
1. Open https://developers.facebook.com/apps and note: how many apps there are, their names, and whether each is in **Development** or **Live** mode. Tell Varsine.
2. Check which app each bot uses: in GitHub, `Settings → Secrets and variables → Actions` of each repo has `META_APP_ID` (you can't read the value; instead, compare with the App ID shown in the Meta dashboard and ask Varsine if unsure).
3. For each app, open **Graph API Explorer**: https://developers.facebook.com/tools/explorer
   - Choose the right app (Meta App), "User Token".
   - Add these permissions: `pages_show_list`, `pages_read_engagement`, `pages_manage_posts`, `pages_manage_metadata`, `pages_messaging`, `instagram_basic`, `instagram_content_publish`, `instagram_manage_messages`, `instagram_manage_comments`, `business_management`.
   - Press **Generate Access Token**. In the Facebook window choose the correct Page (Varsine Hovhannisyan **or** AI Mard) and its Instagram account, allow everything.
   - Copy the token and paste it into GitHub → the correct repo → `Settings → Secrets and variables → Actions → META_USER_TOKEN → Update`. (Personal-Agent for Varsine, AI-Mard for AI Mard.)
   - In that repo open `Actions → "Meta միացում (մեկ անգամ)" → Run workflow`, choose **facebook**, run it, and wait for the green ✅. If it is red, show Varsine the error text (not the token).
4. Tell Varsine: "Part A is done. Please tell Claude Code «Meta-ի նոր բանալին պատրաստ է»."

## Part B — Business Verification (~20 min of work, then 1–14 days waiting)
1. Open https://business.facebook.com/settings/security (Security Center). Pick the business portfolio that owns the Pages above.
2. If it says **Verified**, skip to Part C.
3. Otherwise press **Start verification** and fill: legal business name, address, phone, website (varsine.com or aimard.net). Ask Varsine which legal entity to use (sole proprietor / company) and for the registration document. **Ask before uploading.**
4. Choose verification by email on the domain (e.g. hi@varsine.com or contact@aimard.net) if offered — both arrive in her Gmail.
5. Tell Varsine the status and that Meta will answer in 1–14 days.

## Part C — App settings (~30 min)
For each app: `App settings → Basic`:
1. **Privacy Policy URL** and **User data deletion** URL: the page must exist on her site. Ask Varsine where her site is edited (e.g. Hostinger, Wix, Tilda). Create a page `/privacy` with the text at the end of this document (replace BRAND/EMAIL/SITE). Use the same URL for data deletion (the page has that section).
2. **App icon** 1024×1024: use the brand logo (ask Varsine for the file).
3. **Category**: Business and pages. Save.

## Part D — App Review request (~45 min; do it after Part A is done and the bot has been used for 1 day)
Open `App Review → Permissions and Features`. For each of these, press **Request advanced access**:
`pages_messaging`, `instagram_manage_messages`, `instagram_manage_comments`, `pages_manage_metadata`, `pages_read_engagement`, `instagram_basic`.
If a permission says "make a test API call first", tell Varsine to write to Claude Code «Meta-ի թեստային կանչերը արա» and wait.

Use these answers (English):

> ⚠️ UPDATE (October 2026): the bot now answers automatically. If a request was already submitted with the old text ("nothing is sent until she presses Send"), tell Varsine before changing anything — the description must match how the app really works.

**How will your app use this permission? (pages_messaging / instagram_manage_messages)**
> This is a private tool used only by AI Mard (aimard.net), an Armenian AI-education business, to manage its own Page and Instagram inbox. When a person sends a message to our Page or Instagram account, the app replies within the 24-hour window, only to people who wrote to us first. Replies use only facts from a knowledge document maintained by the business owner (courses, dates, prices, registration link). If the question is not covered, or the person wants to pay, asks for a discount, complains, proposes a partnership or asks for a human, the app sends a short holding message, stops replying in that conversation and hands it over to the owner in a private Telegram chat. If the owner replies manually, the app stays silent in that conversation. The app never sends broadcasts or promotional messages, never contacts people who did not write to us, limits itself to 15 replies per conversation per day, tells people honestly that it is an AI assistant when asked, and deletes a person's data when they send "DELETE".

**instagram_manage_comments**
> Our posts ask readers to comment a keyword (for example "ԱԳԵՆՏ") to receive a free step-by-step guide (PDF). The app reads comments on our own posts only, sends one private reply with the guide link to the commenter, and posts a short public reply ("Sent to your Direct 📩"). Simple questions in comments get a short public answer inviting the person to Direct. Negative or spam comments are not answered automatically — they are reported to the owner. It never comments on other accounts' content.

**pages_manage_metadata**
> Used to subscribe our own Page to webhooks (messages, comments) so the app is notified about new messages and comments on our Page.

**pages_read_engagement / instagram_basic**
> Used to read our own Page and Instagram account information, posts and comments so the app can match comments and messages to the right post and guide.

**Screencast (1–2 min, record the screen, no sound needed)** — show:
1. A test account sends a Direct message to @ai.mard_ (e.g. "When does the next course start?"); the app answers automatically within ~2 minutes with the date from the knowledge document.
2. The test account writes "I want to register, how do I pay?"; the app sends the registration link and a holding message, and the owner's Telegram shows the hand-over card ("🔥 Ready to register") with the conversation; the owner answers manually.
3. The test account comments the keyword under a post; the guide link arrives in its Direct and a short public reply appears under the comment.
4. The test account sends "DELETE"; the app confirms deletion.
(Use the Varsine Hovhannisyan account as the test account; both accounts are managed by the same owner. If something does not work during recording, stop and tell Varsine.)

Before pressing **Submit for review**, show Varsine a summary and ask «Ուղարկե՞մ»։ After submitting, tell her: review usually takes 1–5 business days; if Meta rejects, copy the reason and give it to Claude Code.

---

## Privacy Policy text (replace BRAND, EMAIL, SITE)

**Privacy Policy — BRAND**

Last updated: October 2026

BRAND (SITE) uses a private assistant tool to manage messages and comments on its own Facebook Page and Instagram account.

**What we collect.** When you send us a message or comment on our posts, we receive your public name/username, the message or comment text and its time, as provided by Meta.

**How we use it.** Only to read and answer your message, or to send you the free guide you asked for by commenting a keyword. Replies are reviewed by us. We do not sell or share your data, and we do not use it for advertising.

**Where it is stored.** Message drafts are kept in our private database for up to 30 days and then deleted.

**Data deletion.** To delete your data, send us a message with the word "DELETE" or email EMAIL. We delete everything about you within 7 days and confirm by message.

**Contact.** EMAIL
