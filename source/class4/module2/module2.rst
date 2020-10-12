Test your deployment with MFA enabled
#####################################

.. warning :: You should have received an email or teams chat from yoru SA/SME to continue.

#. Close any opened browser and re-open ``Microsoft Edge``
#. Connect to ``Bluesky``. Don't try with ``Vanilla`` as your MFA test account does not exist in on-prem AAD. Thus, The SSo will not work. You can add this user in ADDS if you are familar with AD.
#. If you are not prompted, open an ``incognito window``. It means you still have Azure AD cookies.
#. At prompt, login with your MFA account. In my case, ``matt@f5access.onmicrosoft.com`` and the password provided by your SA/SME
#. You will be asked to enroll an MFA method

   .. image:: ../pictures/module2/moreinfo.png
      :align: center

#. Click ``Next``
#. You have the choice to use the ``Microsoft Authenticator`` mobile app, or use SMS. Make your choice and follow the step to enroll your device (or phone number)

   .. image:: ../pictures/module2/choice.png
      :align: center

#. I select the mobile app, scan the QR code, and approve the push notification on my mobile phone.
#. I click ``Next`` and ``Done``

   .. image:: ../pictures/module2/done.png
      :align: center

#. Azure AD asks you to change your password set by your SA/SME.

#. You can notice **it does not work**. The user has to be assigned with the ``Bluesky`` app.

   .. image:: ../pictures/module2/error.png
      :align: center

#. In the BIG-IP, edit the ``ISS-Bluesky-<my name>`` template, and in ``Azure Active Directory`` step, add your account.

   .. image:: ../pictures/module2/account.png
      :align: center

#. Click ``Save and Next`` and ``Deploy``

   .. image:: ../pictures/module2/deploy.png
      :align: center

#. Make a new test, approve the ``push notification`` or enter the ``OTP`` received by SMS.

.. note :: This lab is not **Azure AD Conditional Access**. This is just **user MFA**. Conditional Access is similar but it is tied to a policy (group, location, app ...). In this lab, matt will be prompt for MFA whatever the apps he connects to.
