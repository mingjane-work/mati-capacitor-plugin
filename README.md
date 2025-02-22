# Metamap for Capacitor Usage Guide

This is a guide to implement Metamap in the [Ionic Capacitor framework](https://capacitorjs.com/docs).

## Capacitor Demo App

You can go to GitHub to download the [Metamap Capacitor demo app](https://github.com/GetMati/mati-mobile-examples/tree/main/capacitorDemoApp).

## Install Metamap for Capacitor

The following instructions use command line tools to install Metamap for Capacitor to your existing Capacitor application.

1. Use the following CLI to install Metamap for your Capacitor project.

    ```bash
    npm i @aposnovmati/mati-capacitor-plugin
    ```

1. Build your application.
    ```bash
    ionic build
    ```
1. Update the Capacitor files.
    ```bash
    npx cap sync
    ```

## Add the Metamap Button

Add the Metamap button to your application's HTML and JavaScript files.

`your_index.html`

```html
    <ion-content>
    <ion-button className="matiButtonCss" (click)="showMatiFlow()">Show MatiFlow
    </ion-button>
    </ion-content>
```

 `your_index.ts`

```typescript
import { Component } from '@angular/core';

import { MatiCapacitor } from "@aposnovmati/mati-capacitor-plugin";

@Component({
  selector: 'app-home',
  templateUrl: 'home.page.html',
  styleUrls: ['home.page.scss'],
})
export class HomePage {
  constructor() {}

  showMatiFlow() {
    let metadataParams = { param1: "value1" };
    let registerParams = { clientId: "5c94e3c401ddc6001be83c07", flowId: "5e962a23728ddc001b5937aa", metadata: metadataParams};

    MatiCapacitor.showMatiFlow(registerParams)
      .then( verification => console.log("verification success:" + verification.verificationId))
      .catch(() => console.log("verification cancelled"))
  }
}

```

## Launch for Android

Run the following command to launch the application for Android:
```bash
ionic capacitor run android
```

# Launch for iOS
To launch the application for iOS, you need to do the following:

1. Set minimum iOS version in `capacitor.config.json`
    ```json
     "ios": {
      "minVersion": "11.4"
    }
    ```

1. Launch the application for iOS
    ```bash
    ionic capacitor run ios
    ```
