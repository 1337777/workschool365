WorkSchool 365 CRM & LMS for SharePoint Teams

Open Source Code Auditable

http://github.com/1337777/workschool365

Microsoft Marketplace

https://appsource.microsoft.com/en-us/product/web-apps/anthroplogicworkschool3651593890930054.anthroplogic_workschool_365


1. Create Tenant Organization with Sharepoint free, Microsoft Teams free, Microsoft Power Automate free, and Microsoft Stream free /!\

2. In Sharepoint Admin, create new site (with name cycle0) only from the Sharepoint template file ws365_template_zero.wsp . 

3. In Power Automate, sign-out sign-in as admin (admin@orgname.onmicrosoft.com). In My flows, create sample test flow with premium HTTP action to start free trial. In Solutions, create Microsoft Dataverse (Common Data Service) database, while In Environment settings, add current user as Admin user, 

4. The exported Power Automate solution file is workschool365_solution.zip, ( where all "defaultValue":".+?","type": has been erased with "defaultValue":"","type": , and in customizations.xml , cycle0__Graph_Notifications_Interface is listed before cycle0__Graph_Users_Webhook and cycle0__Graph_Groups_Webhook )

5. In Power Automate, import this solution file into Power Automate, enter the required configuration environment variables envpar_config__TenantName (orgname) and envpar_config__TenantDomain (orgname.onmicrosoft.com). And for the others configuration simply enter the space character ( ) as value, these will be filled automatically.

6. In Power Automate, In the importer Solutions, Turn on these flows in this dependent sequence: starting with cycle0__Sharepoint_Copy_List then cycle0__GroupsList then cycle0__Setup. Then do the 1st run of the flow cycle0__Setup by copying its HTTP trigger url address in any web browser. Wait for this run to finish.

7. In Azure Portal, in App Registrations, give admin consents to the three generated Service Principals apps: WorkSchool 365 Graph App__cycle0, WorkSchool 365 Sign App__cycle0 and WorkSchool 365 Microsoft App__cycle0 .

8. In Power Automate, wait 15 minutes, do the 2nd run of the flow cycle0__Setup by copying its HTTP trigger url address in any web browser. Wait for this run to finish.

9. In Azure Portal, in External Identities, in User flows, associate the generated Self-service Sign-up User Flow B1X_1_WorkSchool365__cycle0 to the service principal app WorkSchool 365 Sign App__cycle0 .

10. In Power Automate, for each of these template flows, while they have turned On status, click Edit to open the code then Save again without modifying anything : cycle0__SurveyQuiz__Template , cycle0__Microsoft_Update_Webhook__Template , cycle0__Microsoft_Create_Webhook__Template , cycle0__EventReview__Template , cycle0__Paypal_Webhook__Template , cycle0__EventReview__Delete__Template , cycle0__Stripe_Webhook__Template , cycle0__MySubscriptions__Template , cycle0__Microsoft_Contact_Webhook__Template .

11. In Power Automate, setup the owner email to generate its Sharepoint sites cycle1, cycle2, cycle3 in either of two ways: 
  (A) set the value of the environment variable envpar_config__OwnerEmail (owneruser@extdomain) , then do the 3rd run of the flow cycle0__Setup by copying its HTTP trigger url address in any web browser; or alternatively 
  (B) do the 3rd run of the flow cycle0__Setup but now append the query string  &owneremail=owneruser@extdomain  at the end of its trigger url address.

12. Test that all the templated sites and templated flows are generated and that no setup flow did fail. (X. In Azure Portal or Graph Explorer, set admin@orgname.onmicrosoft.com user as external B2B using alternate email.) (XX. In Azure Portal, in Properties, turn off Security Defaults.)
