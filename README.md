# PLASTBAU OPS

Operations app for Plastbau Arabia: job orders, production tracking, store stock, block cutting calculator, shipping, material consumption and printable reports.

The whole app is a single `index.html` file hosted on GitHub Pages. Company data is stored in a **separate private GitHub repository**, never in this one.

## How it fits together

| Repository | Visibility | Contains |
|---|---|---|
| `plastbau-ops` (this one) | Public (needed for free GitHub Pages) | The app only |
| `plastbau-ops-data` | **Private** | `data/Plastbau_OPS_Data.json`, the company data |

Every change made in the app becomes a commit in the private data repository, with the action and the user's name as the commit message. The repository's commit history is a complete, restorable record of every change.

## 1. Publish the app

1. Create a repository, for example `plastbau-ops`, and upload every file in this folder (including `.nojekyll` and `.gitignore`).
2. Open **Settings → Pages → Build and deployment**, choose **Deploy from a branch**, branch **main**, folder **/ (root)**, then **Save**.
3. After a minute or two the app is at `https://<owner>.github.io/plastbau-ops/`.

## 2. Create the private data repository

1. Create a new repository named `plastbau-ops-data` and set it to **Private**. It can start empty; tick **Add a README** so the `main` branch exists.
2. Do not upload anything else. The app creates the data file itself.

The app refuses to connect to a public repository.

## 3. Create an access token (once per person)

On github.com: **Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**

- **Resource owner:** the account or organisation that owns `plastbau-ops-data`
- **Expiration:** a date that suits the trial, for example 90 days
- **Repository access:** Only select repositories → `plastbau-ops-data`
- **Permissions → Repository permissions → Contents:** Read and write

Copy the token (it starts with `github_pat_`). GitHub shows it only once.

For a team, the cleanest set-up is a GitHub organisation that owns the data repository, with each person using their own GitHub account and token. For a short trial, one shared token limited to the data repository also works. Revoke it at the end of the trial.

## 4. Connect the app

1. Open the app and choose **Use GitHub data repository**.
2. Enter the owner, `plastbau-ops-data`, branch `main`, and keep the data file as `data/Plastbau_OPS_Data.json`.
3. Paste the token and choose **Connect to GitHub**.
4. The first time, the app offers to create the data file. The main admin then creates their account, and adds the other users from **Control Panel → Users and authorities**.

Each computer or phone asks for the token once and remembers it in that browser. **Remove the saved token from this computer** on the same screen deletes it.

To move existing trial or OneDrive data to GitHub, sign in as the main admin and use **Control Panel → Data and updates → Move data to GitHub**. The app copies the current data into the new file.

## Working together

- Changes by other users appear automatically within about 20 seconds.
- If two people save at the same moment, the app reloads the latest data and applies the change again, so nothing is overwritten.
- GitHub works in Chrome, Edge, Safari and Firefox, on computers and phones.

## Backups and restoring

- Every save is a commit in `plastbau-ops-data`. To see or recover an older version, open the data file on GitHub and use **History**.
- **Control Panel → Data and updates → Download backup** still saves a full copy to the computer.

## Update the app

Replace `index.html` in this repository and commit. Users get the new version on their next reload. The data repository is not touched.

## Security notes

- Keep `plastbau-ops-data` private at all times.
- Never paste a token into the app files, this repository, emails or chat. Anyone with a token can read and change the data until it expires or is revoked.
- Tokens are stored in the browser of each device. On a shared computer, remove the token after use.
- App sign-in (email and password) controls what each person can do inside the app. The GitHub token controls who can reach the data at all.

---

Plastbau Arabia · Technical Office
