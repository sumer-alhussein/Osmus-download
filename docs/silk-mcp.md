# Silk and AI apps (MCP), for Osmus testers

[Silk](../README.md#silk), a beta feature of Osmus for Revit 2024, can also take its requests from an AI app that
supports the Model Context Protocol (MCP): the app builds the graph with Silk's tools, and you check it and approve it
in the Silk pane, as with the prompt box. This works only for **Osmus testers**: Revit must be signed in with an Osmus
test account. Everyone else uses Silk's prompt box ([Using Silk](../README.md#using-silk)).

## Before you start

- Osmus 2.1.0 or later, in Revit 2024.
- In *About* on the Osmus tab, **Enable beta features** is on, and Revit has been restarted since.
- Revit is signed in with your Osmus test account (an Autodesk account ending in `@smdudin.net`) **before it finishes
  starting**: Silk checks the account when Revit starts. If you sign in later, restart Revit.
- A project is open.

## Add Silk to your AI app

Osmus installs Silk's MCP server, `Silk.Bridge.exe`, next to the add-in. Add it to your AI app as an MCP server the
app starts itself (a *stdio* or *command* server), with no arguments:

| Osmus installed with | Path of `Silk.Bridge.exe` |
|---|---|
| The single-user installer | `%AppData%\Autodesk\Revit\Addins\2024\Osmus\Silk.Bridge.exe` |
| The all-users installer | `C:\ProgramData\Autodesk\Revit\Addins\2024\Osmus\Silk.Bridge.exe` |
| The bundle, for you only | `%AppData%\Autodesk\ApplicationPlugins\Osmus.bundle\Contents\2024\Osmus\Silk.Bridge.exe` |
| The bundle, for all users | `C:\ProgramData\Autodesk\ApplicationPlugins\Osmus.bundle\Contents\2024\Osmus\Silk.Bridge.exe` |

Most AI apps take an entry like this in their MCP settings file. Write the full path, with your own user folder
(settings files do not expand `%AppData%`), and restart the app:

```json
{
  "mcpServers": {
    "silk": {
      "command": "C:\\Users\\<you>\\AppData\\Roaming\\Autodesk\\Revit\\Addins\\2024\\Osmus\\Silk.Bridge.exe"
    }
  }
}
```

VS Code (agent mode) takes the same server in its `mcp.json`, under `"servers"`:

```json
{
  "servers": {
    "silk": {
      "type": "stdio",
      "command": "C:\\Users\\<you>\\AppData\\Roaming\\Autodesk\\Revit\\Addins\\2024\\Osmus\\Silk.Bridge.exe"
    }
  }
}
```

The app can start before or after Revit: Silk's server connects to Revit at the first request, and again if Revit
restarts.

## Check that it works

Ask your AI app to describe the open Revit model with Silk: it calls `silk_model` and answers with the model's levels,
categories, family types and parameters. Then ask it for something, as you would in the prompt box. Silk's tools let
it:

| Tool | What it does |
|---|---|
| `silk_model` | Describes the model open in Revit |
| `silk_catalog`, `silk_node` | Find the nodes Silk builds graphs with |
| `silk_workflows` | List the graphs saved in your Silk library |
| `silk_check` | Compile a graph and report what is wrong with it |
| `silk_preview` | Dry-run a graph and show it in the Silk pane |
| `silk_status` | Say what became of a preview: still waiting for you, applied, discarded, done or failed |

Your AI app cannot change the model: every change waits for you in the Silk pane, where you *Apply* it (one undo step)
or *Discard* it. A graph that acts outside the model (writing a file, isolating elements in a view) runs only when you
approve it.

What Silk tells your AI app (the model summary, and the results of the graphs it previews, such as element names,
parameter values and IDs) goes to that app and to the service behind it, under their own terms.

## More than one Revit open

Silk's server talks to the Revit that started last. To choose another one, add its process ID (shown in the
*Details* tab of Task Manager) to the server's entry: `"env": { "SILK_REVIT_PID": "12345" }`.

## If something goes wrong

| Your AI app reports | What to do |
|---|---|
| *No Revit with Osmus Silk is running* | Start Revit 2024 with beta features on, signed in with your test account, and open a project. If you signed in after Revit started, restart Revit. |
| *Silk's MCP tools are for Osmus test accounts* | Revit has been signed out, or signed in with another account, since it started: sign in with your test account again. |
| *Revit did not answer within 5 minutes* | Revit is busy, or waiting in a dialog: answer the dialog, then ask again. |

## Updates

Osmus installs a downloaded update when Revit closes. Close your AI app first: while it runs `Silk.Bridge.exe`, the
installer cannot replace that file.
