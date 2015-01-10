# ch-preseed - github-hosted preseed file

Not intended for any production use. This *will* wipe the drive.

## Usage

In order to run this fully automated installation of:

1. Boot from Debian ISO
2. At boot screen, hit ESC
3. Type: `auto url=z4.io`, press ENTER
4. Watch the installation
5. When finished, log on using `vagrant`/`vagrant`.

## Configuration

For this to work, Apache running at z4.io must be configured like this:

    SSLProxyEngine on
    SSLProxyVerify none
    SSLProxyCheckPeerCN off
    ProxyPass /d-i/wheezy/ https://raw.githubusercontent.com/claudehenchoz/ch-preseed/master/
    ProxyPassReverse /d-i/wheezy/ https://raw.githubusercontent.com/claudehenchoz/ch-preseed/master/

This ensures that a request to `http://z4.io/d-i/wheezy/preseed.cfg` is proxied to Github.
