Assessment Notes

Summary of Fixes

1. Fixed SQL `AND`/`OR` precedence in task search. Search results now correctly respect both archived and status filters. Updated the Spring Boot query and the Oracle reference query.
2. Removed artificial API latency caused by a query-length-based `Thread.sleep()`.
3. Fixed the frontend task-loading state so failed requests clear the loading state and display the error. Previous errors are also cleared when a new request starts.
4. Added validation for pagination parameters. Invalid `page` or `pageSize` values now return a client error instead of causing a server error.
5. Added validation for task status. Invalid status values now return a client error with the allowed values.

What I Did Not Change

I did not rewrite the existing pagination implementation, data model, UI structure, or dependency versions because they were outside the highest-value confirmed issues and the assessment requested a focused time-boxed solution.

Biggest Remaining Risk

The backend currently retrieves all matching tasks and performs pagination in application memory. This could become inefficient with a significantly larger dataset. I left it unchanged to keep the scope focused on the confirmed functional and reliability issues.

AI / Tools Used

Used ChatGPT as an AI-assisted development and review tool for identifying issues, reasoning about root causes, and validating fixes. Used PowerShell, Maven, npm/Vite, and manual API/UI testing to verify the changes.
