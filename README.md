WorkSchool 365 CRM & LMS for SharePoint Teams

Open Source Code Auditable

http://github.com/1337777/workschool365

Microsoft Marketplace

https://appsource.microsoft.com/en-us/product/web-apps/anthroplogicworkschool3651593890930054.anthroplogic_workschool_365


1. Create Tenant Organization with Sharepoint free, Microsoft Teams free, Microsoft Power Automate free, and Microsoft Stream free.
2. In Sharepoint Admin, create new site (with name cycle0) only from the Sharepoint template file ws365_template_zero.wsp . 
3. In Power Automate, in Environment settings, add current user as Admin user.
4. In Power Automate, in Solutions, create Microsoft Dataverse (Common Data Service) database.
5. The exported Power Automate solution file is WorkSchool365_0_0_0_0.zip, ( where all "defaultValue":".+?","type": has been erased with "defaultValue":"","type": ), (and in customizations.xml , cycle0__Graph_Notifications_Interface is listed before cycle0__Graph_Users_Webhook and cycle0__Graph_Groups_Webhook )
6. In Power Automate, import the solution file into Power Automate, the configuration environment variables envpar_config__TenantName and envpar_config__TenantDomain are required, and for the others simply enter the space character ( ) as value.
7. In Power Automate, do the 1st run of the flow cycle0__Setup by copying its HTTP trigger url address in any web browser. Wait for this run to finish.
8. In Azure Portal, in App Registrations, give admin consents to the three generated Service Principals apps: WorkSchool 365 Graph App__cycle0, WorkSchool 365 Sign App__cycle0 and WorkSchool 365 Microsoft App__cycle0 .
9. In Azure Portal, in External Identities, in User flows, associate the generated Self-service Sign-up User Flow B1X_1_WorkSchool365__cycle0 to the service principal app WorkSchool 365 Sign App__cycle0 .
10. In Power Automate, turn off the flow cycle0__Graph_Groups_Webhook , and turn off the flow cycle0__Graph_Users_Webhook .
11. In Power Automate, cancel all running instances of the flow cycle0__Graph_Notifications_Interface .
12. In Power Automate, turn on the flow cycle0__Graph_Groups_Webhook , and turn on the flow cycle0__Graph_Users_Webhook .
13. In Power Automate,  do the 2nd run of the flow cycle0__Setup by copying its HTTP trigger url address in any web browser. Wait for this run to finish.
14. In Power Automate, for each of these template flows, while they have turned On status, click Edit to open the code then Save again without modifying anything : (cycle0__SurveyQuiz__Template cycle0__Microsoft_Update_Webhook__Template cycle0__Microsoft_Create_Webhook__Template cycle0__EventReview__Template cycle0__Paypal_Webhook__Template cycle0__EventReview__Delete__Template cycle0__Stripe_Webhook__Templat cycle0__MySubscriptions__Template cycle0__Microsoft_Contact_Webhook__Template ).
15. In Power Automate, setup the owner email to generate its Sharepoint sites in either of two ways: (A) set the value of the environment variable envpar_config__OwnerEmail , then do the 3rd run of the flow cycle0__Setup by copying its HTTP trigger url address in any web browser; or alternatively (B) do the 3rd run of the flow cycle0__Setup but now append the query string  &owneremail=user@domain  at the end of the url address.
16. Test that all the templated sites and templated flows are generated and that no setup flow did fail. X. (In Azure Portal, Properties, turn off Security Defaults.)
