## Usage and Examples

Seedpage is a tool to securely generate cryptographic seeds, that is, pieces of
data that have high entropy and are impossible for an adversary to guess. These
seeds are often used to derive cryptocurrency wallets, but can also serve as
keys for encrypted communication, or as basis for a digital identity.

It is important to use seedpage correctly, otherwise the keys might be leaked,
guessed, or stolen. These principles are important:

- Use seedpage in a trusted environment. For example a freshly factory-reset,
  malware-free smartphone. You can further protect yourself by putting the
  device in aeroplane mode.
- Keep the generated seeds safe. You could store them in a hardware wallet or
  write them on a piece of paper that you store in a secure place.
- Do not share your keys with anyone.
- After you have safely stored your keys, delete all traces. We recommend
  running seedpage in an incognito window that is closed when done, and
  performing a factory reset of the device after using seedpage.

### Entropy

The output of seedpage is based on the entropy field (labeled
`--deterministic`). It is paramount that nobody can guess the content of this
field. By default, seedpage fills it with 32 bytes of data from a
cryptographically secure random number generator.

### Seedtool arguments

Seedpage is based on
[seedtool](https://github.com/BlockchainCommons/seedtool-cli). The "seedtool
arguments" field enables you to pass arbitrary arguments to seedtool. Here are a
few possible use cases:

**Generate a bip39 seed to initialize a hardware cryptocurrency wallet:** In
this case, you leave the arguments empty, and use the output in the `bip39`
field.

**Split a seed into multiple shares for secure, distributed backups:** Configure
the number of shares with a `--group` argument, for example
[`--group=3-of-7`][sskr-example]. Seedtool then generates seven shares. These
are displayed in the `sskr` field and also as QR codes. Any three of the shares
allow you to reconstruct the seed.

In this mode, you would use the seed (for example, enter the bip39 version into
a hardware wallet) and distribute the shares. For example, you could write them
on pieces of paper and send each piece to a trusted friend or family member.
After something bad happens (say, a flood destroys your hardware wallet) you can
seek any three of the friends, gather their shares, and reconstruct the seed.

Note that it is insecure to distribute the shares via email or similar
mechanisms. Any adversary with access to your email account could find three
emails in the "sent" folder, and use these to reconstruct the secret seed.
Instead, use an electronic device only to run seedpage, and use paper or trusted
hardware wallets for anything else.

[sskr-example]: javascript:setSeedtoolArguments('--group=3-of-7')