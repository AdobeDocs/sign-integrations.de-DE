---
title: Veeva Vault Installation Guide
description: Installation guide for enabling the Adobe Sign integration with Veeva
product: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: 5d61a428-06e4-413b-868a-da296532c964
source-git-commit: 1026d696587b898b6e1132ca1a69642d799dcf1d
workflow-type: tm+mt
source-wordcount: '3909'
ht-degree: 3%

---

# [!DNL Veeva Vault] Installationshandbuch{#veeva-installation-guide}

[****](https://adobe.com/go/adobesign-support-center_de)

## Übersicht {#overview}

[!DNL Veeva Vault] [!DNL Veeva Vault] A &quot;Vault&quot; is a content and data repository with typical usage for regulatory filings, research reporting, grants applications, general contracting, and more. A single enterprise can have multiple &#39;vaults&#39; that must be maintained separately.

The high-level steps to complete the integration are:

* Activate your Administrative account in Adobe Acrobat Sign (New Customers Only).
* Create objects to track the history of an agreement lifecycle in Vault.
* Create a new Security profile.
* [!DNL Veeva Vault]
* Create document fields and renditions.
* Configure web actions and update the document lifecycle.
* Create document type user and user role setup.
* Connect Veeva Vault to Adobe Acrobat Sign using middleware.

>[!NOTE]
>
>Adobe Sign admin must perform the Adobe Acrobat Sign setup steps within Adobe Acrobat Sign.

## Konfigurieren Sie [!DNL Veeva Vault] {#configure-veeva}

[!DNL Veeva Vault]

### Schritt 1. Create Group {#create-group}

[!DNL Vault]** **

![](images/create-admin-group.png)

### Schritt 2. Deploy the package {#deploy-package}

[](https://helpx.adobe.com/content/dam/help/en/PKG-AdobeSign-Integration.zip) Once deployed, the package creates:

* Custom objects: Signature object, Signatory object, Signature Event object, Process Locker object
* Signature object page layout
* Signature Event object page layout
* Signatory object page layout
* Process Locker object page layout
* Adobe Sign Integration Task Log object page layout
* Adobe Sign Rendition type
* Original Rendition type
* Shared field signature__c
* Adobe Sign Web Action
* Cancel Adobe Sign Web Action
* Adobe Sign Admin Actions Permission set
* Adobe Sign Integration Profile security profile
* Application role Adobe Sign Admin Role
* Document type group &#39;Adobe Sign Document&#39;
* Adobe Sign Integration Task log object

#### Signature object {#signature-object}

Signature object is created to store agreement-related information. A Signature object is a database that contains information under following specific fields:

****

| Feld | Bezeichnung | Typ | Beschreibung |
| --- | --- | ---| --- | 
| external_id__c | Vereinbarungs-ID | String (100) | Holds the Adobe Acrobat Sign’s unique agreement id |
| file_hash__c | File Hash | String (50) | Holds the md5 checksum of the file that has been sent to Adobe Acrobat Sign |
| name__v | Name | String (128) | Holds the agreement name |
| sender__c | Absender | Object (User) | Holds the reference to the Vault user that has created the agreement |
| signature_status__c | Signature Status | String (75) | Holds the agreement’s status in Adobe Acrobat Sign |
| signature_type__c | Signaturtyp | String (20) | Holds the agreement’s signature type in Adobe Acrobat Sign (WRITTEN or ESIGN) |
| start_date__c | Anfangsdatum | Datum/Uhrzeit | Date when agreement has been sent for signature |
| cancellation_date__c | Cancellation Date | Datum/Uhrzeit | Holds the date when agreement has been cancelled. |
| completion_date__c | Completion Date | Datum/Uhrzeit | Holds the date when agreement has been completed. |
| viewable_rendition_used__c | Viewable Rendition Used | Boolescher Wert | Flag that indicates if viewable rendition has been sent for signature. (by default, it is true) |
| plugin_version__c | Plugin Version | Text (10) | It is used to allow the appropriate processing of all agreements created before a new version 4.0 is deployed. Note: After 4.0 custom web application version is deployed, this field will be set to 4.0 each time Signature record is created. |
| external_environment__c | External Environment | Text (20) | Holds the Adobe Sign’s environment name in which the agreement has been created. |

![](images/signature-object-details.png)

#### Signatory object {#signatory-object}

Signatory object is created to store information related to the participants in an agreement. It contains information under following specific fields:

****

| Feld | Bezeichnung | Typ | Beschreibung |
| --- | --- | ---| --- | 
| email__c | E-Mail | String (120) | Holds the Adobe Acrobat Sign’s unique agreement id |
| external_id__c | Participant Id | String (80) | Holds Adobe Acrobat Sign unique participant’s identifier |
| name__v | Name | String (128) | Holds Adobe Acrobat Sign participant’s name |
| order__c | Auftrag | Zahl | Holds Adobe Acrobat Sign agreement participant’s order number |
| role__c | Rolle | String (30) | Holds Adobe Acrobat Sign agreement participant’s role |
| signature__c | Signatur | Object (Signature) | Holds the reference to the signature parent record |
| signature_status__c | Signature Status | String (100) | Holds Adobe Acrobat Sign agreement participant’s status |
| user__c | Benutzer | Object (User) | Holds the reference to the signatory’s user record if participant is a Vault user |

![](images/signatory-object-details.png)

#### Signature Event object {#signature-event}

Signature Event object is created to store an agreement&#39;s event-related information. It contains information under following specific fields:

Signature Event Object Fields

| Feld | Bezeichnung | Typ | Beschreibung |
| --- | --- | ---| --- | 
| acting_user_email__c | Aktive Benutzer-E-Mail | Zeichenfolge | Holds the email of Adobe Acrobat Sign user that performed the action that caused event to be generated |
| acting_user_name__c | Acting User Name | Zeichenfolge | Holds the name of Adobe Acrobat Sign user that performed the action that caused event to be generated |
| description__c | Beschreibung | Zeichenfolge | Holds the Adobe Acrobat Sign event’s description |
| event_date__c | Ereignisdatum | Datum/Uhrzeit | Holds the Adobe Acrobat Sign event’s date and time |
| event_type__c | Event type | Zeichenfolge | Holds the Adobe Acrobat Sign event’s type |
| name__v | Name | Zeichenfolge | Auto-generated event name |
| participant_comment__c | Participant comment | Zeichenfolge | Holds the Adobe Acrobat Sign participant’s comment if any |
| participant_email__c | Teilnehmer-E-Mail | Zeichenfolge | Holds the Adobe Acrobat Sign participant’s email |
| participant_role__c | Rolle des Teilnehmers | Zeichenfolge | Holds the Adobe Acrobat Sign participant’s role |
| signature__c | Signatur | Object (Signature) | Holds the reference to the signature parent record |
| external_id__c | External ID | Text (200) | Holds Agreement Event identifier generated by Adobe Sign. |

![Bild](images/signature-event-object-details.png)

#### Process Locker object {#process-locker}

A Process Locker object is created to lock the Adobe Acrobat Sign integration process. It does not require any custom fields.

![](images/process-locker-details.png)

#### Adobe Sign Integration Task Log Object {#task-log}

Create Adobe Sign Integration Task Log (as_int_task_log__c). It is high volume object that is used to trace the execution of AgreementsEventsSynchronizerJob and AgreementsEventsProcessingJob.
AgreementsEventsSynchronizerJob: This task ensures that all missing Agreement Events from Adobe Sign are created as active Signature Events in Vault for all Signatures created in Vault in the past N days.
AgreementsEventsProcessingJob: This task ensures that all Documents with active Signature Event records are processed depending on event type.

Adobe Sign Integration Task Log Object Fields

| Feld | Bezeichnung | Typ | Beschreibung |
|---|---|---|---| 
| start_date__c | Anfangsdatum | Datum/Uhrzeit | Task Start date |
| end_date__c | Enddatum | Datum/Uhrzeit | Task End date |
| task_status__c | Task Status | Picklist | Holds task status: Completed (task_completed__c) Completed With Errors (task_completed_with_errors__c) Failed (task_failed__c) |
| task_type__c | Task Type | Picklist | Holds task type: Agreements Events Synchronization (agreements_events_synchronization__c) Agreements Events Processing (agreements_events_processing__c) |
| messages__c | Nachricht | Long (32000) | Holds task message |

![](images/task-log.png)

![](images/task-log-fields.png)

The Signature, Signatory, Signature Event, Process Locker, and Task Log objects that come as a part of the deployment package have the &#39;Audit data changes for this object&#39; property enabled by default.

**** This setting is off by default. Once you enable this setting and create records, you can no longer disable it. If this setting is off and records exist, only a Vault Owner can update the setting.

#### **** {#display-participants-history}

[](https://vvtechpartner-adobe-rim.veevavault.com/ui/#admin/content_setup/object_schema/pagelayout?t=signature__c&amp;d=signature_detail_page_layout__c) The Page Layout has sections for Participants and History.

* **

   ![Bild](images/edit-related-objects.png)

* You can edit the columns to be displayed for the Participants, as shown below.

   ![Bild](images/set-columns-to-display.png)

* **

   ![Bild](images/edit-related-object-in-history.png)

* You can edit the columns to be displayed for the History, as shown below.

   ![Bild](images/select-columns-to-display.png)

#### **** {#view-participants-audit-history}

* To view Participants and Audit history for the Adobe Acrobat Sign document, select the link in the &#39;Adobe Signature&#39; section of the document.

   ![Bild](images/view-participants-audit-history.png)

* The page that opens displays the Participants and History for the Adobe Acrobat Sign document, as shown below.

   ![Bild](images/participants-and-history.png)

* View the audit trail for Signature as shown below.

   ![Bild](images/audit-trail.png)

### Schritt 3. Setup Security profiles {#security-profiles}

Successful package deployment in Step 2 creates Adobe Sign Integration profile. The Adobe Sign Integration Profile is assigned to the system account and is used by the integration when calling Vault APIs. This profile allows permissions for:

* Vault APIs
* Reading, creating, editing, and deleting: Signature, Signatory, Signature Events, and Process Locker objects

You must update the Adobe Sign Admin Group (created in Step 1) by setting the included security profile to Adobe Sign Integration Profile, as shown in the image below.

![](images/security-profiles.png)

### Schritt 4. Benutzer erstellen {#create-user}

The Vault system account user of Adobe Acrobat Sign integration must:

* Have an Adobe Sign Integration Profile
* Have a Security profile
* Have Specific security policy that disables password expiration
* Be a member of Adobe Sign Admin Group.

To do so, follow the steps below:

1. Create Vault system account user of Adobe Acrobat Sign integration.

   ![](images/create-user.png)

2. Add the user to the Adobe Sign Admin Group.

   ![](images/add-user.png)

### Schritt 5. Configure Document Type Group {#create-document-type-group}

When you deploy the Adobe Acrobat Sign package, it creates a Document Type Group record called &#39;Adobe Sign Document&#39;.

![](images/document-type-groups.png)

You must add this document type group for all document classifications that are eligible for Adobe Acrobat Sign process. Since document type group property is not inherited from type to subtype nor from subtype to classification level, it must be set for each document’s classification that is eligible for Adobe Acrobat Sign.

![](images/document-edit-details.png)

**** ************

![](images/create-setup-field.png)

![](images/document-type.png)

### Schritt 6. Create User Role Setup {#create-user-role-setup}

Once lifecycles is(are) properly configured, the system should ensure that Adobe Sign Admin user is added by DAC for all documents that are eligible for Adobe Acrobat Sign process. This is done by creating the appropriate User Role Setup record that specifies:

* Document Type Group as Adobe Sign Document
* Application Role as Adobe Sign Admin Role
* Integration user

![](images/user-role-setup.png)

### Schritt 7. Setup Document Fields {#create-fields}

The package deployment creates following new shared document field that are required for establishing the integration:

* Signature (signature__c)

![Bild](images/document-fields.png)

To set up Document Fields:

1. ********
1. ********

   ![Bild](images/create-display-section.png)

1. ****
1. Add the two shared fields to all document types that are eligible for Adobe Acrobat Signature. ********

   ![Bild](images/create-document-fields.png)

   ![Bild](images/add-existing-fields.png)

   ![Bild](images/use-shared-fields.png)

1. Both fields must have a specific security that allows only members of Adobe Sign Admin Group to update their values.

   ![Bild](images/security-overrides.png)

Disable Vault Overlays (disable_vault_overlays__v) is an existing shared field. Optionally, the field can have a specific security that allows only members of Adobe Sign Admin group to update its value.

### Schritt 8. Declare Document Renditions {#declare-renditions}

** You must declare the Adobe Sign rendition for each document type that is eligible for Adobe Acrobat Signature.

![](images/rendition-type.png)

![Bild](images/edit-details-clinical.png)

**

![Bild](images/original-rendition.png)

### Schritt 9. Update Web Actions {#web-actions}

Adobe Acrobat Sign and Vault integration requires you to create and configure following two web actions:

* ****

   <https://api.na1.adobesign.com/api/gateway/veevavaultintsvc/partner/agreement?docId=${Document.id}&majVer=${Document.major_version_number__v}&minVer=${Document.minor_version_number__v}&vaultid=${Vault.id}&useWaitPage=true>

   ![](images/create-adobe-sign.png)

* ****

   <https://api.na1.adobesign.com/api/gateway/veevavaultintsvc/partner/agreement/cancel?docId=${Document.id}&majVer=${Document.major_version_number__v}&minVer=${Document.minor_version_number__v}&vaultid=${Vault.id}&useWaitPage=true>

   ![](images/cancel-adobe-sign.png)

### Schritt 10. Update document lifecycle {#document-lifecycle}

For each document type eligible for Adobe Signature, you must update corresponding document lifecycle by adding new lifecycle role and states.

Adobe Acrobat Sign agreement lifecycle has following states:

* DRAFT
* AUTHORING or DOCUMENTS_NOT_YET_PROCESSED
* OUT_FOR_SIGNATURE or OUT_FOR_APPROVAL
* SIGNED or APPROVED
* ABGEBROCHEN
* ABGELAUFEN

To update document lifecycle, follow the steps below:

1. Add Lifecycle role. Adobe Sign Admin application role must be added in all lifecycles used by documents eligible for Adobe  Acrobat Signature, as shown below.

   ![](images/document-lifecycle-admin-role.png)

   The admin role should be created with the following options:

   * Enabled Dynamic Access Control.
   * Document sharing rules that include only Document Type Group, as shown in the image below.

   ![](images/adobe-sign-sharing-rule.png)

2. Create Lifecycle states. ************************ Next, create the following states:

   * In Adobe Sign Draft

   ![](images/create-draft-state.png)

   * In Adobe Sign Authoring

   ![](images/create-authoring-state.png)

   * In Adobe Signing

   ![](images/create-signing-state.png)

3. Add User Actions to the below listed states.

   When a Vault document is sent to Adobe Acrobat Sign, its state should correspond to the state in which the agreement is. To do so, add following states in every lifecycle used by documents eligible for Adobe Signature:

   * **** Based on the document type, it can be Draft state or Reviewed. Document state label can be customized as per the customer’s requirements. Before Adobe Signature state must define following two user actions:

      * ** The name of this user action must be the same for all document types for any lifecycle.
      * Action that calls the Web Action ‘Adobe Sign’. This state must have security that allows Adobe Sign Admin Role to: view document, view content, edit fields, edit relationships, download source, manage viewable rendition, and change state.

      ![](images/lifecycle-state1.png)

      * ******
      ******************** ******

      ![Bild](images/lifecycle-state-reviewed.png)
      ![Bild](images/lifecycle-state-reviewed-1.png)
      ![Bild](images/lifecycle-state-reviewed-2.png)

   * **** It is a required state. This state must define following five user actions:

      * ** The name of this user action must be the same for all document types for any lifecycle.
      * ** The name of this user action must be the same for all document types for any lifecycle.
      * ** The name of this user action must be the same for all document types for any lifecycle.
      * **
      * ** This state must have security that allows Adobe Sign Admin role to: view document, view content, edit fields, edit relationships, download source, manage viewable rendition, and change state.

      ![](images/lifecycle-state2.png)

      * ********
      ******************** ******

      ![Bild](images/atomic-security.png)

   * **** It is a required state. This state must have following four user actions defined:

      * Action that changes the state of document to Adobe Sign Cancelled state. The name of this user action must be the same for all document types no matter what lifecycle is.
      * Action that changes the state of document to In Adobe Signing state. The name of this user action must be the same for all document types no matter what lifecycle is.
      * Action that calls the Web Action ‘Adobe Sign’
      * Action that calls the Web Action ‘Cancel Adobe Sign’. This state must have security that allowsAdobe Sign Admin role to: view document, view content, edit fields, edit relationships, download source, manage viewable rendition, and change state.

      ![](images/lifecycle-state3.png)

      * ******
      ******************** ******

      ![Bild](images/adobe-sing-authoring.png)

   * **** It is a required state. This state must have following five user actions defined:

      * Action that changes the state of document to Adobe Sign Cancelled state. The target state of this action can be whatever customer requirement is and it can be different for different types. The name of this user action must be the same for all document types no matter what lifecycle is.
      * Action that changes the state of document to Adobe Sign Rejected state. The target state of this action can be whatever customer requirement is and it can be different for different types. The name of this user action must be the same for all document types no matter what lifecycle is.
      * Action that changes the state of document to Adobe Signed state. The target state of this action can be whatever customer requirement is and it can be different for different types. However, the name of this user action must be the same for all document types no matter what lifecycle is.
      * **
      * ** This state must have security that allowsAdobe Sign Admin role to: view document, view content, edit fields, edit relationships, download source, manage viewable rendition, and change state.

      ![](images/lifecycle-state4.png)

      * ********
      ******************** ******

      ![Bild](images/in-adobe-signing-2.png)

      * **** It is a required state and it can be an existing lifecycle state, like Approved.
This state does not require user actions. It must have security that allows Adobe Sign Admin role to: view documents, view content, and edit fields.

   Following diagram illustrates the mappings between Adobe Acrobat Sign agreement and Vault document states, where the ‘Before Adobe Signature’ state is Draft.

   ![Bild](images/sign-vault-mappings.png)

### Schritt 11. Add Adobe Sign stage to General Lifecycle in Lifecycle Stage groups

![Bild](images/add-adobe-sign-stage.png)

### Schritt 12. Set permissions for User Role in Lifecycle state

You must set appropriate permissions for each User Role in Lifecycle State, as shown in the image below.

![Bild](images/set-user-role-permissions.png)

### Schritt 13. Set up atomic security based on the document state and the user role

![Bild](images/set-atomic-security.png)

### Schritt 14. Create Document messages for Adobe Sign Cancel

![Bild](images/create-cancel-message.png)

## [!DNL Veeva Vault] {#connect-middleware}

[!DNL Veeva Vault] [!DNL Veeva Vault][!DNL Veeva Vault]
[!DNL Veeva Vault]`adobe.for.veeva@xyz.com``bob.smith@xyz.com`

[!DNL Veeva Vault]

1. [ [!DNL Veeva Vault] ](https://static.adobesigncdn.com/veevavaultintsvc/index.html)
1. ****

   ![](images/middleware_login.png)

1. ****

   ![Bild](images/middleware-signin.png)

   After successful signing in, the page displays the associated email id and a Settings tab, as shown below.

   ![Bild](images/middleware_settings.png)

1. ****

   **

   ![Bild](images/middleware_newconnection.png)

1. ****

1. [!DNL Veeva Vault]

   The Adobe Acrobat Sign Credentials are autopopulated from the initial Adobe Sign login.

   ![Bild](images/middleware_addconnection.png)

1. ****

   On successful validation, you see a &#39;User validated successfully&#39; notification, as shown below.

   ![Bild](images/middleware_validated.png)

1. ****

   ![Bild](images/middleware_group.png)

1. ****

   ![Bild](images/add-audit-report.png)

1. ****

   ********[!DNL Veeva Vault]

   ![Bild](images/allow-auto-provisioning.png)

1. ****

   ![Bild](images/edit-connection-dispplay-adobe-sign-rendition.png)

1. ****

   [!DNL Veeva Vault]

   ![Bild](images/middleware_setup.png)

