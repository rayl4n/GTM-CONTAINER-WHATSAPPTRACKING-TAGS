# GTM Container, Tags for WhatsApp Tracking Home

# 🛠️ Remote Services | Serviços remotos

🇺🇸 - If you wish, [we can track you](https://academiadetrackeamento.com.br), just hire our services via the email below.
<br>
🇧🇷 - Se desejar, podemos [fazer o seu trackeamento](https://academiadetrackeamento.com.br) basta contratar nossos serviços através do email abaixo.
<br>
✉️ - Endereço EXCLUSIVO para contratação de serviços: raylan.gig@gmail.com.

# Basic Info

Note|Description
:----|:----
Supported GTM Side|Web and Server.

- Release date: 05/01/2025
- Current tagging server version: 2.4.0

# Basic Steps

1. Include necessary variables (userData, Geolocation, Cookies);
2. Review the special notes;
3. Generate a Webhook URL in n8n
4. Adjust key value in GA4 tag

# Features
- [x] Basic tags, very light and clean for your tracking.
- [x] Built with the latest versions of Google Tag Manager

# TAG's included (**Required**)

TAG|Description
:----|:----
HTTP Request(https://github.com/stape-io/json-http-request-tag)|Required to send requests to n8n
Google Analytics: evento do GA4|Use the standard tag or use a [Stape GA4 Advanced tag](https://github.com/stape-io/ga4-advanced-tag).

# Other (not included)

Triggers, variables and folders

### Trigger
Trigger|Description
:----|:----
gtm.dom / visitor-api-success|Triggered when loading the visitor-api-success event in order to capture the visitor's geolocation data
WhatsAppTrackingTag|Same name used at the GA4 event.

### Variables
Variable|Description
:----|:----
First-party cookie|Store fixed data
Custom JavaScript|capture data from input fields on the form
DataLayer Variable|capture geolocation data

### Extract the selector from the form fields

Open DevTools and select the field
```
Right-click/inspect
```


## Discord - Academia de Trackeamento
- [Access Discord](https://discord.gg/GTzGmKNFy8)
