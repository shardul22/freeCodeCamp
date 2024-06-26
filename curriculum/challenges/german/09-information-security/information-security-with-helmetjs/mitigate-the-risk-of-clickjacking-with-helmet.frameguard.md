---
id: 587d8247367417b2b2512c38
title: Minimiere das Risiko von Clickjacking mit helmet.frameguard()
challengeType: 2
forumTopicId: 301582
dashedName: mitigate-the-risk-of-clickjacking-with-helmet-frameguard
---

# --description--

As a reminder, this project is being built upon the following starter project on <a href="https://gitpod.io/?autostart=true#https://github.com/freeCodeCamp/boilerplate-infosec/" target="_blank" rel="noopener noreferrer nofollow">Gitpod</a>, or cloned from <a href="https://github.com/freeCodeCamp/boilerplate-infosec/" target="_blank" rel="noopener noreferrer nofollow">GitHub</a>.

Deine Seite könnte ohne deine Zustimmung in ein `<frame>` oder `<iframe>` gesetzt werden. Dies kann unter anderem zu Clickjacking-Attacken führen. Clickjacking is a technique of tricking a user into interacting with a page different from what the user thinks it is. This can be obtained by executing your page in a malicious context, by means of iframing. In diesem Zusammenhang kann ein Hacker eine versteckte Ebene über deine Seite legen. Versteckte Buttons können verwendet werden, um schlechte Skripte auszuführen. This middleware sets the X-Frame-Options header. It restricts who can put your site in a frame. Es gibt drei Modi: DENY, SAMEORIGIN und ALLOW-FROM.

We don’t need our app to be framed.

# --instructions--

Use `helmet.frameguard()` passing with the configuration object `{action: 'deny'}`.

# --hints--

helmet.frameguard() middleware should be mounted correctly

```js
(getUserInput) =>
  $.get(getUserInput('url') + '/_api/app-info').then(
    (data) => {
      assert.include(
        data.appStack,
        'frameguard',
        'helmet.frameguard() middleware is not mounted correctly'
      );
    },
    (xhr) => {
      throw new Error(xhr.responseText);
    }
  );
```

helmet.frameguard() 'action' sollte auf 'DENY' gesetzt werden

```js
(getUserInput) =>
  $.get(getUserInput('url') + '/_api/app-info').then(
    (data) => {
      assert.property(data.headers, 'x-frame-options');
      assert.equal(data.headers['x-frame-options'], 'DENY');
    },
    (xhr) => {
      throw new Error(xhr.responseText);
    }
  );
```

