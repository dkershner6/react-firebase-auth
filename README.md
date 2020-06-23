# react-hooks-firebase-auth

Library for easy handling of Firebase Authentication, complete with provider token related events

![NPM Publish](https://github.com/dkershner6/react-hooks-firebase-auth/workflows/Merging%20to%20Master/badge.svg)

## Sample Provider Use

```typescript
const CompleteFirebaseAuthProvider = ({ children }): ReactElement => {
    return (
        <FirebaseAuthProvider
            appName="app"
            firebase={firebase}
            loginComponent={<Login />}
            loadingComponent={
                <Loading
                    progress={30}
                    variant="warning"
                    message="Logging you in..."
                />
            }
            errorComponent={<p>Error</p>}
            onNewLoginSuccess={onNewLoginSuccess}
            onLogout={onLogout}
            onOldLoginRetrieval={onOldLoginRetrieval}
        >
            {children}
        </FirebaseAuthProvider>
    );
};
```

And then for your main app file...

```typescript
<CompleteFirebaseAuthProvider>
    <App />
</CompleteFirebaseAuthProvider>
```

## Sample Container use

```typescript
import { useContainer } from 'unstated-next';
import { FirebaseAuthContainer } from 'react-hooks-firebase-auth';

const Component = () => {
    const { user, token } = useContainer(FirebaseAuthContainer);
};
```

## Sample Auth Enforcement

```typescript
import { EnforceFirebaseAuth } from 'react-hooks-firebase-auth';

const Component = () => {
    return (
        <EnforceFirebaseAuth>
            <AnotherComponent />
        </EnforceFirebaseAuth>
    );
};
```

OR

```typescript
import { withFirebaseAuth } from 'react-hooks-firebase-auth';

const Component = () => {
    return <AnotherComponent />;
};

export default withFirebaseAuth(Component);
```
