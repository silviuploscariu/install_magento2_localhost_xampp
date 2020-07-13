1. Install XAMPP v3.2.4
    LINK: https://www.apachefriends.org/download.html -> 7.2.31

2. Uncomment in XAMPP php.ini:
    - extension=xsl
    - extension=intl
    - intl.default_locale
    - extension=soap

3. Install Magento v2.3.3
    LINK: https://magento.com/tech-resources/download -> 2.3.3 + Include sample data

    - Unzip 'Magento-2.3.3.zip' in 'XAMPP-directory\htdocs\APP-directory'
    - Go to 'localhost/APP-directory/setup

    - CLICK -> 'Agree and Setup Magento'
    - CLICK -> 'Start Readiness Check'
    - If you have errors check if you complete modification in php.ini from step 2.
    - CLICK -> 'Next'
    - Complete info with database name, password, user -> CLICK -> 'Next' 
    - Type in 'Magento Admin Address' only 'admin' -> CLICK -> 'Next'
    - Let default to all -> CLICK -> 'Next'
    - Complete with following

        Example: 

        - New Username: admin
        - New Email: admin@admin.admin
        - New Password: admin123
        - Confirm Password: admin123
    
    - CLICK -> 'Install Now' and wait to complete the install

4. Configurations
    - Open CMD (Windows -> Type -> 'cmd' -> PRESS -> Enter) or Terminal
    - Go to your directory ex "cd: 'XAMPP-directory\htdocs\APP-directory'"
    - Run Comands:
        - php bin/magento setup:upgrade
        - php bin/magento setup:static-content:deploy -f
        - php bin/magento setup:di:compile
        - php bin/magento c:f
        - php bin/magento deploy:mode:show
        - php bin/magento deploy:mode:set developer
            If error 'The directory "XAMPP-directory/htdocs/APP-directory/generated/code/Magento" cannot be deleted Warning!rmdir(XAMPP-directory/htdocs/APP-directory/generated/code/Magento): Directory not empty'
            - rmdir /q generated
            - rmdir /s generated
                Type 'Y'
        - php bin/magento c:f
    - Go to 'XAMPP-directory\htdocs\APP-directory\vendor\magento\framework\View\Element\Template\File' \
        - Open in editor 'Validator.php'
        - Replace 
            $realPath = $this->fileDriver->getRealPath($path);
            with 
            $realPath = str_replace('\\', '/', $this->fileDriver->getRealPath($path));
        - Remove / Delete cache
            - XAMPP-directory\htdocs\APP-directory\var\cache 
5. DONE!

* NOTE :
    - In my case XAMPP-directory is 'D:\XAMPP'
    - In my case APP-directory is 'magento2'

