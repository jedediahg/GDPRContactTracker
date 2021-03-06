# GDPR Contact Tracker
This is a simple design for a Contact Tracing app that can be implemented very simply and that fully respects privacy.
In short the design accomplishes a private contact tracking that exposes data only on a need-to-know basis and with consent of the user.
* Privacy is respected. The Authority does not have access to the data at any time and can't see any of the tracking information.
* Data is decentralized. Each user stores their contact histrory locally on their device. This data is encrypted using a public key from an assymetric encryption keypair, e.g. RSA. Contact information should only be the device push address for sending notification of a hot contact.
* Contacts are anonymous. The owner of the device does not have the private key and can not access to the information of the people with whom they have come into contact. 
* The private key is held by the Authority, who never has access to the encrypted data.
* Individuals give consent. When a person becomes sick, they notify the Authority through the app. They then give their encrypted contact history to the Medical Team. 
* The Medical Team requests the private key from the Authority, who release based on the sickness notification from the user (or the death certificate of the user, as the case may be). 
* The Medical Team can decrypt the contact history and notify the individuals in the list.

The only people that get to see the personal details in the contact history are the medical team. They can only decrypt this after the holder of the data has given consent to the Authority (sickness notification) and the Authority has given the Medical Team the private key.

The contact notification does not need to tell the recipient with whom they came into contact that was infected. Users of the application remain anonymous to each other.

The contact tracking information can even be limited to the device GUID so that notification can be done via push message to the concerned app users. With this method, it is possible to have the app never expose personal information to anyone, not even the Medical Team.

If one would like to ensure that the private key can't be released to the Medical Team without the explicit consent of the User, then the setup requires a couple more steps: Authority encrypts private key with its own symmetric encryption.  Authority sends private key to the User. User encrypts (wraps) the encrypted private key with its own symmetric encryption. User sends the locked key to Authority. Only when the user gives the Sickness Notification to the Authority do they provide the symmetric key to unlock the private key.

In the sequence diagram below, Bob is already a registered user of the app.

The file sequencediagram.org.txt can be used to edit the sequence diagram on https://sequencediagram.org/

A note on contact tracing apps: 

I am not an advocate of contact tracing apps. They are significant threats to human rights. They are also of questionable value in actual contact tracing. I, and many other people, refrain from taking mobile devices into potential high-contact zones, i.e. super markets, medical facilities, post offices, etc. This means that the most likely contacts will not be traceable.

A smart phone is a device that you touch often and that touches your face often. Rather than involve this device in a higher risk situaion, I advise to leave your phone in the vehicle or home when making errands to high density locations. Always wash/disinfect your hands before touching the phone after such activity.

![Sequence Diagram](images/sequence_grouped.PNG)
