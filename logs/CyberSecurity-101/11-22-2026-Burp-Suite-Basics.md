# Burp Suite Basics - [11-22-2026]

## What This Covers

This lab introduces Burp Suite as a web application security testing framework used for intercepting, analysing, and manipulating HTTP/HTTPS traffic between a browser and a web server. It covers the different Burp Suite editions, the functionality available in the Community Edition, and the purpose of its main tools, including Proxy, Repeater, Intruder, Decoder, Comparer, and Sequencer. I explored the Burp Suite Dashboard, global and project settings, navigation, and proxy configuration. The lab also demonstrates how to connect Firefox to Burp Suite using FoxyProxy, configure the browser to send traffic through the local proxy, and inspect captured HTTP requests and responses. I worked with the Target tab to understand site mapping, issue definitions, and target scoping, and explored the built-in Burp Browser and HTTPS interception using the PortSwigger CA certificate. Finally, I followed a practical web application testing example involving a support form, where I used Burp Proxy to intercept a request, modify the submitted email parameter, URL-encode a reflected XSS payload, and forward the modified request to observe its execution.

## Key Concepts

* Understanding Burp Suite as a Java-based framework for web and mobile application penetration testing, including API security assessments.
* Understanding how Burp Suite intercepts and manipulates HTTP and HTTPS communication between a browser and a web server.
* Understanding the differences between Burp Suite Community, Professional, and Enterprise editions.
* Understanding the core features available in Burp Suite Community Edition.
* Understanding Burp Proxy and its role in intercepting and modifying HTTP requests and responses.
* Understanding Repeater and how it allows captured requests to be modified and resent multiple times.
* Understanding Intruder and its use in endpoint fuzzing and brute-force testing, with rate limitations in Community Edition.
* Understanding Decoder and its role in encoding and decoding captured data and payloads.
* Understanding Comparer and how it compares two pieces of data at the word or byte level.
* Understanding Sequencer and how it evaluates the randomness of session tokens and other generated values.
* Understanding Burp extensions, the Extender module, and the BApp Store.
* Understanding the Logger++ extension as an example of additional logging functionality.
* Exploring the Burp Dashboard and understanding its Tasks, Event log, Issue Activity, and Advisory sections.
* Understanding the difference between Global (User) settings and Project settings.
* Navigating Burp Suite settings through the search feature, type filters, and configuration categories.
* Understanding the Burp Proxy's Intercept functionality and how requests can be forwarded, dropped, modified, or sent to other Burp tools.
* Understanding HTTP History and WebSockets History and their importance in reviewing captured traffic.
* Understanding proxy settings such as response interception and Match and Replace.
* Configuring FoxyProxy in Firefox to redirect browser traffic through the Burp Proxy at 127.0.0.1:8080.
* Understanding the importance of enabling and disabling interception appropriately during testing.
* Understanding the Target tab and its Site map, Issue definitions, and Scope settings.
* Using the Site map to discover application pages and API endpoints by browsing the target while the proxy is active.
* Understanding how target scope controls which domains and IP addresses are included in testing.
* Configuring Burp Proxy to intercept only requests directed at in-scope targets.
* Understanding the Burp Browser and how it provides a preconfigured Chromium environment for proxy testing.
* Understanding the purpose of the PortSwigger CA certificate when intercepting HTTPS traffic.
* Importing the PortSwigger CA certificate into Firefox to trust HTTPS connections passing through Burp.
* Understanding reflected Cross-Site Scripting (XSS) and how client-side input filters can be bypassed during authorized testing.
* Intercepting a support form request, modifying the email parameter, URL-encoding a JavaScript payload, and forwarding the modified request.

## Commands/Tools Used

```text
# Burp Suite:
Burp Suite Community Edition

# Browser:
Mozilla Firefox

# Browser Proxy Extension:
FoxyProxy Basic

# Burp Proxy Configuration:
Proxy IP: 127.0.0.1
Proxy Port: 8080

# FoxyProxy Configuration:
1. Open FoxyProxy Options.
2. Create a new proxy configuration.
3. Set the proxy IP to 127.0.0.1.
4. Set the proxy port to 8080.
5. Save the configuration.
6. Activate the Burp proxy profile.
7. Enable Intercept in Burp Suite.


# Burp Suite Main Features:
Proxy
Repeater
Intruder
Decoder
Comparer
Sequencer
Extender

# Burp Dashboard:
Tasks
Event Log
Issue Activity
Advisory

# Burp Target Features:
Site Map
Issue Definitions
Scope Settings


# HTTPS Certificate Configuration:

# Download the PortSwigger CA Certificate:
http://burp/cert

# Firefox Certificate Settings:
about:preferences

# Certificate File:
cacert.der

# HTTPS Trust Configuration:
Import cacert.der
Trust this CA to identify websites


# Burp Browser:
Proxy -> Open Browser


# Target Scope Configuration:
Target -> Site Map
Right-click target -> Add To Scope

# Interception Scope Configuration:
Proxy -> Proxy Settings
Intercept Client Requests -> And URL Is in target scope


# Burp HTTP Traffic Analysis:
Proxy -> HTTP History
Proxy -> WebSockets History


# Practical Reflected XSS Exercise:
Target:
http://MACHINE_IP/ticket/

# Example Support Form Data:
Email: pentester@example.thm
Query: Test Attack

# Example XSS Payload:
<script>alert("Succ3ssful XSS")</script>

# Modify the Intercepted Request:
1. Enable Proxy Intercept.
2. Submit legitimate data through the support form.
3. Intercept the HTTP request.
4. Modify the email parameter with the XSS payload.
5. Select the payload and use Ctrl + U to URL-encode it.
6. Click Forward to send the modified request.
7. Observe the returned alert box.
```

## What I learned

I learned how Burp Suite works as an intermediary between a browser and a web application and how it can be used to inspect and manipulate HTTP/HTTPS traffic during security testing. I explored the Community Edition and understood the purpose of its main tools, including Proxy, Repeater, Intruder, Decoder, Comparer, and Sequencer. I then familiarised myself with the Dashboard, settings, navigation, and the difference between global and project configurations. I configured Firefox to communicate through Burp Suite using FoxyProxy with the proxy address 127.0.0.1 and port 8080, then understood how intercepted requests can be forwarded, dropped, modified, and reviewed through HTTP History. I also explored the Target tab, used the Site map to understand how web pages and endpoints are discovered, and configured target scope to restrict interception to the intended application. Additionally, I learned how Burp's built-in browser works and how the PortSwigger CA certificate allows HTTPS traffic to be inspected through the proxy. Finally, I applied Burp Proxy in the support form exercise by intercepting a request, modifying the email parameter with a reflected XSS payload, URL-encoding the payload using Ctrl + U, and forwarding the modified request to observe the resulting JavaScript alert.
