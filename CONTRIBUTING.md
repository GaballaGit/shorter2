# Getting Started
This app requires more setup to run locally than a traditional web app due to Discord applications needing a public endpoint. For local testing, we must create a new application with Discord and use a tool like ngrok to create an HTTP tunnel between our local dev server and a public endpoint.
>[!Important]
> Make sure you have Bun and ngrok installed.

1. Create a discord application for development on the [Discord Developer Dashboard](https://discord.com/developers/applications) (you can call it `shorter-dev` or something similar):<img width="1910" height="996" alt="image" src="https://github.com/user-attachments/assets/6975c999-c6e3-4c43-a3e3-4e8aa94cda3b" />



    1. After creating your app, copy your **Public Key** and **Application ID** and save them somewhere safe.<img width="1919" height="792" alt="image" src="https://github.com/user-attachments/assets/9b491464-a33f-43dc-8ad8-d279f3d18e9d" />

    1. Go to the *Bot* tab and copy your **token**, again storing it somewhere safe.<img width="1882" height="885" alt="image" src="https://github.com/user-attachments/assets/13cd9a41-edc1-40a2-8f34-ef78ee17b4e9" />

    1. Go to the *OAuth2* tab, choose the **URL Generator**, and click the **bot** and **application.commands** scopes.<img width="1888" height="892" alt="image" src="https://github.com/user-attachments/assets/6fdb4b38-cd81-486b-8ae3-f3a45d281864" />

    1. Select **Send Messages** and **Use Slash Commands** in *Bot Permissions*, then copy the *Generated URL* at the bottom of the page.<img width="1887" height="991" alt="image" src="https://github.com/user-attachments/assets/db175845-2dcd-4700-a6f9-940c4b988616" />

    1. Paste the URL into your browser, follow the OAuth flow, and invite the bot to a server where you'd like to test it.

1. `cd` into the bot package directory.
1. Create a local `.dev.vars` file by running `cp .dev.vars.example .dev.vars` and paste your newly obtained credentials into it. You can ignore the `SHORTER_API_KEY` variable for now.
> [!NOTE]
> `DISCORD_GUILD_ID` is the Server ID of the server you invited shorter bot to. Right click the server and head down to Copy Server ID to retrieve it.
>
> <img width="239" height="535" alt="image" src="https://github.com/user-attachments/assets/8c6c520e-7772-4ba2-82e8-7a76a9874fd6" />
1. Run `bun run register` to register the app's commands with Discord.
1. Start a local dev server and create an HTTP tunnel with ngrok:

    1. Run `bun run tunnel` and follow the link to create an ngrok account and authenticate the `ngrok` CLI.
    > If you've used ngrok prior and/or already have it configured, you can skip the above step.
    1. Run `bun run dev` to start a local dev server on `localhost:8787`.
    1. Run `bun run tunnel` in a different terminal, this time it should display a public URL that forwards the dev server you started in the previous step.
    1. Visit the URL in your browser. If you did everything correctly, you should see the message `Hi!`.

1. Paste the ngrok URL into the *Interactions Endpoint URL* field back on the Discord Developer Dashboard.
1. `cd` into the service package directory.
1. Run `bun run dev` in a third terminal to start a local dev server on `localhost:8788`.


# Submitting a PR


## References
- [Official Discord + Cloudflare Workers tutorial](https://discord.com/developers/docs/tutorials/hosting-on-cloudflare-workers)
- [Discord developer docs](https://discord.dev)
- [ngrok dashboard](https://dashboard.ngrok.com/get-started/setup/linux)
