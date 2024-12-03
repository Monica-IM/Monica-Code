# Troubleshooting Guide

This guide covers common issues and their solutions when using Monica Code IDE extensions.

## Table of Contents
- [Network and Proxy Issues](#network-and-proxy-issues)
- [IDE Compatibility Issues](#ide-compatibility-issues)

## Network and Proxy Issues

### Symptoms
When you need special proxy settings to connect to Monica, you might encounter:
- Network errors or ETIMEDOUT errors in VS Code/IDE
- Plugin shows no response after web login
- Connection failures

### Solutions

1. **VS Code Proxy Settings**
   - VS Code extensions typically use the VS Code application's proxy settings
   - No special configuration is usually needed
   - For detailed documentation about `http.proxySupport`, visit https://code.visualstudio.com/docs/getstarted/settings

2. **Manual Proxy Configuration**
   - For JetBrains IDEs (Monica Code version >= **1.0.1**) or VS Code (>= **1.1.21**), you can configure proxy in config.json
   - Location: typically at `~/.monica-code/config.json`
   - Configuration structure:
     ```jsonc
     {
       // other setting remains unchanged
       "requestOptions": {
         "proxy": "http://your-proxy-url:port"
       }
     }
     ```
     Full options:
     ```
     {
       "requestOptions": {
         "proxy": "http://your-proxy-url:port",  // HTTP/HTTPS proxy URL
         "verifySsl": true,                      // Optional: SSL verification
         "caBundlePath": "",                     // Optional: Custom CA bundle path
         "clientCertificate": {                  // Optional: Client certificate settings
           "cert": "",                           // Certificate file path
           "key": "",                            // Certificate key file path
           "passphrase": ""                      // Certificate passphrase
         }
       }
     }
     ```
   - In most cases, setting only the `proxy` parameter is sufficient
   - Other parameters are optional and rarely needed for basic setup


## IDE Compatibility Issues

### JCEF Support Issues (Monica Code window doesn't appear after activation)

Monica Code requires JCEF (JetBrains Chromium Embedded Framework) support to function properly. In IDEs without JCEF support or with incorrect JCEF configuration, the Monica Code window may not appear at all. (Note: **Android Studio** default runtime does not include JCEF support)

### Symptoms
- Monica Code window doesn't appear after activation
- No visible error messages in older Monica Code versions

### Solutions

1. **Check and Configure JCEF Support**
   - Open IDE Action Search (⌘⇧A / Ctrl+Shift+A)
   - Search for "Choose Boot Java Runtime for IDE"
   - Select a runtime that explicitly includes "with JCEF" in its name
   - Restart your IDE after changing the runtime

If the above solution doesn't resolve your issue, please feel free to ask for further assistance.

## Still Need Help?

If your issue isn't covered here or the solutions don't work:

1. Check our [GitHub Issues](https://github.com/Monica-IM/monica-code/issues) for similar problems
2. Create a new issue following our [issue guidelines](README.md#issue-reporting)
3. Contact [customer support](https://monica.im/feedback?platform=monica_code) for account-related issues

## Updates

This troubleshooting guide is regularly updated. If you encounter an issue not listed here, please let us know through GitHub issues.
