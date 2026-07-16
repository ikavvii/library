My advice based on my experience:

1. If its your first time, f*** it, f*** fear, you gotta barrel through it, even if it gets messed up, showing up matters, I remember I was scared in first year and thought hackathons are things only experienced people can do and win but hell noo. Showing up again n again would give you the motivational boost to try new things, find new stuff that could save time in future and most important - develop your own workflow that works for every hackathon/competitions.
    
2. Get a subscription of a coding agent if you can, trust me its worth it. my recommendation- buy codex - It can analyse websites, github repository, find bugs, do code reviews, it has a special codex security feature built for this only.
    
3. For the github part- I'd recommend watch a video that covers- forking(getting others code to run on your PC from github), working locally(you can download zip as well ), how to push code to the github, pull requests(sending request to owner to merge your new code to their codebase), merging code(for the owner of repo) - and dont worry the interface is really easy , it'll be easy if you do it 2-3 times, would take hardly 10 mins in total in practise.
    
4. Saving time tips: Divide roles, dont try to give everybody the same role where everybody is doing the same things , its effort waste when there's a deadline.  
    So design on Google stitch- UI (Spend time iterating it , dont throw the very first version you get, get variations, make changes to get 80% best version for the MVP)
    

Then code- Use google studio (You can directly send the google stitch mockups to google AI studio and it has a great generous limits for building stuff, assuming you have PRO , which google is giving away for free from the last 2-3 years).

You can use Google AI studio as well for codebase analysis , use 3.1 pro and it should work fine or you can use custom API from there to your vs code va extentions.

5. Prompts Library I've used, that I've never shared until now, I'll share the rudimentry version because they work good enough, you can throw them to grok or gpt and tell them to enhance this to your specific case and use them :  
Go to hackathons official page:  
Prompt 1: For analysis  
Analyze this hackathon via dedicated web search to cover every important detail, with all the important instructions, requirements, rules, timeline, evaluations as I am participating in this hackathon and intending on winning it. Save all the details to markdown file.

Here is the link : (Paste your official link with info)  
Prompt 2:  
Act as an elite hackathon strategist with 10+ years of experience helping teams win major competitions. Generate 8 hackathon project ideas that are unique , following all the regulations from the given details of hackathon. Each idea should also have an example of how the user would use it(any 2 examples) and its features in less technical vocabulary. Make sure to create ideas that fulfill judging criteria the best. In the end categorize and rank all those ideas as well on the basis of complexity, UX difficulty, "Wow" factor, Innovation score. In the end suggest your top 3 as well.

Choose your Idea and start building the mockups via stitch and then MVP prototype via google ai studio and push to github.

**Before you ship your app, run through these security fundamentals:**

The most common vulnerabilities aren't sophisticated; they're basic things like exposed API keys, weak passwords, or missing ownership checks that let one user read another's data. A quick audit across these 7 areas will cover 90% of vulnerabilities:

- **Authentication** — Hash passwords with bcrypt/argon2, expire sessions on logout, verify emails, make reset tokens single-use and short-lived, and rate-limit login attempts to block brute force
    
- **Access Control** — Every API endpoint must verify the logged-in user actually owns the data they're requesting. Never trust client-supplied IDs blindly, and protect admin routes server-side — not just in the UI
    
- **Secrets & API Keys** — No keys, tokens, or DB credentials in your frontend code or git history. Everything goes in environment variables, server-side only. Rotate anything that may have already leaked
    
- **Input Validation** — Use parameterized queries to prevent SQL injection, escape output to prevent XSS, validate file uploads strictly, and never pass user input to shell commands or eval()
    
- **Abuse & Bot Protection** — Rate-limit every public endpoint, add CAPTCHA on registration and login, set request size limits, and return proper 429 errors so bots can't hammer your app or run up your AI costs
    
- **Deployment & Monitoring** — Enforce HTTPS, set security headers (CSP, X-Frame-Options etc.), keep your database off the public internet, log auth and error events, and set up something like Sentry so you know when things go wrong
    
- **Payments & PII** — Never let raw card data touch your server (use Stripe.js), enforce pricing server-side, verify webhook signatures, encrypt sensitive user data at rest, and test your refund/cancel flows for logic bugs