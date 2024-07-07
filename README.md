# senthilnathan.js.org
Certainly! Here’s a concise version of each step for your architecture diagram documentation:

1. **Check Certificate Expiry**: If the VPN certificate is expiring, initiate the renewal process.
2. **Perform Health Check**: Check the renewal API’s health; if OK, proceed. If not, switch to the next TPP endpoint on port 8081.
3. **Request New Certificate**: Create a CSR for the VPN certificate and request a new certificate from the renewal API, which calls Venafi TPP. If successful, receive the certificate path key; otherwise, get error details.
4. **Validate Certificate**: Attempt to retrieve the certificate using the certificate path key. The renewal API calls Venafi TPP with this key, repeating the process up to four times.
5. **Delete Existing Certificate**: Remove the existing SSAC certificate.
6. **Request New Certificate**: Create a CSR for the VPN certificate and request a new certificate from the renewal API, which calls Venafi TPP. If successful, receive the certificate path key; otherwise, get error details.
7. **Validate Certificate**: Attempt to retrieve the certificate using the certificate path key. The renewal API calls Venafi TPP with this key, repeating the process up to four times.
8. **Retrieve Certificate**: If validation succeeds, obtain the certificate bundle chain from the renewal API.
9. **Complete Renewal**: Conclude the renewal process.

These lines should help in creating a clear and concise architecture diagram.
Sure, here are the corrected and concise steps for your architecture diagram:

1. If the certificate type is SSAC, delete the existing certificate.
2. Perform a health check on the renewal API; if it returns "OK", proceed to the next step, otherwise, switch to the next TPP endpoint on port 8081.
3. Create a CSR and request a new certificate from the renewal API, which then calls Venafi TPP; if successful, it returns the certificate path key, otherwise, it returns error information.
4. Validate the certificate by attempting to retrieve it twice using the certificate path key via the renewal API's call to Venafi TPP.
5. If validation is successful, retrieve the certificate bundle chain from the renewal API.
6. Complete the certificate trust chain installation process.
