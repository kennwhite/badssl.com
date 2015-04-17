[![badssl.com](badssl.com.png)](https://badssl.com)

Visit [`badssl.com`](https://badssl.com/) for a list of test subdomains, including:

- [`self-signed.badssl.com`](https://self-signed.badssl.com)
- [`wrong.host.badssl.com`](https://wrong.host.badssl.com)
- [`expired.badssl.com`](https://expired.badssl.com)
- [`incomplete-chain.badssl.com`](https://incomplete-chain.badssl.com)
- [`sha1.badssl.com`](https://sha1.badssl.com)
- [`mixed.badssl.com`](https://mixed.badssl.com)
- [`rc4.badssl.com`](https://rc4.badssl.com)
- [`cbc.badssl.com`](https://cbc.badssl.com)
- [`hsts.badssl.com`](https://hsts.badssl.com)
- [`preloaded-hsts.badssl.com`](https://preloaded-hsts.badssl.com)

## Server Setup

Stock Ubuntu VM, DNS A records for `badssl.com.` and `*.badssl.com.` pointing to the VM.

Push the code into `~/badssl/` on the server:

    make deploy

Set up nginx on the server:

    sudo apt-get update
    sudo apt-get install nginx

    # Link repo into /var/www
    sudo ln -s "${HOME}/badssl" /var/www/badssl

    sudo ln -s /var/www/badssl/config/nginx.conf /etc/nginx/sites-available/badssl
    sudo ln -s /etc/nginx/sites-available/badssl /etc/nginx/sites-enabled/badssl

    # Make sure the actual keys are in /etc/keys/
    sudo service nginx restart

