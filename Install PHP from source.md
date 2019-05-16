# Install PHP from source
### Download PHP to `/usr/src` folder from PHP.Net website

    sudo wget https://php.net/distributions/php-<version>.tar.bz2

Extract the archive

    sudo tar xf php-<version>.tar.bz2 --directory .

Delete the archive

    sudo rm php-<version>.tar.bz2

Navigate into the new PHP directory

    cd /usr/src/php-<version>

Install essential packages

    sudo apt-get install build-essential

Install required dependent libraries

    sudo apt-get install libxml2-dev libssl-dev libcurl3-dev libcurl4-openssl-dev

Create soft link to cURL installation

    sudo ln -s x86_64-linux-gnu/curl

Execute the configure script for the custom CLI installation

    sudo ./configure \
    --with-config-file-path=/etc/php/<version>/cli \
    --with-pear=/usr/share/php \
    --enable-libxml=/usr \
    --with-mysqli \
    --with-zlib \
    --with-iconv=shared \
    --with-pdo-mysql=shared \
    --enable-pdo \
    --with-openssl \
    --with-curl

You can execute only with required extentions (minimal version)

    sudo ./configure --disable-all --prefix=/usr --with-config-file-path=/etc/php.ini --with-config-file-scan-dir=/etc/php.d

Compile the custom PHP version

    sudo make

Install the new version

    sudo make install

Test the new installation

    php -v