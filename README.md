# Nostr Static Contact Form

The **Nostr Static Contact Form** is an embeddable, static contact form that securely sends messages using the decentralized Nostr protocol. Each submission generates an ephemeral Nostr account, encrypts your message using NIP‑04, and publishes the event to a relay network. This form is ideal for any website that needs a simple, modern, mobile‑friendly contact solution without relying on centralized servers.

## What is Nostr?

[Nostr](https://github.com/nostr-protocol/nostr) (Notes and Other Stuff Transmitted by Relays) is an open, decentralized protocol designed to create, sign, and publish content. Nostr is censorship-resistant and relies on a network of relays rather than a single central server. It is used for messaging and data publication while focusing on privacy and resilience.

## Features

- **Embeddable & Static:** A single HTML file that can be hosted on any static site.
- **Modern & Mobile-Friendly:** Responsive design with a clean, minimal interface.
- **Decentralized Messaging:** Publishes encrypted messages as Nostr events to multiple relays.
- **Ephemeral Security:** Generates a new ephemeral key pair for each submission.
- **Admin Configurable:** The recipient NPUB is set in the code so that all messages go directly to your account.
- **Simple Feedback:** After submission, users see only a "Success" or "Failed" message.

## How It Works

1. **User Submission:** The user fills out the basic contact fields (Name, Email, Message) and submits the form.
2. **Message Assembly:** The form data is compiled into a Markdown‑formatted message.
3. **Ephemeral Key Generation:** A new ephemeral key pair is generated for that submission.
4. **Encryption:** The message is encrypted using NIP‑04 with the admin’s NPUB.
5. **Event Publishing:** The encrypted message is packaged as a Nostr event (kind 4) and published to a set of relays.
6. **User Feedback:** The form displays a success or failure message depending on whether at least one relay accepted the event.

## How to Use

### 1. Configure the Recipient NPUB

Open the HTML file and locate the following line in the JavaScript section:

```js
const recipientNpub = "npubYOURADMINNPUBHERE"; // Replace with your NPUB
```

Replace `"npubYOURADMINNPUBHERE"` with your actual Nostr public key (NPUB). This key will be used to receive all messages submitted through the form.

### 2. Deploy the Form

Since the form is a single HTML file, you can host it on any static hosting provider such as GitHub Pages, Netlify, or Vercel.

### 3. Embedding as an iFrame

To use the contact form on another website, simply embed it within an `<iframe>`. For example:

```html
<iframe 
  src="https://yourdomain.com/path/to/nostr-static-contact-form.html" 
  style="width:100%; border:none; height:500px;">
</iframe>
```

Place this code on any page where you want the form to appear. Adjust the `height` and other styles as needed to fit your design.

### 4. Test It Out

Visit your deployed page (or the page containing the iframe) and submit a message. A success or failure message will display based on the relay response.

## Dependencies

- **Nostr Tools v2.10.4:**  
  The form relies on [nostr-tools](https://github.com/fiatjaf/nostr-tools) (loaded via CDN) for key generation, encryption, and event publishing.

## License

This project is open source and available under the [MIT License](LICENSE).

## Additional Resources

- [Nostr Protocol Documentation](https://github.com/nostr-protocol/nostr)
- [Nostr Tools GitHub Repository](https://github.com/fiatjaf/nostr-tools)
