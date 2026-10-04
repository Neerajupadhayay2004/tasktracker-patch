# Patch Exercise Notes

## Summary
I focused on issues that could affect correctness or user experience without changing the overall structure.

1. Fixed task-search SQL condition grouping. The original AND/OR combination could bypass archived and status filters for some description matches.
2. Removed the artificial Thread.sleep() delay from the API. It made normal searches slower without adding application value.
3. Added validation for page, pageSize, and status so invalid client input gets a clear 400 response instead of an unexpected server error.
4. Fixed React request state handling and reset pagination when search/filter changes. Errors now clear loading state and stale responses are ignored after component updates.

I also kept the standalone SQL and Oracle reference query consistent with the application query.

## What I did not change
I did not redesign the UI, add new features, or rewrite the data-access layer. I did not add search debounce because I wanted to keep the patch focused.

## Biggest remaining risk
The backend currently loads all matching rows and paginates in Java. With a much larger dataset, database-level pagination and a dedicated count query would scale better.

## Tools / AI
I used GitHub to inspect the repository and an AI assistant to help review possible issues. I reviewed the proposed changes and kept only changes I could explain and verify.
