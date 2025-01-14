# Exchange Payload  

 [Configuration Profile Reference - Exchange Payload](https://developer.apple.com/library/content/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010206-CH1-SW25)  

In iOS, the Exchange payload is designated by specifying `com.apple.eas.account` as the `PayloadType` value. This payload configures an Exchange Active Sync account on the device.  

In macOS, the Exchange payload is designated by specifying `com.apple.ews.account` as the `PayloadType` value. This payload will configure an Exchange Web Services account for Contacts, Mail, Notes, Reminders, and Calendar.  

In addition to the settings common to all payloads, this payload defines the following keys:  

|Key|Type|Value|
|-|-|-|
|Available in both iOS and macOS|
|`EmailAddress`|String| Specifies the full email address for the account. If not present in the payload, the device prompts for this string during profile installation.</br>In macOS, this key is required.|
|`Host`|String|Specifies the Exchange server host name (or IP address).</br>In macOS 10.11 and later, this key is optional.|
|`SSL`|Boolean|Optional. Default YES. Specifies whether the Exchange server uses SSL for authentication.|
|`UserName`|String|This string specifies the user name for this Exchange account. If missing, the devices prompts for it during profile installation.</br>In macOS, this key is required.|
|`Password`|String|Optional. The password of the account. Use only with encrypted profiles.|
|Available in iOS only|
|`Certificate`|NSData blob|Optional. For accounts that allow authentication via certificate, a .p12 identity certificate in NSData blob format.|
|`CertificateName`|String|Optional. Specifies the name or description of the certificate.|
|`CertificatePassword`|Data|Optional. The password necessary for the p12 identity certificate. Used with mandatory encryption of profiles.|
|`PreventMove`|Boolean|Optional. Default `false`.</br>If set to `true`, messages may not be moved out of this email account into another account. Also prevents forwarding or replying from a different account than the message was originated from.</br>**Availability:** Available in iOS 5.0 and later.|
|`PreventAppSheet`|Boolean|Optional. Default `false`. If set to `true`, this account will not be available for sending mail in any app other than the Apple Mail app.</br>**Availability:** Available in iOS 5.0 and later.|
|`PayloadCertificateUUID`|String|UUID of the certificate payload to use for the identity credential. If this field is present, the `Certificate` field is not used.</br>**Availability:** Available in iOS 5.0 and later.|
|`SMIMEEnabled`|Boolean|Optional. Default `false`. If `true`, this account supports S/MIME. </br>As of iOS 10.0, this key is ignored.</br>**Availability:** Available only in iOS 5.0 through 9.3.3.|
|`SMIMESigningEnabled`|Boolean|Optional. Default `true`. If set to `true`, S/MIME signing is enabled for this account. </br>**Availability:** Available only in iOS 10.3 and later.|
|`SMIMESigningCertificateUUID`|String|Optional. The `PayloadUUID` of the identity certificate used to sign messages sent from this account.  </br>**Availability:** Available only in iOS 5.0 and later.|
|`SMIMEEncryptionEnabled`|Boolean|Optional. Default `false`. If set to `true`, S/MIME encryption is on by default for this account. </br>**Availability:** Available only in iOS 10.3 and later. As of iOS 12.0, this key is deprecated. It is recommended to use `SMIMEEncryptByDefault` instead.|
|`SMIMEEncryptionCertificateUUID`|String|Optional. The `PayloadUUID` of the identity certificate used to decrypt messages sent to this account. The public certificate is attached to outgoing mail to allow encrypted mail to be sent to this user. When the user sends encrypted mail, the public certificate is used to encrypt the copy of the mail in their Sent mailbox. </br>**Availability:** Available only in iOS 5.0 and later.|
|`SMIMEEnablePerMessageSwitch`|Boolean|Optional. Default `false`. If set to `true`, displays the per-message encryption switch in the Mail Compose UI. </br>**Availability:** Available only in iOS 8.0 and later. As of iOS 12.0, this key is deprecated. It is recommended to use `SMIMEEnableEncryptionPerMessageSwitch` instead.|
|`SMIMESigningUserOverrideable`|Boolean|Optional. Default `false`. If set to `true`, the user can toggle S/MIME signing on or off in Settings. </br>**Availability:** Available only in iOS 12.0 and later.|
|`SMIMESigningCertificateUUIDUserOverrideable`|Boolean|Optional. Default `false`. If set to `true`, the user can select the signing identity. </br>**Availability:** Available only in iOS 12.0 and later.|
|`SMIMEEncryptByDefault`|Boolean|Optional. Default `false`. If set to `true`, S/MIME encryption is enabled by default. If `SMIMEEnableEncryptionPerMessageSwitch` is `false`, this default cannot be changed by the user. </br>**Availability:** Available only in iOS 12.0 and later.|
|`SMIMEEncryptByDefaultUserOverrideable`|Boolean|Optional. Default `false`. If set to `true`, the user can toggle the encryption by default setting. </br>**Availability:** Available only in iOS 12.0 and later.|
|`SMIMEEncryptionCertificateUUIDUserOverrideable`|Boolean|Optional. Default `false`. If set to `true`, the user can select the S/MIME encryption identity and encryption is enabled. </br>**Availability:** Available only in iOS 12.0 and later.|
|`SMIMEEnableEncryptionPerMessageSwitch`|Boolean|Optional. Default `false`. If set to `true`, enable the per-message encryption switch in the compose view and encryption is enabled. </br>**Availability:** Available only in iOS 12.0 and later.|
|`disableMailRecentsSyncing`|Boolean|If `true`, this account is excluded from address Recents syncing. This defaults to `false`.</br>**Availability:** Available only in iOS 6.0 and later.|
|`MailNumberOfPastDaysToSync`|Integer|The number of days since synchronization.|
|`CommunicationServiceRules`|Dictionary|Optional. The communication service handler rules for this account. The `CommunicationServiceRules` dictionary currently contains only a `DefaultServiceHandlers` key; its value is a dictionary which contains an `AudioCall` key whose value is a string containing the bundle identifier for the default application that handles audio calls made to contacts from this account.|
|`OAuth`|Boolean|Optional. Specifies whether the connection should use OAuth for authentication. If enabled, a password should not be specified. This defaults to `false`.</br>**Availability:** Available only in iOS 12.0 and later.|
|Available in macOS Only|
|`Path`|String|Optional.|
|`Port`|Integer|Optional.|
|`ExternalHost`|String|Optional.|
|`ExternalSSL`|Boolean|Optional.|
|`ExternalPath`|String|Optional.|
|`ExternalPort`|Integer|Optional.|
  


> **Note:** As with VPN and Wi-Fi configurations, it is possible to associate an SCEP credential with an Exchange configuration via the `PayloadCertificateUUID` key.  
  
