# oauth2-oidc-w3id

oauth2-oidc-w3id is an OAuth2 and OpenId Connect (OIDC) client for Angular. The library is a Github fork of [manfredsteyer/angular-oauth2-oidc](https://github.com/manfredsteyer/angular-oauth2-oidc).

This library extends to support:
- Emits fetch id token event `fetch_token` before request to /token endpoint

## Installing

```
npm i oauth2-oidc-w3id --save
```

## Configuring for Code Flow

```TypeScript
import { AuthConfig } from 'angular-oauth2-oidc';

export const authConfig: AuthConfig = {
  ...
  responseType: 'code',
  // config support PKCE or not 
  disablePKCE: true
  ...
}
```

## Subscribe fetch token event:

```TypeScript
constructor(private oauthService: OAuthService) {
    this.oauthService.configure(authConf);
    this.oauthService.tokenValidationHandler = new JwksValidationHandler();

    this.oauthService.events.pipe(
        map((event: OAuthEvent) => event.type)
    ).subscribe(type => {
        if (type === 'fetch_token') {
            // do something before requet token endpoint
        }
    });
}
```

## More Documentation (!)
See the [original project documentation](https://manfredsteyer.github.io/angular-oauth2-oidc/docs/) for more information about this library.


## build library
1. `npm run package`

## publish to npm
1. `npm login`
2. `npm publish ./dist/lib/oauth2-oidc-w3id-[version].tgz`

## upadate package to npm
1. update version in `./projects/lib/package.json`
2. delete ./dist folder
3. `npm run package`
4. `npm publish ./dist/lib/oauth2-oidc-w3id-[version].tgz`








