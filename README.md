# seedpage -- A seedtool that runs in the browser.

Hello everybody out there using seedtool!

Since I've discovered Blockchain Commons and its projects like ByteWords,
seedtool, UR, and SSKR, I've been fascinated by the clarity and simplicity of
the ideas. These are tools that I've long wanted to have. Seedtool in
particular would be fantastic to safely generate secret key shares, if only I
could be confident about running it securely.

What I want is a seedtool that anyone can easily run on an airgapped device.
That is why I am proposing to **build a seedtool that runs in a standalone
HTML/JavaScript page** in a web browser. This means that any cheap old
smartphone or laptop can be used to run it, without any prerequisites and
without having to compile anything. I am looking for motivated contributors who
want to help me in this endeavor.

### The principles of this project

* Build a single-page app that can be run in any browser.
* It works completely offline. It can be run in an incognito window, with all
  traces deleted once the window is closed.
* Core features:
    * Generate seeds
    * Generate seed shares and show them as ByteWords, URs, or QR codes
    * Show seed as BIP-39 so it can be imported in a wallet
    * Reconstruct a seed from shares (This is a bit secondary, but I would like
      users to only need one single tool for handling their seeds)
* Security is paramount:
    * Code should be very readable, easy to inspect, with few dependencies
    * The page can warn the user if the device is not in airplane mode (by
      trying a network request) or not in incognito mode (by looking for old
      previously-stored cookies)
    * The page can include clear and simple instructions for users, e.g., what
      to do with their shares.

Besides the Blockchain Commons projects, another source of inspiration for this
is https://github.com/iancoleman/bip39 -- That tool handles the mnemonic ->
address conversion, whereas my proposed seedtool would handle seed -> mnemonic
and seed <-> shares.
