# croxy proxy youtube

croxy proxy youtube ( Specially designed for youtube access ) is a PHP script proxy and helps in hiding the client's identity and allows them to access resources on the server indirectly. The proxy script receives client requests and forwards them to the server then returns the server's response back. This proxy script allows you to forward all HTTP/HTTPS requests to another server. 
Here are some additional details about PHP script proxies:
 
Proxies can also be used to cache responses from the server. This can help improve performance .
They can protecting the server from potential security threats.
This can be useful for debugging or tracking usage patterns.

## How to use
* Copy the [Proxy.php](Proxy.php) script to publicly-accessible folder 
* Make a cURL request targeting this script
* Add **Proxy-Auth** header with auth key [found here](https://github.com/zounar/php-proxy/blob/master/Proxy.php#L40)
* Add **Proxy-Target-URL** header with URL to be requested by the proxy
 

for security reasons consider changing `Proxy-Auth` token in [proxy source file](https://github.com/zounar/php-proxy/blob/master/Proxy.php#L40).

## How to use (via composer)
This might be useful when you want to redirect requests coming into your app. 

* Run `composer require zounar/php-proxy`
* Add `Proxy::run();` line to where you want to execute it (usually into a controller action)
  * In this example, the script is in `AppController` - `actionProxy`:
    ```
    use Zounar\PHPProxy\Proxy;
    
    class AppController extends Controller {

        public function actionProxy() {
            Proxy::$AUTH_KEY = '<your-new-key>';
            // Do your custom logic before running proxy
            $responseCode = Proxy::run();
            // Do your custom logic after running proxy
            // You can utilize HTTP response code returned from the run() method
        }
    }
    ```
* Make a cURL request to your web
  * In the example, it would be `http://your-web.com/app/proxy`
* Add **Proxy-Auth** header with auth key [found here](https://github.com/zounar/php-proxy/blob/master/Proxy.php#L40)
* Add **Proxy-Target-URL** header with URL to be requested by the proxy
* (Optional) Add **Proxy-Debug** header for debug mode


