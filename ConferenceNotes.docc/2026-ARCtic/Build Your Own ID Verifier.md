# Build Your Own (Pseudo) ID Verifier

@Metadata {
    @TitleHeading("Workshop")
}

Daiki Matsudate

## Abstract

Modern digital identity systems such as Apple Wallet and mdoc defined in ISO 18013-5/7, 23220 series use a powerful but approachable pattern: a verifier requests specific attributes, the holder responds with a signed document, and only the necessary information is revealed (for example, "21+ OK" instead of a full birth date).

In this hands-on workshop, we'll recreate a simplified version of that flow on iOS. Participants will build an app that can act as both a Holder and a Verifier. The Verifier initiates a session using a QR-based handshake, establishes a local connection over BLE / MultipeerConnectivity, sends a challenge and a list of requested attributes, and receives a signed "pseudo document" from the Holder. Using CryptoKit, we'll sign and verify the payload on-device and display only the approved attributes in the UI.

## Key Takeaways

-
