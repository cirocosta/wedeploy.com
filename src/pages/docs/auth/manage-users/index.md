---
title: "Manage Users"
description: "Create, delete or update users by using WeDeploy Auth."
headerTitle: "Auth"
layout: "guide"
weight: 2
---

### {$page.title}

###### {$page.description}

<aside>

If you are unfamiliar with our API, please visit the [API Clients](/docs/intro/api-clients/) page first to learn how to install and configure it.

</aside>

<article id="1">

## Create user

You create a new user in your WeDeploy project by calling the `createUser` method or by signing in a user for the first time using an identity provider such as Google or Facebook.

```javascript
WeDeploy
	.auth('https://<serviceID>-<projectID>.wedeploy.io')
	.createUser({
		email: 'user@domain.com',
		password: 'abc'
	})
	.then(function(user) {
		// Successfully created.
	})
	.catch(function(err) {
		// Not created.
	});
```
```swift
WeDeploy
	.auth('https://<serviceID>-<projectID>.wedeploy.io')
	.createUser(email: "user@domain.com", password: "abc", name: "somename")
	.then { user -> Void in
		// Successfully created.
	}
	.catch { err in
		// Not created.
	}
```
```text/x-java
WeDeploy
	.auth("<auth-url>")
	.createUser("user@domain.com", "password", "somename")
	.execute();
```

</article>

<article id="2">

## Get current user

```javascript
var currentUser = WeDeploy.auth('https://<serviceID>-<projectID>.wedeploy.io').currentUser;

if (currentUser) {
	// User is signed in.
} else {
	// No user is signed in.
}
```
```swift
WeDeploy
	.auth('https://<serviceID>-<projectID>.wedeploy.io')
	.getCurrentUser()
	.then { user -> Void in
		// User found.
	}
	.catch { error in
		// User does not exist.
	}
```
```text/x-java
WeDeploy
	.auth("<auth-url>")
	.getCurrentUser()
	.execute();
```

</article>

<article id="3">

## Get user

```javascript
WeDeploy
	.auth('https://<serviceID>-<projectID>.wedeploy.io')
	.getUser(userId)
	.then(function(user) {
		// User found.
	})
	.catch(function(err) {
		// User does not exist.
	});
```
```swift
WeDeploy
	.auth('https://<serviceID>-<projectID>.wedeploy.io')
	.getUser(id: "userId")
	.then { user -> Void in
		// User found.
	}
	.catch { error in
		// User does not exist.
	}
```
```text/x-java
WeDeploy
	.auth("<auth-url>")
	.getUser("userId")
	.execute();
```

</article>

<article id="4">

## Delete user

```javascript
var currentUser = WeDeploy.auth('https://<serviceID>-<projectID>.wedeploy.io').currentUser;

currentUser
	.deleteUser()
	.then(function() {
		// Successfully deleted.
	})
	.catch(function(err) {
		// Not deleted.
	});
```
```swift
WeDeploy
	.auth('https://<serviceID>-<projectID>.wedeploy.io')
	.deleteUser(id: "userId")
	.then { _ -> Void in
		// Successfully deleted
	}
	.catch { err in
		// Not deleted.
	}
```
```text/x-java
WeDeploy
	.auth("<auth-url>")
	.deleteUser("userId")
	.execute();
```

</article>

<article id="5">

## Update user

```javascript
var currentUser = WeDeploy.auth('https://<serviceID>-<projectID>.wedeploy.io').currentUser;

currentUser
	.updateUser({
		password: "password",
		email: "eleven@hawkinslabs.com",
		name: "Eleven",
		photoUrl: "https://hawkinslabs.com/011/profile.jpg"
	})
	.then(function() {
		// Successfully updated.
	})
	.catch(function(err) {
		// Not updated.
	});
```
```swift
WeDeploy
	.auth('https://<serviceID>-<projectID>.wedeploy.io')
	.updateUser(id: "userId" , email: "eleven@hawkinslabs.com", password: "password", name: "Eleven")
	.then { _ -> Void in
		// Successfully updated
	}
	.catch { err in
		// Not updated.
	}
```
```text/x-java
JSONObject fields = new JSONObject()
	.put("email", "eleven@hawkinslabs.com")
	.put("password", "newPassword")
	.put("name", "Eleven");

WeDeploy
	.auth("<auth-url>")
	.updateUser("userId", fields)
	.execute();
```

</article>

<article id="6">

## Send a password reset email

```javascript
WeDeploy
	.auth('https://<serviceID>-<projectID>.wedeploy.io')
	.sendPasswordResetEmail("user@domain.com")
	.then(function() {
		// Email sent.
	})
	.catch(function(err) {
		// An error happened.
	});
```
```swift
WeDeploy
	.auth('https://<serviceID>-<projectID>.wedeploy.io')
	.sendPasswordReset(email: "user@domain.com")
	.then { _ -> Void in
		// Successfully signed out.
	}
	.catch { err in
		// Not signed out.
	}
```
```text/x-java
WeDeploy
	.auth("<auth-url>")
	.sendPasswordResetEmail("user@domain.com")
	.execute();
```

</article>

<article id="7">

## Sign-out

```javascript
WeDeploy
	.auth('https://<serviceID>-<projectID>.wedeploy.io')
	.signOut()
	.then(function() {
		// User is signed out.
	})
	.catch(function(err) {
		// User was signed out.
	});
```
```swift
WeDeploy
	.auth('https://<serviceID>-<projectID>.wedeploy.io')
	.signOut()
	.then { _ -> Void in
		// Successfully signed out.
	}
	.catch { err in
		// Not signed out.
	}
```
```text/x-java
WeDeploy
	.auth("<auth-url>")
	.signOut()
	.execute();
```

</article>

## What's next?

Learn how to sign-in users using their [email and password](/docs/auth/sign-in-with-password/).
