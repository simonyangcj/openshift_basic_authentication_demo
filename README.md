#openshift base authentication demo 

----
a demo project from those of you want to implement openshift basic authentication
----


how to play
==================================

----

* First you should know how openshift working with different [authentication] method
* Then you should run you openshift-kube-apiserver with ``master-config.yaml`` with base authentication enabled. It looks like below:
    ```
    oauthConfig:
    ...
    identityProviders:
      - name: my_remote_basic_auth_provider
        challenge: true
        login: true
        provider:
          apiVersion: v1
          kind: BasicAuthPasswordIdentityProvider
          url: https://localhost:9443/99cloud/authentication_service/1.0.0/login
          ca: /etc/origin/master/delegate_ca.crt
          certFile: /etc/origin/master/admin.crt
          keyFile: /etc/origin/master/admin.key
    ```
* Normally you will run you cluster with container so ensure you mapping ``credential`` folder to ``/etc/origin/master`` or just copy the ``ca.crt`` , ``admin.crt`` , ``admin.key`` to the mapping folder
* We you copy those file remember to rename ``credential/ca.crt`` to ``delegate_ca.crt`` because the mapping folder may contains cluster ca certs
* Build it with command ``go build .``
* Run ``./openshift_basic_authentication_demo`` to start server 
* The server is liscening on the port 9443. Feel free to modify it.
* Once you done all above steps. Open you browser and visit openshift web-console and login with username ``simon`` and password ``123456``


----

[Simon Yang]

[authentication]: https://docs.openshift.com/enterprise/3.0/admin_guide/configuring_authentication.html#BasicAuthPasswordIdentityProvider
[Simon Yang]: simonycj@gmail.com