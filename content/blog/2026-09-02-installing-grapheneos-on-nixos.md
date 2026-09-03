+++
title = "Installing GrapheneOS on NixOS"
tags = ["GrapheneOS", "NixOS"]
+++

I recently bought a Google Pixel 10a and today I received it. I always wanted to
use GrapheneOS for various reasons I won't detail here, but never had a Pixel
phone to begin with. Now I can! Though with a small hickup: NixOS is not
officially supported by GrapheneOS, but it won't stop me to try anyway.

For reproducibility sake, I am on a NixOS generation which is built from this
commit: `ff0dd6dc3c0e0b480cc8546d3be080fc538f366a` of my versionned nix configs
which can be found either on [GitHub](https://github.com/ymelois/nixfiles/commit/ff0dd6dc3c0e0b480cc8546d3be080fc538f366a)
or [Tangled](https://tangled.org/youn.dev/nixfiles/commit/ff0dd6dc3c0e0b480cc8546d3be080fc538f366a).

To make the setup work through the web installer with WebUSB I had to add this
to my NixOS config:

```nix
environment.systemPackages = [
  pkgs.android-tools
];
```

And I used `pkgs.ungoogled-chromium` as Zen (Firefox fork) doesn't support WebUSB.

Now, I simply had to follow <https://grapheneos.org/install/web>.

And tada, after clicking buttons, GrapheneOS is installed on my Pixel 10a!

I was unfamiliar with such bare ecosystem as I've only ever used google-android
OSes. It did not include an app store, or a minimal one. So now, like anyone, I
went on GrapheneOS's forum and found this post: <https://discuss.grapheneos.org/d/17640-i-just-installed-grapheneos-where-do-i-get-good-apps>,
where I learned about [Obtainium](https://obtainium.imranr.dev/) and
[Aurora Store](https://github.com/whyorean/AuroraStore).

Unfortunately (or fortunately? you'll see why) I couldn't install one of my
banking app BoursoBank from Aurora Store nor from the sandboxed Google Play Store.
<https://grapheneos.org/usage#banking-apps> explains why and
<https://github.com/PrivSec-dev/banking-apps-compat-report/issues/147> have
many similar reports where other users also cannot install BoursoBank.
Fortunately for me, I don't use it anymore and don't have any money left there
anyway, I use another bank. I procrastinate the closing of my BoursoBank account
I know, but now I know even more why I should.
