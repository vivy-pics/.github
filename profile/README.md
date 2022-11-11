<p align="center">
<img alt="full" src="https://github.com/vivy-pics/branding/raw/master/full.svg"/>
<h3 align="center">What does it mean to put your heart into something?</h3>
</p>

---

VIVY is a image board in the vein of [Danbooru](https://github.com/danbooru/danbooru) whilst being
pretty, rather than the current styles of boards which look dated. It's also an experiment, utilising
newer technology such as Cloudflare's R2 and Pages, and EdgeDB.

## Etymology
VIVY's name comes from... [Vivy](https://en.wikipedia.org/wiki/Vivy:_Fluorite_Eye%27s_Song)! It is an
absolutely *fantastic* anime and you should go watch it! Right now. Now. Watch it now. Go watch Vivy.

## Infrastructure
VIVY is heavily powered by Cloudflare infrastructure - it uses R2 for CDN and Pages for frontend. On
the backend side of things, it uses Fastify as a web server (with Typebox to provide full schema and
type safety) and EdgeDB as a database, chosen for its graph model since many objects link together.
The backend is not hosted on Cloudflare (which is the only bit that Cloudflare isn't involved in!).

## Self-Hosting
:warning: There is **no official support** for self-hosted instances. We may give support from time to
time for setup, but VIVY will never officially support self-hosted and makes no guarantees that your
setup today will work tomorrow.

### Storage
VIVY should, in theory, be compatible with any S3 service, including - but not limited to - Cloudflare
R2 (what it was primarily designed for), AWS S3, Wasabi, and Backblaze B2. This also includes
self-hosted S3 alternatives, which means, once again in theory, that you can make VIVY completely locally
hosted.

### Frontend
The frontend can compile to [anything SvelteKit supports](https://kit.svelte.dev/docs/adapters) (except
static) which permits it to run on a variety of infrastructure. There should be no problems here.

### Backend
The backend is a standard Node.js application, so it'll run anywhere that isn't a serverless environment.
It's recommended to use `pm2` to manage the backend and to cluster it for performance. You will also need
to install [EdgeDB](https://www.edgedb.com/install) and create an instance, run migrations, then put your
connection info into the environment.
