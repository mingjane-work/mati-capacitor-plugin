# MetaMap for Capacitor Usage Guide

The following instructions use command line tools to install MetaMap for Capacitor to your existing Capacitor application.

1. Use the following CLI to install MetaMap for your Capacitor project.
```bash
    npm i @avo121/mati-capacitor-plugin
  ```

2. Build your application.
```bash
    ionic build
  ```
3. Update the Capacitor files.
```bash
    npx cap sync
  ```

4. Add the MetaMap button to your application's HTML and JavaScript files.

`your_index.html`

```html
    <ion-content>
    <ion-button className="metaMapButtonCss" (click)="showMetaMapFlow()">Show MetaMapFlow
    </ion-button>
    </ion-content>
```

`your_index.ts`

```bash
import { Component } from '@angular/core';

import { MetaMapCapacitor } from "@avo121/mati-capacitor-plugin";

@Component({
  selector: 'app-home',
  templateUrl: 'home.page.html',
  styleUrls: ['home.page.scss'],
})
export class HomePage {
  constructor() {}

  showMetaMapFlow() {
    let metadataParams = { param1: "value1" };
    let registerParams = { clientId: "YOUR_CLIENT_ID", flowId: "YOUR_FLOW_ID", metadata: metadataParams};

    MetaMapCapacitor.showMetaMapFlow(registerParams)
      .then( verification => console.log("verification success:" + verification.verificationId))
      .catch(() => console.log("verification cancelled"))
  }
}
```

## Launch for Android

1. Run the following command to launch the application for Android:
```bash
ionic capacitor run android
```

# Launch for iOS

1. Set minimum iOS version in `capacitor.config.json`
 ```bash
     "ios": {
      "minVersion": "12.0"
    }
```

2. Add the following to info.plist:
```bash
<key>NSCameraUsageDescription</key>
<string>MetaMap verification SDK requires camera use</string>

<key>NSMicrophoneUsageDescription</key>
<string>MetaMap verification SDK requires microphone use</string>

<key>NSPhotoLibraryUsageDescription</key>
<string>MetaMap verification SDK requires access to media library</string>

<key>NSLocationWhenInUseUsageDescription</key>
<string>MetaMap will use your location information to provide best possible verification experience.</string>

<key>NSLocationAlwaysAndWhenInUseUsageDescription</key>
<string>MetaMap will use your location information to provide best possible verification experience.</string>

<key>NSLocationAlwaysUsageDescription</key>
<string>MetaMap will use your location information to provide best possible verification experience.</string>
```

3. Launch the application for iOS
```bash
    ionic capacitor run ios
   ```