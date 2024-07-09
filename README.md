# senthilnathan.js.org

As we discussed earlier, we have two steps of authentication:

BAM for application
Specific to reports
The log clearly mentions that the user was denied access to a specific report because the application can't retrieve specific data from the DB. I don't believe this is an environment or Java setup issue.

To further investigate, we can replicate the scenario in the lower region (UAT). We can empty the view and test if the report is accessible, which should help us confirm the issue.
