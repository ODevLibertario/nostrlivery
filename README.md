# Nostrlivery

![logo](./nostrlivery_logo.svg)

Decentralized delivery application that uses Nostr and Bitcoin

**Three mobile apps:**
- **Company - https://github.com/ODevLibertario/nostrlivery-company**
- **Driver - Not started**
- **Consumer - Not started**

**A nostr relay as backend - https://github.com/ODevLibertario/nostrlivery-node**

The backend is a special nostr relay that knows how to speak the apps protocol. Should be able to be plugged in to any nostr relay. Initially there will be one dedicated relay for reference.

**The company app allows for:**
- Choice of nostrlivery node
- Login
- Registration of a new company
- Associating with drivers to the company
- Removing drivers from company
- Receiving orders
- Checking delivery history

**The driver app allows for:**
- Choice of nostrlivery node
- Login
- Registration
- Accepting associations to companies
- Setting the price of your service by km or other parameters
- Receiving delivery orders
- Routing delivery orders
- Rating clients
- Checking delivery history

**The consumer app allows for:**
- Choice of nostrlivery node
- Login
- Registration 
- Browsing near companies
- Searching company by npub
- Making order
- Rating company 
- Rating driver

**The backend node:**
- Manages nostr event communication with the nostr network
- Stores data as nostr events
- Serves as a payment mediator during an order
- The node is not a nostr relay, it is a nostr entity with nsec and npub that talks to nostr relays

**How does payment work:**

The consumer picks their order and based on the distance from the company receives an invoice to pay.

When he pays the invoice, the money gets stored into the node's wallet and it behaves like an htlc that splits the payment into two branches, the first splits the payment into three parts: the payment for the company, the payment to the driver, and the payment to the node, but that path is only unlocked if given a passcode that the client has and will only give once he received the goods. Once given the passcode, the node will zap the company and the driver their sats and keep a small percentage to cover computing costs.

The second path is a timelock that returns the full amount of money to the client as a fallback after a set amount of time if the delivery didn't happen.

**Benefits:**
- No centralized middle man, you need a relay but there could be many.
- Much lower fees, today delivery apps take something like 30%. Free market would define fees here but I imagine they will be much lower.
- Can't be censored.
- Can't be taxed.

**Problems:**
- You need to trust the store you are buying from since their reputation is on the line, so small unknown stores would very hardly be trusted.
- There are many possible attack vectors here to spam the system, and bot reviews but we can add rules to the system to avoid most of these.

**How to contribute**
- Join the telegram group: [https://t.me/+qgoN80-CulQyNGYx](https://t.me/+qgoN80-CulQyNGYx)
- Ask @odevlibertario to join the repo you want to contribute on
- Check the [Tasks](./Tasks.md) for pending tasks you can start
- Open a pull request to master with your code, refer to which task you are implementing

**How to contribute financially**
- Make a donation to @odevlibertario at: freshdriver32@walletofsatoshi.com
- The money will used to support the developers of the project and offer bounties
