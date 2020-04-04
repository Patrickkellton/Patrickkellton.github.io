---
published: true
---
### Incident stats


SELECT FILTER(count(*), where eventType() = 'IssueCreated') AS 'Created issues' FROM IssueCreated since last week COMPARE WITH 1 week ago

SELECT FILTER(count(*), where eventType() = 'IssueMerged') AS 'Correlated issues' FROM IssueMerged since last week COMPARE WITH 1 week ago


SELECT 100 * FILTER(count(*), where eventType() = 'IssueMerged') / FILTER(count(*), where eventType() = 'IssueCreated') AS 'Correlation Rate' FROM IssueCreated, IssueMerged since last week COMPARE WITH 1 week ago


SELECT 100 * (1 - (FILTER(count(*), where eventType() = 'IssueActivated') / FILTER(count(*), where eventType() = 'IssueCreated'))) AS 'Noise Reduction Rate' FROM IssueCreated, IssueActivated since 1 week ago COMPARE WITH 1 week ago


SELECT FILTER(count(*), where eventType() = 'IssueCreated') AS 'Created issues' FROM IssueCreated TIMESERIES 1 day SINCE last week FACET sources


SELECT FILTER(count(*), where eventType() = 'IssueMerged') AS 'Correlated issues' FROM IssueMerged TIMESERIES 1 day SINCE last week


SELECT 100 * FILTER(count(*), where eventType() = 'IssueMerged') / FILTER(count(*), where eventType() = 'IssueCreated') AS 'Correlation Rate' FROM IssueCreated, IssueMerged TIMESERIES 1 day since last week COMPARE WITH 1 week ago


SELECT 100 * (1 - (FILTER(count(*), where eventType() = 'IssueActivated') / FILTER(count(*), where eventType() = 'IssueCreated'))) AS 'Noise Reduction Rate' FROM IssueCreated, IssueActivated TIMESERIES 1 day since last week COMPARE WITH 1 week ago

SELECT (FILTER(count(*), where eventType() = 'IssueActivated')) as 'activated issues', (FILTER(count(*), where eventType() = 'IssueCreated')) as 'created issues' FROM IssueCreated, IssueActivated TIMESERIES 1 day since last week COMPARE WITH 1 week ago


SELECT uniquecount(issueId) as 'correlated issues' FROM IssueMerged facet ruleName since 1 week ago


SELECT priority, sources, title, correlationRuleIds as 'correlation decision ids', eventCount FROM IssueClosed since 1 week ago

