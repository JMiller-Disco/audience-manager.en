---
description: The options under the Administration menu let you create Audience Manager users and assign them to groups. You can also view limits (traits, segments, destinations, and models).
keywords: rbac;RBAC;role based;role-based;role-based access controls
seo-description: The options under the Administration menu let you create Audience Manager users and assign them to groups. You can also view limits (traits, segments, destinations, and models).
seo-title: Administration
solution: Audience Manager
title: Administration
topic: DIL API
uuid: 498e0316-cf1b-43e9-88ba-338ee0daf225
---

# Administration (RBAC Controls) {#administration}

![](assets/rbac-controls.png) 

The options under the [!UICONTROL Administration] menu let you create Audience Manager users and assign them to groups. You can also view limits (traits, segments, destinations, and models).

Enterprise customers using [!DNL Audience Manager] need one data management platform for all of their data, but must be able to control the visibility of the different data elements to specific business units. You can accomplish this using group permissions, also referred to as [!UICONTROL Role-Based Access Control] ([!UICONTROL RBAC]).

[!DNL Audience Manager] uses groups to assign permissions. Permissions are not assigned at the user level. Group permissions are tied to objects (traits, segments, etc.) and to actions you can perform on those objects (edit, view, etc.). These controls are also available through the Audience Manager REST APIs. See [User Management](/help/using/api/rest-api-main/aam-api-user-group-permission/aam-api-user.md), [Group Management](/help/using/api/rest-api-main/aam-api-user-group-permission/aam-api-group.md), and [Permissions Management](/help/using/api/rest-api-main/aam-api-user-group-permission/aam-api-permissions.md) API methods.

## Create Users {#create-users}

<!-- t_create_users.xml -->

Create users in [!DNL Audience Manager] and specify user details, login status, and assign users to groups.

1. Click **[!UICONTROL Administration]** > **[!UICONTROL Users]**.
1. Click ![](assets/icon_add.png) to display the [!UICONTROL Create New User] page.
1. Under **[!UICONTROL User Details]**, fill in the fields:
   * **Username:** Specify a unique username for Audience Manager.
   * **First Name:** Specify the user's first name.
   * **Last Name:** Specify the user's last name.
   * **Email Address:** Specify the user's email address. [!DNL Audience Manager] does not send regular notification to users. [!DNL Audience Manager] administrators have access to users' email addresses and can manually email users as needed. For example, if a user forgets his or her password, the email address specified in this field is used to send a temporary password and instructions to reset the password.
   * **Phone Number:** Specify the user's phone number.
   * **Is Admin:** Specify if this user is an [!DNL Audience Manager] administrator. Admin users can manage users (create, edit, etc.) and groups (create, assign permissions, etc.). Non-admin users can control only their own user profiles, including editing their email addresses and resetting their own passwords. For more information, see [Edit Your Account Settings](../../features/administration/edit-account-settings.md).
1. Under **[!UICONTROL Login]**, select the desired status:
   * **Active:**  Active users can access [!DNL Audience Manager] and have the permissions granted by group membership.
   * **Deactivated:**  Deactivated users cannot access [!DNL Audience Manager] and do not have any permissions. If you deactivate users, their user information remains in [!DNL Audience Manager] and you can simple reactivate them, if necessary. If you remove users, you must re-create them if they need to use [!DNL Audience Manager] again in the future.
   * **Expired:** A user's password is older than 90 days.
   * **Pending:** The user has a temporary password, either as after a password reset or as a brand new account, and they have not yet set a permanent password.
   * **Locked Out:** 5 incorrect login attempts will lock out a user.
