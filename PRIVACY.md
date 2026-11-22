# Osmus Privacy Policy

*Last updated: November 22, 2026*

Osmus is an add-in for Autodesk® Revit® developed by Sumer Alhussein ("we", "us"). This policy explains what
information Osmus handles and where it goes.

## What we collect

Nothing. Osmus does not collect, store or send any personal information, project data or usage statistics to us.
There are no accounts, no analytics, no tracking and no advertising. Osmus sends nothing about you or your projects
to anyone else either, unless you ask it to: Silk, a beta feature that is off until you turn it on, sends your
requests to the language model service you choose (see [Silk](#silk-beta-feature) below).

## Data that stays on your computer

Osmus saves these files on your computer only:

- **Settings**: `%AppData%\Osmus\settings.osmus` (automatic updates, beta features, Warden, Colored Tabs, the last
  export profile).
- **Export profiles** you save in the Exports Manager: `Documents\OsmusExportProfiles`.
- **Logs** of exports, updates and errors: `%TEMP%\Osmus\Logs`, deleted after 30 days. They can contain file paths,
  project names and your Revit user name. They never leave your computer unless you choose to attach them to a
  support request.
- **Updates**: downloaded installers in `%TEMP%\OsmusUpdate`, and the updater with its last result in
  `%LocalAppData%\Osmus`.
- **Silk**, once you use it: its settings and the graphs you save in `%AppData%\Osmus\Silk` (the API key you enter is
  kept there, encrypted for your Windows user), the graphs it previews, the records of its runs and its pane's browser
  data in `%LocalAppData%\Osmus\Silk`, and the graphs you open in Dynamo in `Documents\Silk`.

Uninstalling Osmus removes the add-in; you can delete these folders by hand.

## Internet connections

When **Update automatically** is on (the default), Osmus checks for a new version when Revit starts, and when you
click **Check now** in *About*. It asks GitHub for the latest release of Osmus (`api.github.com` and `github.com`)
and, when there is a newer version, downloads it from GitHub and checks it against the published checksum. These
requests contain the Osmus version and nothing about you or your projects. Like any web request, they show your IP
address to GitHub, which handles it under the
[GitHub Privacy Statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement).
You can turn automatic updates off in *About*.

Silk's prompt box connects to the service you set in its settings, only when you send it a request (see below).

The links in Osmus (documentation, releases, issues, email) open in your browser or email program only when you
click them.

If you downloaded Osmus from the Autodesk App Store, Autodesk handles that download under its own privacy statement.

## Silk (beta feature)

Silk is off until you turn on *Enable beta features* in *About* (Revit 2024). Its prompt box sends nothing until you
enter a language model service, with your own API key, in the pane's settings, and agree to send it your requests.

Each request then goes to that service with a summary of the model open in Revit: the model's name, its levels and
their elevations, how many elements of each category it has, and the names of its family types and parameters, with
the titles and descriptions of the graphs saved in your Silk library. Nothing else from the model is sent. The service
answers with a graph, which Silk shows you before anything in the model changes.

The service is the one you chose, under your own account with it: it handles what you send under its own terms and
privacy policy, and we receive none of it. You can withdraw your consent or forget the key in the pane's settings at
any time, or turn beta features off.

For Osmus testers only, Silk also lets AI apps on the same computer use it (through the Model Context Protocol), over
a connection that only your Windows user can open; it is not available to other accounts.

## Support requests

When you email us or open an issue on GitHub, we receive what you send (for example your email address, your message
and any log or file you attach) and use it only to answer you. We do not share it or sell it.

## Children

Osmus is a professional tool for building design and is not directed at children.

## Changes

We may update this policy. The date at the top shows the current version, and important changes are mentioned in the
release notes.

## Contact

Sumer Alhussein, sumer.alhussein@gmail.com
