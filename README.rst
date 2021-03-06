==========================
Django Social Registration
==========================

Django Social Registration enables developers to add alternative registration
methods based on third party sites.

Requirements
============
django
oauth
python-openid
pyfacebook

Installation
============

#. Add the ``socialregistration`` directory to your ``PYTHON_PATH``.
#. Add ``socialregistration`` to your ``INSTALLED_APPS`` settings of Django.
#. Add ``socialregistration.urls`` to your ``urls.py`` file.

Configuration
=============

Facebook Graph API Connect
----------------
#.  The previous connect will be deprecated in further releases for now it's still available.
#.  This new version will support desktop as well as mobile. Use ``FACEBOOK_DISPLAY`` in your settings file to serve the different platforms. Possibilities: (``touch``, ``wap``, default: ``popup``)
#.  Add ``FACEBOOK_APP_ID`` and ``FACEBOOK_SECRET_KEY`` to your settings file representing the app id and the secret key you were given by Facebook.
#.  Add ``socialregistration.auth.FacebookAuth`` to ``AUTHENTICATION_BACKENDS`` in your settings file.
#.  Add tags to your template file::

	{% load facebook_tags %} 
 	{% facebook_button %}

Twitter
-------
#. Add the following variables to your ``settings.py`` file with the values you were given by Twitter::

    TWITTER_CONSUMER_KEY
    TWITTER_CONSUMER_SECRET_KEY
    TWITTER_REQUEST_TOKEN_URL
    TWITTER_ACCESS_TOKEN_URL
    TWITTER_AUTHORIZATION_URL

#. Add ``socialregistration.auth.TwitterAuth`` to ``AUTHENTICATION_BACKENDS`` in your settings file.

#. Add tags to your template file::

    {% load twitter_tags %}
    {% twitter_button %}

LinkedIn
-------
#. Add the following variables to your ``settings.py`` file with the values you were given by LinkedIn::

    LINKEDIN_CONSUMER_KEY
    LINKEDIN_CONSUMER_SECRET_KEY
    LINKEDIN_REQUEST_TOKEN_URL
    LINKEDIN_ACCESS_TOKEN_URL
    LINKEDIN_AUTHORIZATION_URL

#. Add ``socialregistration.auth.LinkedinAuth`` to ``AUTHENTICATION_BACKENDS`` in your settings file.

#. Add tags to your template file::

    {% load linkedin_tags %}
    {% linkedin_button %}

Other OAuth Services
--------------------
There is an example of how FriendFeed integration could work.
``socialregistration.models`` provides a ``FriendFeedProfile`` model to save account
data, ``socialregistration.auth`` provides examples for different auth backends for
different service providers, ``socialregistration.utils`` provides a Twitter
and FriendFeed interface and ``socialregistration.urls`` provides examples based
on Twitter and FriendFeed how to hook in more OAuth based services.

OpenID
------
#. Add ``socialregistration.auth.OpenIDAuth`` to ``AUTHENTICATION_BACKENDS`` in your settings file.
#. Add tags to your template file::

    {% load openid_tags %}
    {% openid_form %}

Logging users out
-----------------
You can use the standard {% url auth_logout %} url to log users out of Django.
Please note that this will not log users out of third party sites though.
When using Facebook Connect, it is recommended to follow the FBConnect developer
wiki. See: http://wiki.developers.facebook.com/index.php/Connect/Authorization_Websites#Logging_Out_Users ::

    <a href="#" onclick="FB.Connect.logoutAndRedirect('{% url auth_logout %}')">Logout</a>

HTTPS
-----
If you wish everything to go through HTTPS, set ``SOCIALREGISTRATION_USE_HTTPS`` in your settings file to
``True``

Other Information
-----------------
If you don't wish your users to be redirected to the setup view to create a username but rather have
a username generated for them, set ``SOCIALREGISTRATION_GENERATE_USERNAME`` in your settings file to ``True``
