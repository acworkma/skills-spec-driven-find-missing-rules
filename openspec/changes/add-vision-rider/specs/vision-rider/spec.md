## ADDED Requirements

### Requirement: Setup lead time
A vision rider MUST take effect on the first day of a month at least 30 calendar
days after its configuration is approved; a shorter start MUST have approval
from both the product owner and underwriting.

Source: Answer 4.

#### Scenario: Standard start
- **GIVEN** the rider's configuration is approved
- **WHEN** the rider takes effect without a shorter-start exception
- **THEN** its effective date is the first day of a month at least 30 calendar days after configuration approval

#### Scenario: Short-notice start needs approval
- **GIVEN** a requested start is on the first day of a month fewer than 30 calendar days after configuration approval
- **WHEN** approval from either the product owner or underwriting is missing
- **THEN** the rider does not take effect on that requested date

#### Scenario: Short-notice start has both approvals
- **GIVEN** a requested start is on the first day of a month fewer than 30 calendar days after configuration approval
- **WHEN** both the product owner and underwriting approve the shorter start
- **THEN** the setup lead-time exception is approved

#### Scenario: Requested start is not the first day of a month
- **GIVEN** a requested effective date is not the first day of a month
- **WHEN** the rider's effective date is determined
- **THEN** the rider does not take effect on that requested date

### Requirement: Independent configuration approval
A second configuration analyst MUST review and approve the configuration;
the analyst who built it MUST NOT perform that review or approval.

Source: Answer 1.

#### Scenario: Independent review and approval
- **GIVEN** a configuration built by one configuration analyst
- **WHEN** the configuration is reviewed and approved
- **THEN** a second configuration analyst who did not build it performs the review and approval

#### Scenario: Builder attempts review or approval
- **GIVEN** a configuration analyst built the configuration
- **WHEN** that analyst attempts to perform its review or approval
- **THEN** that analyst cannot perform the review or approval

### Requirement: Dependent coverage
The rider MUST cover dependents when the group's medical plan covers
dependents, subject to the same age limit as that plan.

Source: Answer 2.

#### Scenario: Eligible dependent is covered
- **GIVEN** the group's medical plan covers dependents
- **AND** a dependent meets that plan's age limit
- **WHEN** rider coverage is determined
- **THEN** the dependent is covered by the rider

#### Scenario: Medical plan does not cover dependents
- **GIVEN** the group's medical plan does not cover dependents
- **WHEN** rider coverage is determined
- **THEN** dependents are not covered by the rider

#### Scenario: Dependent exceeds the age limit
- **GIVEN** the group's medical plan covers dependents
- **AND** a dependent exceeds that plan's age limit
- **WHEN** rider coverage is determined
- **THEN** the dependent is not covered by the rider

### Requirement: New-hire waiting period
A new hire in a waiting period MUST receive rider coverage when their medical
coverage starts, not before.

Source: Answer 3.

#### Scenario: Medical coverage starts
- **GIVEN** a new hire has been in a waiting period
- **WHEN** their medical coverage starts
- **THEN** their rider coverage starts

#### Scenario: Rider coverage is requested before medical coverage starts
- **GIVEN** a new hire is in a waiting period and their medical coverage has not started
- **WHEN** rider coverage is requested before their medical coverage starts
- **THEN** their rider coverage does not start before their medical coverage

### Requirement: Go-live prerequisites
The rider MUST NOT go live until Fabrikam Vision Services accepts a synthetic
test eligibility file and the eight standard test claims pay as expected.

Source: Answer 5.

#### Scenario: Both prerequisites are satisfied
- **GIVEN** Fabrikam Vision Services has accepted a synthetic test eligibility file
- **WHEN** the eight standard test claims pay as expected
- **THEN** both go-live prerequisites are satisfied

#### Scenario: Test eligibility file is not accepted
- **GIVEN** the eight standard test claims pay as expected
- **WHEN** Fabrikam Vision Services has not accepted the synthetic test eligibility file
- **THEN** the rider does not go live

#### Scenario: A standard test claim does not pay as expected
- **GIVEN** Fabrikam Vision Services has accepted a synthetic test eligibility file
- **WHEN** any of the eight standard test claims does not pay as expected
- **THEN** the rider does not go live

### Requirement: Coverage ending before go-live
If a group's coverage ends before go-live, the rider request MUST be cancelled
and Fabrikam Vision Services MUST be told to drop the group.

Source: Answer 6.

#### Scenario: Group coverage ends before launch
- **GIVEN** a group has a rider request that has not gone live
- **WHEN** the group's coverage ends
- **THEN** the rider request is cancelled
- **AND** Fabrikam Vision Services is told to drop the group

### Requirement: Mid-year allowances and frequency limits
For a rider that starts mid-year, allowances and frequency limits MUST start
fresh on the rider's effective date and MUST NOT be prorated.

Source: Answer 7.

#### Scenario: Mid-year rider starts
- **GIVEN** a rider starts mid-year
- **WHEN** its effective date arrives
- **THEN** its allowances and frequency limits start fresh

#### Scenario: Proration is attempted
- **GIVEN** a rider starts mid-year
- **WHEN** proration is attempted for its allowances or frequency limits
- **THEN** neither is prorated
- **AND** both start fresh on the rider's effective date