# LAB-14.3

1. CSRF and the state Parameter: In your own words, explain how an attacker could perform a Cross-Site Request Forgery (CSRF) attack on an OAuth flow. How does using the state parameter, as recommended, prevent this specific attack?

 - Answer: An attacker could initiate an Oauth login process using their own external profile, then proceed to intercept the final authorization response (the token or code). Then the bad actor would trick a victim into clicking a request link that would bind the victim's local account to the attackers external profile using the attacker's generated token or code. Also known as Account TakeOver or Session Hijacking the attacker would then have open access to the victim's account using their (the attacker's) profile credentials.

2. Redirect URI Attacks: The article mentions that validating a redirect_uri by simply checking the domain or allowing subdomains is a common mistake. Describe a hypothetical scenario where a “leaky” redirect_uri validation (e.g., one that allows any path on a valid domain) could be exploited to steal an authorization code.
 
 - Answer: A bad actor could exploit this by creating a malicious link pointing to an identity provider instead of a legitimate landing path. The malicious path would contain the open redirector pointing back to an attacker controlled server. The user clicks the link and is promted to login at said identity provider, the "loose" policy check would match and issue an authorization code. The identity provider then issues a redirect to the malicious redirect_uri including the Authorization code in the query string.

3. User Experience vs. Security: Adding a third-party login option like “Login with Google” is a significant user experience improvement. However, it also introduces complexity and new potential security risks. Based on the article and your own thoughts, describe one key trade-off a development team must consider when deciding to implement OAuth. (For example, think about the balance between convenience for the user and the responsibility of the application to protect user data).

 - Answer: Although not having to enter/save many passwords and faster sign up is greatly appreciated, security risks would be the biggest trade off with all the work arounds described in the article. There would have to be a vast amount of security expertise before implementing a feature that just speeds up login experience vs user data safety.
