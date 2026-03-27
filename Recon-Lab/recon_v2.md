# Reconnaissance Phase - A more information guide !!!

## https://subdomain.domain.com/path/q=sas

## https://subdomain.domain.com/path/file.name

## https://subdomain.domain.com/path/version


## Front-End / Client
1. HTML
    -> Version being used ?
    ~ Steps 
        
        Look at the DOCTYPE at the top of the page source:
            1. HTML5: <!DOCTYPE html>
            2. Older versions:
                <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" ...>
            3. Open Developer Tools (F12) -> Elements tab -> view the source.
        
    ~Tools
        1. Wappalyzer (browser extenstion) - shows HTMLversion among other tech.
        2. BuiltWith (website or extension) - lists detected technologies.
        3. WhatWeb (CLI) - whatweb https://example.com includes HTML version detection.

2. CSS 
    -> Framework being used ? // Version being used ?
    ~ Steps 

        Inspect the <head> section for <link> tags pointing to CSS files:
            1. Bootstrap: bootstrap.min.css or bootstrap.css
            2. Tailwind: tailwind.css or class names like flex, p-4
            3. Foundation: foundation.css
        
        Look for class names in elements:
            1. Bootstrap: container, row,col-md-6
            2. Tailwind: text-center, bg-blue-500

        Check source maps or comments that might reveal framework and versions.

    ~ Version Extraction
        1. Sometimes version is in the filename: bootstrap-4.6.0.min.css.
        2. Use tools like wappalyzer or Retire.js to detect version.
        3. For Bootstrap, you can also check global JavaScript object: typeof bootstrap !== 'undefined' in console.

    ~ Tools
        Wappalyzer - identifies CSS frameworks.
        WhatRuns (browser extension) - shows frameworks and versions.
        Retire.js - specifically finds vulnerable versions of libraries (including CSS/JS).
    

3. 
    -> Languages being used ? // Version being used ?
     ~ Info 
        - Modern web apps use JavaScript (ECMAScript). You may see TypeScript (compiled to JS) via source maps or comments like //# sourceMappingURL.
        - Detection is less about language version and more about frameworks/libraries.

    -> Framework being used ? // Version being used ?
     ~ Info
        React
            1. Look for data-reactroot r data-reactid attributes in DOM
            2. In console, check if window.React or window.REactDOM exists.
            3. Look for JS files like react.js, react-dom.js, or buncled with .chunk.js.

        Vue
            1. data-v- attributes on elements.
            2. windows.Vue in console.
            3. Files: vue.js, vue.min.js.

        Angular
            1. ng- attributes (e.g., ng-app).
            2. window.angular in console.
            3. Files: angular.js, main.js with Angular-specific patterns.

        jQuery
            1. $ or jQuery in console.
            2. Files: jquery.min.js,

    ~ Version Extraction
        1. Check the filename for versions (e.g., react-16.8.6.js).
        2. Look at source map URL (if present) - often includes version.
        3. Use console
            - React: React.version
            - Vue: Vue.version
            - AngularJS: angular.version.full
            - jQuery: $.fnjquery
        4. Use browser extensions: Wappalyzer, Library Detector, Retire,js.

## Back-End / Server
    -> Languages being used ? // Version being used ?
    -> Framework being used ? // Version being used ?
   
    ~ Manula Techniques
        HTTP Response Headers
            1. Server header - e.g., Server: Apache/2.4.41 (web server)

            2. X-Powered-By - e.g., X-Powered-By: PHP/7.4.33, X-Powered-By: Express
            
            3. Custom framework headers
                1. X-Runtime -> Ruby on Rails
                2. X-Django-* ->  Django
                3. X-AspNet-Version -> ASP.NET
                4. X-Frame-Options sometimes hints at frameworks (but not definitive)
        Cookies
            1. PHPSESSID -> PHP
            2. JSESSIONID -> Java
            3. laravel_session -> Laravel (PHP)
            4. ASP.NET_SessionId -> ASP.NET
            5. csrftoken -> Django
            6. _session_id -> Ruby on Rails

        URL Patterns & Extensions
            1. .php -> PHP
            2. .aspx, .asp -> ASP.NET
            3. .do, .jsp  Java (Struts, JSP)
            4. Clean URLs with no extension often indicate a framework like Express, Django, Laravel, etc.

        Error Messages
            Trigger errors by adding unexpected characters, malformed JSON, or invalid paths.
                PHP Parse error -> PHP
                Django version 3.2.8 -> Django + version
                ASP.NET yellow screen -> .NET version
                Express error stack -> Node.js/Express

        Default Paths & Files
            1. /wp-admin, /wp-content -> WordPress (PHP)
            2. /admin, /manager
            3. /api/ endpoints -> sometimes reveal framework in JSON responses
            4. /robots.txt, /sitemap.xml, /.env, /composer.json, /package.json (if exposed)

        HTML/JS Comments & Source Maps
            1. <!-- Powered by Django 3.2 -->
            2. Source maps may include server-side filenames or paths.
        
    ~ Tools
        1. Wappalyzer
        2. WhatWeb
        3. BuiltWith
        4. Nmap with http-headers, http-enum scripts

    ~ Extracting Versions
        1. Headers -> sometimes X-Powered-By: PHP/8.1.2
        2. Error pages -> often print full version numbers in stack traces
        3. Default assets -> e.g., /wp-includes/css/... may contain version in filename
        4. Source maps -> /dist/app.js.map might reveal server-side version comments
        5. Tool output -> whatweb often shows version when aggressive (-a 3)

        
## Database 
    -> Type of database being used ?
    -> Which database is being used to stored data ? // Version of database being used ?
    -> The ORM of database being used ? // Version being used ? 

## APIs 
    -> What bridge is being used ? // Version used ? 

## Enviroment & Hosting 
    -> Platform-as-a-Service (PaaS) // Version being used ?
    -> Cloud providers ? // Version being used ?
    -> Virtual Provider Services (VPS) // Version being used ?

## Container orchestration 
    -> Which is being used // Version being used ?

## Contanious Integration / Continous Deployment 
    -> Which is being used // Version being used ?

## SSL / TLS - This is what enables HTTPS
    -> Which is being used // Version being used ?

## Content Delivery Network (CDN)
    -> Which is being used // Version being used ?

## Content Management Services (CMS)
    -> Which is being used // Version being used ?

## Caching
    -> Which is being used // Version being used ?

## Secuirty headers
    -> What security headers are being used ?
    -> What security headers are missing ?

## Third-Party Services & Integrations
    -> What third party exist ? 

## Operating Sytemt
    -> What Operating System is being used // Version being used ?

## Web Application on Firewall (WAF)
    -> What WAF is being used // Version being used ?

## Intrusion Detection System and Intrution Prevention System(IDS/IPS)
    -> Type of IDS & IPS being used // Version being used ?

## DNS & Subdomain Enumeration
    -> Enumerate subdomains ?

## Directory & File Discovery
    -> Enumerate directory & file ?
    
## Parameter discovery 
    -> Enumerate paremeter ?

## Tokens, sessions & cookies
    -> Identify them ?
    -> Know where they are being implemented ?
