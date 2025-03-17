---
title: Developer Dashboard Node/Express Configuration
description: Recipe Description
hidden: false
recipe:
  color: '#018FF4'
  icon: 🦉
---
```javascript JavaScript
const readme = require("readmeio").auth("apikey");

const getUserByEmail = (userEmail) => {
  return users.find({ email: userEmail });
};

const getUserByAPIKey = (userAPIKey) => {
  return users.find({ apiKey: userAPIKey });
};

router.use(
  readme(async (req, getUser) => {
    const user = await getUser({
      byEmail: getUserByEmail,
      byAPIKey: getUserByAPIKey,
    });

    return {
      name: user.name,
      email: user.email,

      apiKeys: [{
        label: `${user.name}'s API Key`,
        apiKey: user.apiKey
      }]
    };
  })
);

```

```json Response Example
{"success":true}
```

# 1. getUser function

<!-- javascript@ -->

ReadMe will provide a getUser function that takes two parameters, byEmail and byAPIKey. You should provide a function to each that returns a user in your system fetched by those two methods. This way whenever the middleware is hit ReadMe will be able to successfully find the user.

# 2. Fetch User via Email

<!-- javascript@ -->

When a user logs into ReadMe we'll make a request with their email address to get more information. This allows us to show their API Logs and API Keys directly in the documentation.

# 3. Fetch User via API Key

<!-- javascript@ -->



# 4. Return User

<!-- javascript@ -->

