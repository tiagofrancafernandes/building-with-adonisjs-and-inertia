![Adocasts](https://github.com/adocasts/.github/blob/main/assets/brand-banner-rounded.png?raw=true)

# Building with AdonisJS & Inertia

[![YouTube Badge](https://img.shields.io/youtube/channel/subscribers/UCTEKX3KQAJi7_0-_rSz0Edg?logo=YouTube&style=for-the-badge)](https://youtube.com/adocasts)
[![Twitter Badge](https://img.shields.io/twitter/follow/adocasts?logo=twitter&logoColor=white&style=for-the-badge)](https://twitter.com/adocasts)
[![Twitch Badge](https://img.shields.io/twitch/status/adocasts?logo=twitch&logoColor=white&style=for-the-badge)](https://twitch.tv/adocasts)

In this series, we'll learn how to use InertiaJS with AdonisJS 6 to build a feature-complete application, called [PlotMyCourse](https://plotmycourse.app).

🛠️ Our application will use

- AdonisJS (back-end)
- Vue 3 (front-end)
- Inertia (back-end ↔ front-end glue)
- Shadcn-Vue
- Server-Side Rendering (SSR)

🎯 It'll feature

- Organizations
- Org-Level Authorization
- Member Invitations
- Settings Panel
- Drag-And-Drop Ordering
- Plenty Of Forms

👉 [View Building with AdonisJS & Inertia](https://adocasts.com/series/building-with-inertiajs)

---

📑 Documentation
<br/>
[Inertia](https://inertiajs.com/) | [AdonisJS Inertia Adapter](https://docs.adonisjs.com/guides/views-and-templates/inertia)

---

#### Install


### Prerequisites
* **PostgreSQL** &mdash; We use PostgreSQL as our database driver so you'll either want it installed on your machine or a service that provides it.
* **SMTP Provider** &mdash; Locally, we like to use MailTrap
* **Redis Server** &mdash; We now require a Redis connection via [Bentocache](https://bentocache.dev/docs/introduction)
* **Node v20.6+** &mdash; Recommended

### Installation
1. Clone the repository
```sh
git clone https://github.com/adocasts/adocasts.git
```
2. Install NPM packages
```sh
npm i
```
3. Duplicate `.env.example` and rename `.env`
4. Fill out the `.env` variables

### Data
We provide a `StarterSeed` that will populate your database with faker data to populate pages on the Adocasts site.

I haven't tested this yet since our migration from AdonisJS 5 to 6. If you run into any problems, feel free to open an issue.

1. Migrate your database
```sh
node ace migration:run
```
2. _(Optional)_ If you'd like to start fresh (without faker data), open our `StarterSeed` at `database/seeders/StarterSeed.ts` and comment out the `seedUsersAndContent()` call within the run method.
```ts
public async run() {
  const trx = await Database.transaction()

  try {
    await this.seedRoles(trx)

    if (!Application.inTest) {
      // await this.seedUsersAndContent(trx)
    }

    await trx.commit()
  } catch (error) {
    await trx.rollback()
    console.log({ error })
  }
}
```
3. Seed our faker data
```sh
node ace db:seed
```
---

#### Prettier

```sh
./node_modules/prettier/bin/prettier.cjs -w --config ./.prettierrc {database,config,start,resources,app,bin,inertia,tests} *.{ts,js,json}
```

---
---
