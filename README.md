WorkSchool 365 CRM & LMS for SharePoint Teams

Open Source Code Auditable

http://github.com/1337777/workschool365

Microsoft Marketplace

https://appsource.microsoft.com/en-us/product/web-apps/anthroplogicworkschool3651593890930054.anthroplogic_workschool_365


1. Create Tenant Organization with Sharepoint free, Microsoft Teams free, Microsoft Power Automate free, and Microsoft Stream free /!\

2. In Sharepoint Admin, create new blank site (with name cycle0) only from custom template to be uploaded later. Enter the homepage of the newly create site (/sites/cycle0), in Solution Gallery, upload and activate the Sharepoint template file ws365_template_zero.wsp into this site. Enter again the homepage of the newly create site, finish the setup of the site by choosing this newly activated custom template. 

3. In Sharepoint, enter the zero site (/sites/cycle0) again, go to the document libraries SurveyQuiz and EventReview, and upload there the template files contained in the archive folder ws365_template_zero_content

4. In Power Automate, sign-out sign-in as admin (admin@orgname.onmicrosoft.com). In My flows, create sample test flow with premium HTTP action to start free trial. In Environment settings, add current user as Admin user. In Solutions, create Microsoft Dataverse (Common Data Service) database.

5. The exported Power Automate solution file is workschool365_solution.zip . (Reminder: all secret-values "defaultValue":".+?","type": has been regexp-erased with "defaultValue":"","type": , and in customizations.xml there is this listing dependence cycle0__Graph_Notifications_Interface then cycle0__Graph_Users_Webhook then cycle0__Graph_Groups_Webhook, also there is this listing dependence cycle0__AzureAD_Signed then cycle0__Sharepoint_Copy_List then cycle0__GroupsList then cycle0__Setup )

6. In Power Automate, import this solution file into Power Automate, enter the connections (where for the HTTP with Azure AD connection, https://graph.microsoft.com is both the base url and app id uri),  enter the required configuration environment variables envpar_config__TenantName (orgname) and envpar_config__TenantDomain (orgname.onmicrosoft.com). And for the others configuration simply enter the space character ( ) as value, these will be filled automatically. Wait for the import to finish. Sign-out sign-in again as admin (admin@orgname.onmicrosoft.com).

7. In Power Automate, In this imported Solution, optionally configure any of the default environment variables envpar_config__CyclesNumber (4) , envpar_config__CyclesRename (cycle) , envpar_config__CycleZeroName (cycle0) , envpar_config__PaypalApiPrefix (https://api.paypal.com). Next, (Turn off then) Turn on these flows in this dependent sequence: starting with cycle0__AzureAD_Signed then cycle0__Sharepoint_Copy_List then cycle0__GroupsList then cycle0__Setup. Also Turn on each and all the remaining flows. Then do the 1st run of the flow cycle0__Setup by copying its HTTP trigger url address in any web browser. Wait for this run to finish.

8. In Azure Portal, in App Registrations, give admin consents to the three generated Service Principals apps: WorkSchool 365 Graph App__cycle0, WorkSchool 365 Sign App__cycle0 and WorkSchool 365 Microsoft App__cycle0 .

9. In Power Automate, wait 15 minutes, do the 2nd run of the flow cycle0__Setup by copying its HTTP trigger url address in any web browser. Wait for this run to finish.

10. In Azure Portal, in External Identities, in User flows, associate the generated Self-service Sign-up User Flow B1X_1_WorkSchool365__cycle0 to the service principal app WorkSchool 365 Sign App__cycle0 .

11. In Power Automate, for each of these template flows, while they have turned On status, click Edit to open the code then Save again without modifying anything : cycle0__SurveyQuiz__Template , cycle0__Microsoft_Update_Webhook__Template , cycle0__Microsoft_Create_Webhook__Template , cycle0__EventReview__Template , cycle0__Paypal_Webhook__Template , cycle0__EventReview__Delete__Template , cycle0__Stripe_Webhook__Template , cycle0__MySubscriptions__Template , cycle0__Microsoft_Contact_Webhook__Template .

12. In Power Automate, setup the owner email to generate its Sharepoint sites cycle1, cycle2, cycle3 in either of two ways: 
  (A) set the value of the environment variable envpar_config__OwnerEmail (owneruser@extdomain) , then do the 3rd run of the flow cycle0__Setup by copying its HTTP trigger url address in any web browser; or alternatively 
  (B) do the 3rd run of the flow cycle0__Setup but now append the query string  &owneremail=owneruser@extdomain  at the end of its trigger url address.

13. Test that all the templated sites and templated flows are generated and that no setup flow did fail. (X. In Azure Portal or Graph Explorer, set admin@orgname.onmicrosoft.com user as external B2B using alternate email.) (XX. In Azure Portal, in Properties, turn off Security Defaults.)
