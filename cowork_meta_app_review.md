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

**How will your app use this permission? (pages_messaging / instagram_manage_messages)**
> This is a private tool used only by the owner of the Page "BRAND" to manage her own business inbox. When a customer sends a message to our Page/Instagram account, the app reads the conversation and prepares a reply draft in the owner's writing style. The draft is shown to the owner in a private Telegram chat; nothing is sent until she presses "Send". We only reply within the 24-hour messaging window, only to people who wrote to us first. No marketing broadcasts, no messages to people who have not contacted us.

**instagram_manage_comments**
> Our posts ask readers to comment a keyword (for example "ՀՐԱՀԱՆԳ") to receive a free step-by-step guide (PDF). The app reads comments on our own posts, detects the keyword and sends one private reply with the guide link to that commenter. It does not read or reply to comments on other accounts' content.

**pages_manage_metadata**
> Used to subscribe our own Page to webhooks (messages, comments) so the app is notified about new messages and comments on our Page.

**pages_read_engagement / instagram_basic**
> Used to read our own Page and Instagram account information, posts and comments so the app can match comments and messages to the right post and guide.

**Screencast (1–2 min, record the screen, no sound needed)** — show:
1. A test Instagram account sends a Direct message to @BRAND_IG.
2. The Telegram bot shows the reply draft with buttons ✅ Send / ✏️ Edit.
3. The owner presses ✅ Send; the reply appears in the Instagram conversation.
4. A test account comments the keyword under a post; the guide link arrives in its Direct.
(Varsine will get the working demo from Claude Code before recording. If it is not ready, stop and tell her.)

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
