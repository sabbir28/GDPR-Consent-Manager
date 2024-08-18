

### Description

**GDPR Consent Manager** is an Android application designed to help developers easily integrate GDPR (General Data Protection Regulation) consent handling into their apps. This project leverages Google's User Messaging Platform (UMP) SDK to display and manage consent messages for users within the European Economic Area (EEA) and the UK, ensuring compliance with regulations when serving personalized ads using Google AdMob.

---

### Features

- **Easy Integration:** Simplified setup process to integrate GDPR consent management into your Android app.
- **User-Friendly Interface:** Customizable consent message that informs users about data usage in a clear and concise manner.
- **Consent Storage & Management:** Automatically stores user consent choices and provides options to withdraw or modify consent.
- **Compliance with GDPR:** Ensures that your app adheres to GDPR requirements by supporting both personalized and non-personalized ads.
- **Support for Multiple SDKs:** Seamless integration with Google AdMob and other ad networks via mediation partners.

---

### Installation

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/yourusername/GDPR-Consent-Manager.git
   ```
2. **Open the Project:**
   - Open the project in Android Studio.
   - Ensure that you have the latest Android SDK and Google Play Services installed.

3. **Add UMP SDK to Your Project:**
   - In your `build.gradle` (app level), add the UMP SDK dependency:
     ```gradle
     implementation 'com.google.android.ump:user-messaging-platform:2.0.0'
     ```

4. **Initialize the SDK:**
   - Initialize the UMP SDK in your `MainActivity`:
     ```java
     import com.google.android.ump.ConsentInformation;
     import com.google.android.ump.ConsentRequestParameters;
     import com.google.android.ump.UserMessagingPlatform;
     
     public class MainActivity extends AppCompatActivity {
         @Override
         protected void onCreate(Bundle savedInstanceState) {
             super.onCreate(savedInstanceState);
             setContentView(R.layout.activity_main);
             
             ConsentRequestParameters params = new ConsentRequestParameters
                 .Builder()
                 .setTagForUnderAgeOfConsent(false)
                 .build();

             ConsentInformation consentInformation = UserMessagingPlatform.getConsentInformation(this);
             consentInformation.requestConsentInfoUpdate(
                 this,
                 params,
                 () -> {
                     // Handle success
                 },
                 requestConsentError -> {
                     // Handle failure
                 });
         }
     }
     ```

---

### Usage

1. **Customizing the Consent Message:**
   - Edit the message configuration in the UMP setup to reflect your app’s data usage policies.

2. **Showing the Consent Form:**
   - Implement logic to show the consent form when required:
     ```java
     consentInformation.showConsentFormIfRequired(
         this,
         form -> form.show(
             this,
             formError -> {
                 // Handle form dismissal
             }));
     ```

3. **Handling Consent Revocation:**
   - Implement a way for users to withdraw their consent choices by showing the privacy options form:
     ```java
     consentInformation.showPrivacyOptionsForm(this);
     ```

---

### Contribution

1. **Fork the Repository**
2. **Create a Feature Branch**
   ```bash
   git checkout -b feature-branch
   ```
3. **Commit Your Changes**
   ```bash
   git commit -m 'Add a new feature'
   ```
4. **Push to the Branch**
   ```bash
   git push origin feature-branch
   ```
5. **Create a Pull Request**

---

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

### Contact

**MD. Sabbir Hoshen**  
*Email*: [sabbirb228@gmail.com](mailto:sabbirb228@gmail.com)  
*GitHub*: [sabbir28](https://github.com/sabbir28)  
*Google Help Site*: [developers.google.com](https://developers.google.com/admob/android/privacy)  
