## Executive Summary

Bedrock conducted a six-week manual QA engagement for the LinenLane e-commerce relaunch from October 13 through November 22, 2026. The engagement covered 11 builds and was led by Priya Subramanian, Pod Lead, with testing focused on the planned November 26, 2026 launch.

The Bedrock team designed 187 unique test cases, with 165 retained in the master suite after some cases were retired during execution. All 165 applicable cases were executed against every build, and the team identified 64 unique defects during the engagement.

The pass rate increased from 24% in Build 1 to 75% in Build 6, where a plateau began, and reached 91% in Build 11. By engagement close, 62 defects had been fixed and verified. Across the engagement, 8 new defects and 3 regressions were recorded, resulting in a net positive improvement of 51 defects.

The most consequential finding was a race condition in the checkout flow that allowed duplicate-submitted orders under network latency. The issue was identified in Build 4, fixed in Build 5, and verified in Build 6. LinenLane's revenue model estimated a potential cost of $40,000 per high-traffic event if the issue had shipped.

Bedrock recommends extending the QA engagement for two weeks after launch to monitor account migration and validate post-launch hot fixes. Account migration remains the highest residual-risk area in the test coverage assessment.

At engagement close, with 0 Critical defects, 0 High defects, and 2 Low defects deferred in the Catalog feature area, Bedrock supports the November 26 launch with the stated recommendations.

### Verification Checklist

- Six-week engagement: Fact Sheet, Engagement type.
- October 13 to November 22, 2026: Fact Sheet, Engagement dates.
- 11 builds: Fact Sheet, Builds tested.
- November 26, 2026 launch: Fact Sheet, Launch date.
- 187 unique test cases: Fact Sheet, Test case totals.
- 165 cases in the master suite: Fact Sheet, Test case totals.
- All 165 applicable cases executed against every build: Fact Sheet, Test case totals.
- 64 unique defects: Fact Sheet, Defect totals.
- 24% pass rate in Build 1: Fact Sheet, Pass rate trajectory.
- 75% pass rate in Build 6: Fact Sheet, Pass rate trajectory.
- Plateau beginning at Build 6: Fact Sheet, Pass rate trajectory.
- 91% pass rate in Build 11: Fact Sheet, Pass rate trajectory.
- 62 defects fixed and verified: Fact Sheet, Defect totals.
- 8 new defects: Fact Sheet, Pass rate trajectory.
- 3 regressions: Fact Sheet, Pass rate trajectory.
- 51 defects net positive: Fact Sheet, Pass rate trajectory.
- Race condition identified in Build 4, fixed in Build 5, and verified in Build 6: Fact Sheet, Most consequential finding.
- $40,000 estimated cost per high-traffic event: Fact Sheet, Most consequential finding.
- Two-week post-launch QA extension: Fact Sheet, Most consequential recommendation.
- Account migration as the highest residual-risk area: Fact Sheet, Most consequential recommendation.
- 0 Critical, 0 High, and 2 Low defects open: Fact Sheet, Launch readiness assessment.
- 2 Low defects in the Catalog feature area: Fact Sheet, Defect totals and Open items and deferred work.
- Bedrock support for the November 26 launch: Fact Sheet, Launch readiness assessment.