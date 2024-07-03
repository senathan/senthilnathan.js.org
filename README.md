# senthilnathan.js.org
Subject: Summary of Today's Discussion and Action Points

Hi Manish,

As per our conversation today, please find below the summary:

1. Understanding on the prod issue:
   - No changes were made either from the UI or DB end.
   - Our analysis reveals that the UI application is accessed via BAM using a gateway, followed by views and tables that allow user access to reports.
   - You identified that a daily batch process loads data into the respective table, which is crucial for report access.

2. Discussion on earlier tickets:
   - We've encountered three significant prod issues since Q2 2023:
     - Issue 1: Unable to download a report specific to one entitlement.
       - Root Cause: A deprecated column was removed from its respective tables, breaking the report functionality.
     - Issues 2 & 3: Users faced "forbidden" errors while accessing reports.
       - Root Cause: There's suspicion that a daily batch process loading data into relevant tables might have caused these issues. Further investigation in the lower region is needed for confirmation.

   - Solution: None identified yet; investigation ongoing.

3. Moving forward:
   - We'll include testing on GMR UI in our test cases whenever there are DB changes to GMR Reports or related tables and views.

Please add anything that may have been missed or needs further attention.

Thank you for your cooperation.

Best regards,

[Your Name]  
[Your Position]  
[Your Contact Information]
