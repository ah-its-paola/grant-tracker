# Grant Tracker

A small, free web page that helps a nonprofit team see every grant at a glance: where it stands, when it's due, what's missing, and quick calendar imports to track deadlines more easily.

**[Try it here](https://grant-tracker-pi.vercel.app/)**

It opens with 25 made-up sample grants, so you can click around right away. You can also upload your own spreadsheet. Your file stays in your browser. Nothing is uploaded or sent anywhere.

## Why I made this

This is my first attempt at building a simple, low-code app with Claude Code. As I'm transitioning from private sector work to public sector or nonprofit work, I am thinking about common problems that could be resolved by a simple app. Both types of agencies track grant deadlines, so I figured that was a great place to start.

The goal was not to build something fancy. I wanted to learn the loop: describe a useful tool, build it, try it, and improve it. I also wanted to see how far a person without a software background can get by being clear about the problem and the rules.

## The problem I started with

Before a team meeting, a development team wants to find a funder or program, see its status, and notice what information is missing. They shouldn't have to search a whole spreadsheet to do it.

I started from one question: **what problem am I trying to solve?** Every feature below had to answer it, or it didn't go in.

## The rules I set

I gave Claude these ground rules at the start and held to them the whole way:

- Use only made-up records while building. No real donor, client, or staff data.
- Keep the supplied facts exactly as they are. Never invent a missing value.
- Show unknown information clearly instead of hiding or guessing it.
- Don't connect to any live system.
- Don't claim the tool is more ready than it is.
- Keep the original source file unchanged.

Later I relaxed two of these on purpose, and I want to be honest about that: I made the page public so others can try it, and I removed the "fictional records" wording except on the sample data.

## How I worked

1. **Plan first.** I asked Claude to confirm it could read the records and fields, tell me what was missing, and give me a short plan. I told it to wait until I said to build.
2. **Build small, then look.** I tried each version myself and gave feedback in plain words.
3. **Ask for the reason.** When Claude suggested something, I asked why, and asked to see it compared with how it worked today before I agreed.
4. **Test what I can check myself.** For example, I confirmed in LibreOffice how the spreadsheet's status dropdown behaves instead of taking a claim on faith.
5. **Simplify.** I removed things that didn't earn their place.

### Decisions I made, and why

- **Icons plus color for status.** Color alone doesn't work for people who can't see color differences, so every status also has a small icon.
- **A "?" for anything missing.** It's cleaner and screen readers still hear "Missing."
- **Missing items always sort first.** The point is to notice gaps, so they shouldn't sink to the bottom.
- **Your file stays in your browser.** No server, no account, no database. That protects privacy and keeps the tool simple.
- **No email or push notifications.** They need a server that stores people's data, which goes against the privacy choice above. Instead, there's an "Add all to calendar" button that saves a calendar file with a reminder 7 days and 1 day before each deadline.
- **Extra columns are fine.** The page finds the five columns it needs by name and ignores the rest, so people can keep their own columns.
- **A warning before using AI with data.** The cleanup prompt starts with a reminder to remove personal information, follow your organization's data and AI policy, and turn off AI training on your data if you can.

## How to use it with your own data

1. Click **Use your own data** and answer the short questions. They give you the right steps.
2. Start from the **template** (a spreadsheet with a Grants tab), or use the **cleanup prompt** to have an AI tool move your existing spreadsheet into the template.
3. Upload a `.xlsx` or `.csv` file.

The page reads these five columns: `grant_id`, `funder`, `program`, `deadline`, `status`. Write deadlines like `2026-12-31`. If you use an `.xlsx` file, it reads the tab named `Grants` (or the first tab if there isn't one).

**Please do not put personal information in your file.** The page can't check for you.

## What I tested, and what I didn't

Tested with automated browser checks and by hand:

- Search, status filter, sorting, Reset, and the missing-information labels
- Uploading `.xlsx` and `.csv` files, including files saved by LibreOffice
- Phone-sized screens and light and dark mode
- The calendar file and the keep-it-up-to-date file link (Chrome and Edge only)
- Opening the calendar file in Google Calendar.

Not tested:
- A real screen reader. I checked the page's structure and labels, but I haven't listened to it with one.
- Anything with real grant data.

## Known limits

- Each person loads their own file. There is no shared live database.
- Linking a file so the page updates when you save it only works in Chrome and Edge.
- Older `.xls` files, Numbers files, and links to Google Sheets don't work. Download a copy as `.xlsx` or `.csv` first.

## What's in this repo

- `index.html` is the whole app. It's one file with no dependencies.
- `Grant_Tracker_Template.xlsx` is the blank template.
- `Spreadsheet_Cleanup_Prompt.txt` is the prompt for cleaning up an existing spreadsheet.

To run it on your own computer, download `index.html` and open it in a browser.

## License

MIT License. Built with Claude Code.
