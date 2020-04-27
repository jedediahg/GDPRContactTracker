# GDPR Contact Tracker
This is a simple design for a Contact Tracing app that can be implemented very simply and that fully respects privacy.
In short the design accomplishes a private contact tracking that exposes data only on a need-to-know basis and with consent of the user.
* The Authority does not have access to the data at any time and can't see any of the tracking information.
* Each user stores their contact histrory locally on their device. This data is encrypted using a public key from an assymetric encryption keypair, e.g. RSA.
* The owner of the device does not have the private key and can not access to the information of the people with whom they have come into contact. 
* The private key is held by the Authority, who never has access to the encrypted data.
* When a person becomes sick, they notify the Authority through the app. They then give their encrypted contact history to the Medical Team. 
* The Medical Team requests the private key from the Authority, who release based on the sickness notification from the user. 
* The Medical Team can decrypt the contact history and notify the individuals in the list.

The only people that get to see the personal details in the contact history are the medical team. They can only decrypt this after the holder of the data has given consent to the Authority (sickness notification) and the Authority has given the Medical Team the private key.

The contact notification does not need to tell the recipient with whom they came into contact that was infected. Users of the application remain anonymous to each other.

The contact tracking information can even be limited to the device GUID so that notification can be done via push message to the concerned app users. With this method, it is possible to have the app never expose personal information to anyone, not even the Medical Team.

In the sequence diagram below, Bob is already a registered user of the app.

The file sequencediagram.org.txt can be used to edit the sequence diagram on https://sequencediagram.org/

![Sequence Diagram](images/Sequence.PNG)
