# Protocol: marina

## Host redirect

- A Config > Wii checkbox, "Connect Nintendo WFC to OpenPak", redirects the
  console's WFC host names to OpenPak. The host list and address come from a
  network profile fetched at launch, checked against a list compiled into the
  build, with the last good profile and then a built-in list as fallbacks.

## Connecting to OpenPak

Create an account at https://openpak.org, then use OpenPak > Sign in in the
emulator. The account only names you and authorises cloud saves; WFC itself
has no accounts. Tick the WFC checkbox in Config > Wii to redirect the
console's names to OpenPak. Games that need a patch to use plain HTTP for
their login also need OpenPak's stage-0 Gecko code, published with the
wii-patcher project in the OpenPak organisation.
