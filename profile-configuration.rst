Profile configuration tutorial
==============================

Configuration
-------------

If you are using the provided docker container, all configuration explained on
this document has already been done on the container.

This document list the steps taken to configure EJBCA.

Misconfiguring a Certificate authority can severely affect all systems that
rely on it for authentication purposes, leading to a swath of security
vulnerabilities being implicitly added to them. Please be extra careful when
dealing with this.

Pre Configuration
~~~~~~~~~~~~~~~~~

To configure EJBCA via the web interface, first you need to configure your
browser certificates.

Copy the client side certificate from your EJBCA instance, located on
'/p12/superadmin.p12' and '/p12/ca.crt' to your local machine.

The way trusted and client certificates are configured vary from browser to
browser. Please, check you favorite browser manual. Add 'ca.crt' to your
'Certificate Authorities' list. Add 'superadmin.p12' to 'personal certificates'
list. The password for the file is 'ejbca' (all lowercase, without quotes)

Now you can access the EJBCA Web service at hostname:8443/ejbca You may need to
authorize the site to use a personal certificate. Select the certificate
superadmin.p12.

Configuring EJBCA Profiles
~~~~~~~~~~~~~~~~~~~~~~~~~~

Follow the link for the administration menu. Click on 'Certificate Profiles'
Clone the ENDUSER default profile. Give the new profile the name CFREE. Click
the button edit on the new created profile.

Change the following fields: 

- Available bit lengths: deselect key lengths bellow 2048 bits
- Signature Algorithm: Sha256WithRSA
- Allow extension override: check
- Basic Constraints: unselect critical 
- Key Usage: unselect critical, select 'data encipherment' and 'Key agreement' 
- Extended Key Usage: unselect

Click 'save' at the bottom of the page to save editions.

Click on 'End Entity Profiles'. Create a new profile, called
'EMPTY\_CFREE' Edit the profile

-  Batch generation (clear text pwd storage)

   -  Select 'Use'

-  Subject Alternative Name

   -  Add DNS Name
   -  Add IP Address

-  Default Certificate Profile

   -  Select CFREE

-  Available Certificate Profiles

   -  Select CFREE

Click 'save' at the bottom of the page to save editions
