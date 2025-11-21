# Gimii - Consent Raiser for Google Tag Manager

This Google Tag Manager (GTM) template provides a seamless integration for the Gimii consent raiser solution. The template dynamically loads the Gimii script to handle consent management and ad server integration.

## Overview

The Gimii Consent Raiser template is designed to:
- Load the Gimii consent management script
- Support both production and staging environments
- Integrate with Google Ads server
- Allow custom ads tag prefix configuration

## Configuration Parameters

### Raiser ID (Required)
- **Field Name**: `raiserId`
- **Type**: Text
- **Description**: Unique identifier for your Gimii consent raiser instance
- **Example**: `raiser_123`

### Environment (Required)
- **Field Name**: `env`
- **Type**: Select
- **Options**:
  - `production` - Uses `https://static.gimii.fr`
  - `staging` - Uses `https://static.gimii.dev`
- **Description**: Determines which Gimii environment to use

### Ads Prefix (Optional)
- **Field Name**: `adsPrefix`
- **Type**: Text
- **Description**: Custom prefix for ads tags when integrating with Google Ads
- **Example**: `my-site-prefix`

### Ad server (Required)
- **Field Name**: `adServer`
- **Type**: Select
- **Options**:
  - `google-ads` - Google Ads
  - `ms-monetize` - Microsoft Monetize (xandr)
  - `actirise` - Actirise
- **Description**: Determines which ad server to use

## Usage

### Basic Setup

1. Create a new tag in GTM using the Gimii Consent Raiser template
2. Configure the required parameters:
   - Set your `Raiser ID`
   - Select the appropriate `Environment`
3. Set the trigger to fire on page load or as needed
4. Publish your GTM container

### Advanced Configuration

For advanced setups with custom ads tag prefixes:

1. Follow the basic setup steps
2. Add your custom `Ads Prefix` value
3. The template will automatically append this to the script URL

## Script Loading

The template dynamically constructs the Gimii script URL based on your configuration:

### Production Environment
```
https://static.gimii.fr/gimii.js?raiserId={YOUR_RAISER_ID}&adServer=google-ads
```

### Staging Environment
```
https://static.gimii.dev/gimii.js?raiserId={YOUR_RAISER_ID}&adServer=google-ads
```

### With Ads Prefix
```
https://static.gimii.fr/gimii.js?raiserId={YOUR_RAISER_ID}&adServer=google-ads&adsTagPrefix={YOUR_PREFIX}
```

## Testing

The template includes comprehensive unit tests to ensure proper functionality:

### Test Scenarios

1. **Basic Production URL**: Validates correct URL construction for production environment
2. **Basic Staging URL**: Validates correct URL construction for staging environment  
3. **Production URL with Ads Prefix**: Validates URL construction with optional ads prefix parameter

### Running Tests

Tests are automatically executed during template deployment and can be run in the GTM interface under the template's test section.

## Error Handling

The template includes robust error handling:
- Success callbacks are triggered when the script loads successfully
- Failure callbacks are triggered if script loading fails
- All script injections are performed through GTM's secure `injectScript` API

## Security

The template follows GTM security best practices:
- Uses GTM's sandboxed JavaScript environment
- Only allows script injection from approved Gimii domains
- Validates all input parameters

## License

See the LICENSE file for license information.

## Changelog

### Version 1.0.0
- Initial release
- Support for production and staging environments
- Google Ads server integration
- Optional ads prefix configuration
- Comprehensive unit testing

### Version 1.1.0
- Add ad server field

### Version 1.1.1
- Fix template name