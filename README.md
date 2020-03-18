# Salesforce-Admin-Case-Study-ABC-Limited

Scenario:
Sarah Fisher, the Director of Sales at ABC Labs, wants to implement the concept of "at-risk" opportunities. Sarah should have the ability to flag an opportunity as "at-risk”. If an opportunity is flagged as at-risk and the Amount is greater than $100,000, we want to automatically create a related record to the opportunity, called a Deal Support Request. The Deal Support Request should be owned by Sarah Fisher, and include the following data points.

Note: At ABC Labs Deal Support Requests are also created by Sales Team for tracking work outside existing opportunity and hence not all Deal Support Request have Opportunity on them.

1. A Status picklist that defaults to "Open"
2. An "Assignee" field where Sarah can assign the Deal Support Request to another user
3. Two read-only fields that shows the Opportunity's amount and Close Date in real time
4. On Account detail page Sarah likes to see how many Opportunities on the account are at-risk.

Please note that you can leave all users inactive as can only have one active end users in a Salesforce development sandbox;

Solution:

Below are the detailed steps involved in building the solution for the case study:


1. ‘Risk Flag’ - Custom checkbox field creation in Opportunity object
2. Add the field from Step 1 in Opportunity Sales layout and assign it to the profile of Sarah Fisher
3. Create new Object ‘Deal Support Request’ and provide access to the profile of Sarah Fisher (Profile name: Custom: ABC Sales Manager) for this object.
4. Create Lookup fields ’Opportunity’ and ‘Assignee’ (User) in the Deal Support Request object.
5. Create Picklist field ‘Status’ in the Deal Support Request object.
6. Create formula fields ’Opportunity Amount’ and ‘Opportunity Close Date’ in the Deal Support Request object.
7. Add the fields created in steps 4,5,6 to the layout of Deal Support Request object.
8. Create Custom label ‘Oppty Threshold Deal Support’ to store the Opportunity amount limit which will be a criteria for triggering Deal Support Request.
9. Create Custom label ‘Deal Support Request Default Owner’ to store the id of the default owner for auto created Deal Support Request records.
10. Create a process builder to auto-populate Deal Support Request record when an Opportunity is above 100000 USD and its risk Flag is true.
11. Use the custom labels created from step 8 and 9 in the Process Builder to create a scalable Process builder which don’t need to be changed when the Director of Sales change or if the business decides to change the upper limit value at Opportunity level for auto creating Deal Support Request.
12. Process Builder should be set in such a way that auto created Deal Support Request should be assigned to Sarah Fisher and lookup for Opportunity should be populated.
13. Include the Deal Support Request as a Related List to the Opportunity view.
14. Include the column Risk flag in the Opportunity Related List of Account View.
15. Create a tab for Deal Support Request so that Sales users can use to manually create Deal Support Request without tagging Opportunity.
