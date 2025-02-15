# Telecom - Media and Switching

### Key concepts:

* Transmitter: Converts Info → signal for transmission
* Transmission Medium: Carries signal - Transmitter → Receiver
* Receiver: Converts signal → Info

### Guided and Unguided Media

#### _Guided Media_

> _“Wired or bounded transmission, idea for speed, security and small distance”_

* Tisted Pair, coaxial Cable, Fiber Optic

#### Unguided Media

> “Wireless Transmissions who broadcast signals through air used for long-distance”

* Infrared, Microwaves, Radio Waves

### Channels

#### Communication channels:

* Simplex (keyboard/TV/Monitor), Half-duplex (Talkie-walkie), Full duplex (phones)

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

### Switching

*   Store-and-Forward Switching

    This method involves receiving the entire frame before forwarding it. The switch checks for errors and only forwards error-free frames. While this ensures data integrity, it can introduce slight delays.
*   Cut-through Switching

    This technique begins forwarding the frame as soon as the destination address is read. It's faster than store-and-forward but doesn't check for errors, potentially propagating corrupted data.

FCS: Frame Check Sequence

> _“Contains checksum, a value calculated using Cyclic Redundancy Check (CRC)”_
