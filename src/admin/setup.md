# Overall setup

The rust-project-goals repository is set up as follows

* an mdbook for generating the main content
* a Rust binary in `src` that serves as
    * a runnable utility for doing various admin functions on the CLI (e.g., generating a draft RFC)
    * an mdbook preprocessor for generating content like the list of goals
    * a utility invoked in CI that can query github and produce a JSON with the goal status
* pages on the Rust website that fetches JSON data from rust-project-goals repo to generate content
    * the JSON data is generated by the Rust binary
* tracking issues for each active project goal:
    * tagged with `C-tracking-issue`
    * and added to the appropriate milestone
* triagebot modifications to link Zulip and the repo tracking issues 
    * the command `&#64;triagebot ping-goals N D` will ping all active goal points of contact to ask them to add updates
        * *N* is a threshold number of days; if people have posted an update within the last N days, we won't bother them. Usually I do this as the current date + 7, so that people who posted during the current month or the last week of the previous month don't get any pings.
        * *D* is a word like `Sep-22` that indicates the day
    * the bot monitors for comments on github and forwards them to Zulip

