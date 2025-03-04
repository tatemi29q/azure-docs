---
title: 'Tutorial: Azure Active Directory integration with Reward Gateway | Microsoft Docs'
description: Learn how to configure single sign-on between Azure Active Directory and Reward Gateway.
services: active-directory
author: jeevansd
manager: CelesteDG
ms.reviewer: celested
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.topic: tutorial
ms.date: 08/31/2021
ms.author: jeedes
---
# Tutorial: Azure Active Directory integration with Reward Gateway

In this tutorial, you'll learn how to integrate Reward Gateway with Azure Active Directory (Azure AD). When you integrate Reward Gateway with Azure AD, you can:

* Control in Azure AD who has access to Reward Gateway.
* Enable your users to be automatically signed-in to Reward Gateway with their Azure AD accounts.
* Manage your accounts in one central location - the Azure portal.

## Prerequisites

To configure Azure AD integration with Reward Gateway, you need the following items:

* An Azure AD subscription. If you don't have an Azure AD environment, you can get a [free account](https://azure.microsoft.com/free/).
* Reward Gateway single sign-on enabled subscription.

## Scenario description

In this tutorial, you configure and test Azure AD single sign-on in a test environment.

* Reward Gateway supports **IDP** initiated SSO.

* Reward Gateway supports [Automated user provisioning](reward-gateway-provisioning-tutorial.md).

## Add Reward Gateway from the gallery

To configure the integration of Reward Gateway into Azure AD, you need to add Reward Gateway from the gallery to your list of managed SaaS apps.

1. Sign in to the Azure portal using either a work or school account, or a personal Microsoft account.
1. On the left navigation pane, select the **Azure Active Directory** service.
1. Navigate to **Enterprise Applications** and then select **All Applications**.
1. To add new application, select **New application**.
1. In the **Add from the gallery** section, type **Reward Gateway** in the search box.
1. Select **Reward Gateway** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

## Configure and test Azure AD SSO for Reward Gateway

Configure and test Azure AD SSO with Reward Gateway using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between an Azure AD user and the related user in Reward Gateway.

To configure and test Azure AD SSO with Reward Gateway, perform the following steps:

1. **[Configure Azure AD SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **[Create an Azure AD test user](#create-an-azure-ad-test-user)** - to test Azure AD single sign-on with B.Simon.
    1. **[Assign the Azure AD test user](#assign-the-azure-ad-test-user)** - to enable B.Simon to use Azure AD single sign-on.
1. **[Configure Reward Gateway SSO](#configure-reward-gateway-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Reward Gateway test user](#create-reward-gateway-test-user)** - to have a counterpart of B.Simon in Reward Gateway that is linked to the Azure AD representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Azure AD SSO

Follow these steps to enable Azure AD SSO in the Azure portal.

1. In the Azure portal, on the **Reward Gateway** application integration page, find the **Manage** section and select **single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, click the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

4. On the **Set up Single Sign-On with SAML** page, perform the following steps:

    a. In the **Identifier** text box, type a URL using one of the following patterns:

    | Identifier URL |
    |---|
    | `https://<COMPANY_NAME>.rewardgateway.com` |
    | `https://<COMPANY_NAME>.rewardgateway.co.uk/` |
    | `https://<COMPANY_NAME>.rewardgateway.co.nz/` |
    | `https://<COMPANY_NAME>.rewardgateway.com.au/`|
    |

    b. In the **Reply URL** text box, type a URL using one of the following patterns:

    | Reply URL |
    |---|
    | `https://<COMPANY_NAME>.rewardgateway.com/Authentication/EndLogin?idp=<Unique Id>` |
    | `https://<COMPANY_NAME>.rewardgateway.co.uk/Authentication/EndLogin?idp=<Unique Id>` |
    | `https://<COMPANY_NAME>.rewardgateway.co.nz/Authentication/EndLogin?idp=<Unique Id>` |
    | `https://<COMPANY_NAME>.rewardgateway.com.au/Authentication/EndLogin?idp=<Unique Id>` |
    |

	> [!NOTE]
	> These values are not real. Update these values with the actual Identifier and Reply URL. To get these values start setting up an Integration on the Reward Manager Portal. Details can be found on https://success.rewardgateway.com/hc/en-us/articles/360038650573-Microsoft-Azure-for-Authentication

5. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, click **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

	![The Certificate download link](common/metadataxml.png)

6. On the **Set up Reward Gateway** section, copy the appropriate URL(s) as per your requirement.

	![Copy configuration URLs](common/copy-configuration-urls.png)

### Create an Azure AD test user

In this section, you'll create a test user in the Azure portal called B.Simon.

1. From the left pane in the Azure portal, select **Azure Active Directory**, select **Users**, and then select **All users**.
1. Select **New user** at the top of the screen.
1. In the **User** properties, follow these steps:
   1. In the **Name** field, enter `B.Simon`.  
   1. In the **User name** field, enter the username@companydomain.extension. For example, `B.Simon@contoso.com`.
   1. Select the **Show password** check box, and then write down the value that's displayed in the **Password** box.
   1. Click **Create**.

### Assign the Azure AD test user

In this section, you'll enable B.Simon to use Azure single sign-on by granting access to Reward Gateway.

1. In the Azure portal, select **Enterprise Applications**, and then select **All applications**.
1. In the applications list, select **Reward Gateway**.
1. In the app's overview page, find the **Manage** section and select **Users and groups**.
1. Select **Add user**, then select **Users and groups** in the **Add Assignment** dialog.
1. In the **Users and groups** dialog, select **B.Simon** from the Users list, then click the **Select** button at the bottom of the screen.
1. If you are expecting a role to be assigned to the users, you can select it from the **Select a role** dropdown. If no role has been set up for this app, you see "Default Access" role selected.
1. In the **Add Assignment** dialog, click the **Assign** button.

## Configure Reward Gateway SSO

To configure single sign-on on **Reward Gateway** side, start setting up an Integration on the Reward Manager Portal. Use the downloaded metadata to obtain your Signing Certificate and upload that during the configuration. Details can be found on https://success.rewardgateway.com/hc/en-us/articles/360038650573-Microsoft-Azure-for-Authentication.

### Create Reward Gateway test user

In this section, you create a user called Britta Simon in Reward Gateway. Work with [Reward Gateway support team](mailto:clientsupport@rewardgateway.com) to add the users in the Reward Gateway platform. Users must be created and activated before you use single sign-on.

Reward Gateway also supports automatic user provisioning, you can find more details [here](./reward-gateway-provisioning-tutorial.md) on how to configure automatic user provisioning.

## Test SSO

In this section, you test your Azure AD single sign-on configuration with following options.

* Click on Test this application in Azure portal and you should be automatically signed in to the Reward Gateway for which you set up the SSO.

* You can use Microsoft My Apps. When you click the Reward Gateway tile in the My Apps, you should be automatically signed in to the Reward Gateway for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Next steps

Once you configure Reward Gateway you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](/cloud-app-security/proxy-deployment-aad).