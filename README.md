# Strategic Compass App

A simple AI-powered web app for founders of growing coaching businesses that delivers strategic clarity in under 10 minutes by turning a short interview into a decision-making compass their whole team can follow.

## User Journey
1. **Landing page:** Visitor clicks **Start your strategic interview**.
2. **Auth:** Sign up or log in using the platform's built-in authentication.
3. **Interview flow:** 12 linear questions, one per screen, with visible progress indicator.
4. **Compass generation:** On submission, answers are sent to the AI endpoint; a loading state shows while the Strategic Compass is generated.
5. **Compass output:** Two-column layout with vertical navigation (Strategic Intent, Three Strategic Pillars, Alignment Principles, Founders Rules of Engagement) and an action bar for save, download, and copy/share.
6. **Dashboard:** Users can revisit the **My compasses** dashboard to open saved outputs using the same layout as the main output page.

## Core Features
- **Built-in auth** for signup/login and account persistence.
- **AI integration** (e.g., OpenAI GPT API) for a single endpoint that transforms 12 interview answers into a structured JSON Strategic Compass.
- **Compass management**: save to account, list in dashboard, reopen detail view.
- **Download/Share**: optional PDF generation or HTML-to-PDF export; link or basic email sharing can be added later.

## Page Overview
- **Landing page:** Hero with primary CTA to start the interview.
- **Auth page:** Combined signup/login flow using platform auth.
- **Interview page:** Renders 12-step linear interview with progress bar and per-question screen.
- **Loading screen:** Displays while the AI endpoint processes answers.
- **Strategic compass page:** Two-column layout with vertical section navigation and action bar (save, download, copy/share).
- **My compasses dashboard:** Lists saved compasses with links to open the detail view (reuses compass layout).

## Data Model (conceptual)
- **User**: platform-provided auth identity.
- **Compass**:
  - `id`
  - `userId`
  - `answers` (12-question payload)
  - `strategicCompass` (structured JSON response with intent, pillars, principles, rules)
  - `createdAt` / `updatedAt`

## API Workflow
1. **Submit interview answers:** Frontend posts the 12 answers to the backend AI endpoint.
2. **AI processing:** Backend calls the LLM (e.g., OpenAI GPT) to generate the structured Strategic Compass.
3. **Response:** Backend returns JSON containing the four sections; frontend renders the two-column view.
4. **Persistence:** On save, the compass JSON and original answers are stored in the database associated with the user.

## UI Notes
- **Progress indicator** on interview screens.
- **Vertical navigation** on the compass page for quick section jumps.
- **Action bar** supports save, download (PDF/HTML), and copy/share.
- **Dashboard cards/list** showing title, date, and quick open action for each saved compass.

## Next Steps
- Scaffold the frontend with routing for the six pages.
- Implement platform auth wiring for protected routes.
- Build the 12-step interview form with validation and progress.
- Create the AI endpoint wrapper and integrate API error handling/loading states.
- Persist compass records and surface them in the dashboard.
- Add PDF export or HTML-to-PDF download and basic sharing.
