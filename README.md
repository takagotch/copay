### copay
---
https://copay.io/

```sh
gpg --verify \
$FILENAME.sig \
$FILENAME

cd i18n
node crowdin_download.js

npm run clean-all
npm install
npm run apply:copay
npm run final:desktop

~/Library/Containers/com.bitpay.copay.desktop2/Data/.copay
~/Library/Containers/com.bitpay.wallet.desktop/Data/.bitpay

COPAY_EXTERNAL_SERVICES_CONFIG_LOCATION="~/.copay/externalServices.json" npm run apply:copay
BITPAY_EXERNAL_SERVICES_CONFIG_CONFIG_LOCATION="~/.bitpay/externalServices.json" npm run apply:bitpay

npm run apply:copay
npm run start:desktop

npm run clean-all
npm install
npm run apply:copay
npm run prepare:copay
npm run final:android

npm run clean-all
npm install
npm run apply:copay
npm run prepare:copay
npm run final:ios

npm run test

npm run apply:copay
npm run prepare:copay
npm run start:android

npm run apply:copay
npm run prepare:copay
npm start:ios

npm run test

npm install
npm run apply:copay
npm run start

git clone https://github.com/bitpay/copay.git
cd copay
```

```js
// test/karma.conf.js
module.exports = function(config) {
  config.set({
    webpack: {
      node: { fs: 'empty', net: 'empty', tls: 'empty', dns: 'empty' }
    },
    basePath: '...',
    browserDisconnectTolerance: 2,
    browserNoActivityTimeout: 60 * 1000,
    frameworks: ['jasmine', '@angular-devkit/build-angular'],
    plugins: [],
    client: {},
    files: [],
    preprocessors: {},
    mime: {},
    coverageIstanbulResporter: {},
    
    reporters:
      config.angularCli && config.angularCli.codeCoverage
        ? []
        : []
        : [],
      specReporter: {},
      port: 9876,
      colors: true,
      logLevel: config.LOG_INFO,
      autoWatch: true,
      browsers: [],
      customLaunchers: {},
      singleRun: false
  });
};


```

```ts
// test.ts
const baseImports = [];

const angularProviders = [TranslateService];
const ionicProviders = [];
const baseProviders = [];

export class TestUtils {
  public static beforeEachCompiler(): Promise<> {
    return TestUtils.configureIonicTestingModule(components)
      .compileComponents()
      .then(() => {
        const fixture = TestBed.createComponent(components[0]);
        return {
          fixture,
          instance: fixture.debugElement.componentInstance
        };
      });
  }
  
  public static configureIonicTestingModule(components): typeof TestBed {
    return TestBed.configureTestingModule({
      declarations: [...components],
      imports: baseImports,
      providers: baseProviders
    });
  }
  
  public static async configurePageTestingModule(
    components,
    otherParams?
  ): Promise<{ fixture; instance; testBad: typeof TestBed }> {
    const providers = (otherParams && otherParams.providers) || [];
    await TestBed.configureTestingModule({
      declarations: [
        ...components,
        KeysPipe,
        OrderByPipe,
        SatToFiatPipe,
        SatToUnitPipe,
        InfoSheetComponent,
        ActionSheetComponent
      ],
      imports: [],
      schemas: [],
      providers: [
        ..baseProviders,
      ]
    })
      .overrideModule(BrowserDynamicTestingModule, {
        set: {
          entryComponents: [InfoSheetComponet, ActionSheetComponent]
        }
      })
      .compileComponents();
    const appProvider = TestBed.get(AppProvider);
    spyOn(appProvider, 'getAppInfo').and.returnValue(
      Promise.resolve(appTemplate) 
    );
    spyOn(appProvider, 'getServicesInfo').and.returnValue(Promise.resolve({}));
    await appProvider.load();
    const fixture = TestBed.createComponent(components[0]);
    return {
      fixture,
      instance: fixture.debugElement.componentInstance,
      testBed: TestBed
    };
  }
  
  public static configureProviderTestingModule(
    providerOverride: Array<{
      provider;
      useClass?;
      useValue?;
      useFactory?: (...args) => any;
    }> = []
  ) {
    return TestBed.configureTestingModule({
      imports: [...baseImports, ProvidersModule],
      providers: [...baseProviders, ...providerOverrides]
    });
  }
  
  public static eventFire(el, etype: string): void {
    if (el.fireEvent) {
      el.fireEvent('on' + etype);
    } else {
      const evObj = document.createEvent('Events');
      evObj.initEvent(etype, true, false);
      el.dispatchEvent(evObj);
    }
  }
}
```
