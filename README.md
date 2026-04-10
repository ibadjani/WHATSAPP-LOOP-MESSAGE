# 💬 WhatsApp Message Loop — Browser Console Script

> Send repeated messages on WhatsApp Web automatically using your browser console. No extensions, no downloads, no installs required.

---

## 🚀 Features

- ✅ Send any message multiple times automatically
- ✅ Works directly from browser console
- ✅ No external tools or extensions needed
- ✅ Customizable message and repeat count
- ✅ 1 second delay between messages to avoid ban
- ✅ Live progress shown in console
- ✅ Uses keyboard simulation — no button clicking required

---

## ⚠️ Disclaimer

> This script is for **educational and personal use only.**
> - Do **NOT** use this to spam or harass anyone.
> - Sending too many messages may result in your WhatsApp number being **temporarily or permanently banned.**
> - The developer is **not responsible** for any misuse or consequences.
> - Use responsibly and only with the consent of the recipient.

---

## 📋 Requirements

- A modern browser (Chrome or Edge recommended)
- WhatsApp Web: [https://web.whatsapp.com](https://web.whatsapp.com)
- A stable internet connection

---

## 🛠️ How To Use

### Step 1 — Open WhatsApp Web
Go to [https://web.whatsapp.com](https://web.whatsapp.com) and scan the QR code with your phone.

### Step 2 — Open a Chat
Click on the contact or group you want to send messages to. Make sure the chat is fully open on the right side.

### Step 3 — Click Inside the Message Box
Click once inside the message input box at the bottom so it is focused.

### Step 4 — Open Browser Console
Press `F12` on your keyboard, then click the **Console** tab.

### Step 5 — Paste the Code
Copy the script below and paste it into the console, then press **Enter**.

### Step 6 — Enter Your Message and Count
A popup will ask you to:
1. Type your message
2. Enter how many times to send it

### Step 7 — Done! ✅
Watch the console for live progress updates.

---

## 💻 The Script

```javascript
var message = prompt("Enter your message", "");
var counter = parseInt(prompt("How many times?", 100));
var sent = 0;

function sendMessage() {
  if (sent >= counter) {
    console.log("✅ Done! Total sent: " + sent);
    return;
  }

  var textbox = document.querySelector('[contenteditable="true"]');
  textbox.focus();

  // Paste message using execCommand
  document.execCommand('insertText', false, message);

  // Simulate pressing Enter key to send
  textbox.dispatchEvent(new KeyboardEvent('keydown', {
    bubbles: true, cancelable: true, keyCode: 13, key: 'Enter'
  }));

  sent++;
  console.log("✅ Sent: " + sent + "/" + counter);
  setTimeout(sendMessage, 1000);
}

sendMessage();
```

---

## 🔧 Troubleshooting

| Problem | Solution |
|---|---|
| `Cannot set properties of null` | Make sure a chat is open and message box is visible |
| `Send button not found` | Click inside the message box first, then run the script |
| Message types but doesn't send | Click inside the chat box before running |
| Script stops after 1 message | Refresh the page, reopen the chat and try again |
| WhatsApp UI changed | The `contenteditable` selector is universal and should always work |

---

## ⚙️ Customization

| Setting | How to Change |
|---|---|
| **Message** | Type it in the prompt when asked |
| **Repeat Count** | Enter any number in the second prompt |
| **Delay** | Change `1000` in `setTimeout(sendMessage, 1000)` — value is in milliseconds |

**Delay Guide:**
- `500` = 0.5 seconds (fast, higher ban risk)
- `1000` = 1 second (recommended)
- `2000` = 2 seconds (safe and slow)
- `5000` = 5 seconds (very safe)

---

## 📁 File Structure

```
whatsapp-loop/
│
├── README.md          ← You are here
└── script.js          ← The main console script
```

---

## 📜 How It Works

1. `prompt()` asks for your message and repeat count
2. `document.querySelector('[contenteditable="true"]')` finds the WhatsApp message input box
3. `document.execCommand('insertText')` types the message into the box
4. `KeyboardEvent` with `keyCode: 13` simulates pressing **Enter** to send
5. `setTimeout` waits 1 second before sending the next message
6. The function calls itself recursively until the counter reaches zero

---

## 🙋 FAQ

**Q: Does this work on mobile?**
A: No. Browser console is only available on desktop browsers.

**Q: Will my account get banned?**
A: There is a risk if you send too many messages too fast. Keep the delay at 1000ms or higher.

**Q: Does it work on WhatsApp groups?**
A: Yes. Open the group chat and run the script the same way.

**Q: How do I stop the script mid-way?**
A: Type this in the console and press Enter:
```javascript
sent = counter;
```

---

## 👨‍💻 Author

**Ibad**
Student — Air University Islamabad, Faculty of Computing & AI

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

> ⭐ If this helped you, consider giving the repo a star!