1. Under **[!UICONTROL Assigned Groups]**, from the drop-down list, select the desired groups to which you want to assign this user.
  For more information about groups and permissions, see [Create a Group](../../features/administration/administration-overview.md#create-group).
1. Click **[!UICONTROL Save]**.

## Create a Group {#create-group} 

A *group* is a collection of users that share access rights to destination, segment, and trait objects. You can limit groups to single objects only or give them broad access to combinations of different objects.

<!-- t_create_groups.xml -->

To create a group:

1. Click **[!UICONTROL Administration]** > **[!UICONTROL Groups]**.
1. Click  ![](assets/icon_add.png) to open the [!UICONTROL Group Settings] page.
1. In [!UICONTROL Group Details]:
   * Name the group.
   * Provide a brief group description.
1. In [!UICONTROL Group Members], click a user from **[!UICONTROL Add Users]** options to add them to the group.
1. In [!UICONTROL Group Permissions], select a [trait](../../features/traits/trait-details-page.md), [segment](../../features/segments/segments-purpose.md), or [destination](../../features/destinations/destinations.md) from **[!UICONTROL Add Object]**.
   This opens a permissions window for your selected object.
1. Select the check box for the permissions you want group members to have.
1. *(Optional)* Assign [Wild Card Permissions](../../features/administration/administration-overview.md#wild-card-permissions) to the group.
1. Click **[!UICONTROL Save Group]**.

## Understanding Wild Card Permissions {#wild-card-permissions}

Simplify group rights management with [!UICONTROL Wild Card Permissions].

<!-- c_wildcard_permissions.xml -->

[!UICONTROL Wild Card Permissions] give group members automatic access to each data source associated to a segment, destination, or trait. By comparison, regular permissions only let you assign specific data sources to the one of these objects. And, when you add new data sources, group members don't get access to those new sources.

You have to open the group permissions and assign those new data sources to the group. [!UICONTROL Wild Card Permissions] let you avoid this manual data source update process. Groups with [!UICONTROL Wild Card Permissions] get access to new data sources without explicit authorization.

![](assets/wild-card.png) 

Read below for a description of what each wildcard permission means:

**Trait**

* `MAP_ALL_TRAITS_TO_MODELS` - Users can select traits as the baseline for models.
* `EDIT_ALL_TRAITS` - Users can edit all traits set up within their company account.
* `VIEW_ALL_TRAITS` - Users can view all traits set up within their company account.
* `DELETE_ALL_TRAITS` - Users can delete all traits set up within their company account.
* `CREATE_ALL_ALGO_TRAITS` - Users can create algorithmic traits.
* `MAP_ALL_TO_SEGMENTS` - Users can add any of the traits belonging to their company to segments.
* `CREATE_ALL_TRAITS` - Users can create traits.

**Reports**

* `PTRREPORTS` - This wildcard permission refers to outdated functionality and will be removed from the Audience Manager UI shortly.

**Models**

* `VIEW_MODELS` - Users have permission to view models belonging to their company.

**Derived Signals**

* `VIEW_DERIVED_SIGNALS` - Users can view all the derived signals belonging to their company.
* `CREATE_DERIVED_SIGNALS` - Users can create derived signals.
* `EDIT_DERIVED_SIGNALS` - Users can edit all the derived signals belonging to their company.
* `DELETE_DERIVED_SIGNALS` - Users can delete any of the derived signals belonging to their company.

**Destination**

* `EDIT_ALL_DESTINATIONS` - Users can edit all the destination set up within their company account.
* `CREATE_DESTINATIONS` - Users can create destinations.
* `VIEW_ALL_DESTINATIONS` - Users can view all the destinations set up within their company account.
* `DELETE_ALL_DESTINATIONS` - Users can delete all the destinations set up within their company account.

**Tags**

* `VIEW_TAGS` - Users can do everything (view, create, edit, delete) on their Tag Containers.

**Audience Lab**

* `MANAGE_SEGMENT_TEST_GROUPS` - Users can do everything (view, create, edit, delete) on their Audience Lab test groups.

**Segment**

* `CREATE_ALL_SEGMENTS` - Users can create segments.
* `DELETE_ALL_SEGMENTS` - Users can delete all the segments set up within their company account.
* `MAP_ALL_TO_DESTINATIONS` - Users can map any of the segments belonging to their company to destinations.
* `EDIT_ALL_SEGMENTS` - Users can edit all the segments set up within their company account.
* `MAP_ALL_SEGMENTS_TO_MODELS` - Users can select segments as the baseline for models.
* `VIEW_ALL_SEGMENTS` - Users can view all the segments set up within their company account.

**Signals**

* `VIEW_ALL_SIGNALS` - Users can view all signals captured in [Data Explorer](/help/using/features/data-explorer/data-explorer-overview.md).