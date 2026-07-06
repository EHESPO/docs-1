# GitHub Docs <!-- omit in toc -->

Welcome to GitHub Docs! GitHub’s documentation is open source, meaning anyone from inside or outside the company can contribute. For full contributing guidelines, visit our [contributing guide](https://docs.github.com/en/contributing).


## Quick links by contributor type

* **Hubbers (GitHub employees):** See [CONTRIBUTING.md](https://github.com/github/docs-content/blob/main/CONTRIBUTING.md) in the `docs-content` repository for GitHub-specific processes.

* **Open source contributors:** See [CONTRIBUTING.md](https://github.com/github/docs/blob/main/.github/CONTRIBUTING.md) in the `docs` repository for a quick-start summary.

## How we sync changes across Docs repositories

There are two GitHub Docs repositories: 

- **`github/docs`** (public): Open to external contributions

- **`github/docs-internal`** (private): For GitHub employee contributions. 

The two repositories sync frequently. Content changes in one are reflected in the other.  Hubbers might prefer to post in `docs` when working with a customer, but `docs` has limitations on the types of contributions it accepts to safeguard the site and our workflows. Internal contributions should usually go to `docs-internal`.

**Important:** The `docs` repository accepts contributions to content files (`.md` files in `/content` and select `/data` sections like reusables only). Infrastructure files, workflows, and site-building code are not open for external modification.

## New to contributing

Here are some resources to help you get started with open source contributions:

* [Finding ways to contribute to open source on GitHub](https://docs.github.com/en/get-started/exploring-projects-on-github/finding-ways-to-contribute-to-open-source-on-github)
* [Set up Git](https://docs.github.com/en/get-started/git-basics/set-up-git)
* [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow)
* [Collaborating with pull requests](https://docs.github.com/en/github/collaborating-with-pull-requests)

## License

This project is dual-licensed under:

* **Creative Commons Attribution 4.0** - for documentation and content in the assets, content, and data folders (see [LICENSE](LICENSE))
* **MIT License** - for code (see [LICENSE-CODE](LICENSE-CODE))
. eheps-soc/
│
├── policies/
│   ├── mdm.json
│   ├── email-domains.json
│   ├── users.json
│
├── scripts/
│   ├── validate-policy.js
│   ├── generate-fix.js
│
├── actions/
│   ├── soc-check.yml
│   ├── policy-sync.yml
│
├── soc-server.js
├── README.md

{
  "organization": "EHEPS",
  "domains": ["eheps.org", "eheps.com"],

  "workProfiles": {
    "enabled": true,
    "androidEnterprise": true
  },

  "allowedEmails": [
    "executivedirector@eheps.org",
    "executive@eheps.com",
    "admin@eheps.org"
  ],

  "devicePolicy": {
    "requireScreenLock": true,
    "encryptionRequired": true,
    "workProfileRequired": true
  }
}{
  "primaryProvider": "Google Workspace",
  "domains": [
    "eheps.org",
    "eheps.com"
  ],

  "routingRules": {
    "org": "executivedirector@eheps.org",
    "com": "executive@eheps.com"
  },

  "requiredMX": [
    "aspmx.l.google.com",
    "alt1.aspmx.l.google.com",
    "alt2.aspmx.l.google.com",
    "alt3.aspmx.l.google.com",
    "alt4.aspmx.l.google.com"
  ]
}. 

const fs = require("fs");

const mdm = JSON.parse(fs.readFileSync("./policies/mdm.json"));
const email = JSON.parse(fs.readFileSync("./policies/email-domains.json"));

function validate() {
  const errors = [];

  if (!mdm.workProfiles.enabled) {
    errors.push("MDM Work Profile disabled");
  }

  if (!email.domains.includes("eheps.org")) {
    errors.push("Missing eheps.org domain");
  }

  if (!email.requiredMX.length) {
    errors.push("MX records missing");
  }

  if (errors.length > 0) {
    console.log("❌ POLICY ISSUES:");
    console.log(errors);
    process.exit(1);
  }

  console.log("✅ All SOC policies valid");
}
name: SOC Policy Check

on:
  push:
    paths:
      - "policies/**"

jobs:
  validate:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 18. name: SOC Policy Check

on:
  push:
    paths:
      - "policies/**"

jobs:
  validate:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 18

      - name: Validate SOC Policies
        run: node scripts/validate-policy.jsname: SOC Policy Check

on:
  push:
    paths:
      - "policies/**"

jobs:
  validate:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 18

      - name: Validate SOC Policies
        run: node scripts/validate-policy.js

      - name: Validate SOC Policies
      GitHub policy change
   ↓
SOC detects change
   ↓
Backend triggers Google Workspace Admin API
   ↓
Android Device Policy applies config
   ↓
Work Profile created on device
        run: node scripts/validate-policy.jseheps-enterprise/
│
├── policies/
│   ├── users.json
│   ├── domains.json
│   ├── mdm.json
│
├── provisioning/
│   ├── create-user.js
│   ├── assign-email.js
│   ├── apply-mdm.js
│
├── soc-server.js
├── .env
└── .github/workflows/provision.yml
validate();const { google } = require("googleapis");

async function createUser(auth, user) {
  const admin = google.admin({ version: "directory_v1", auth });

  const res = await admin.users.insert({
    requestBody: {
      primaryEmail: user.email,
      name: {
        givenName: user.firstName,
        familyName: user.lastName
      },
      password: user.password,
      changePasswordAtNextLogin: true
    }
  });

  return res.data;
}

module.exports = { createUser };
