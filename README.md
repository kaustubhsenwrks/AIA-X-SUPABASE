# AIA-X-SUPABASE

🤝 AIALCHEMIST × Supabase: Powering Next-Gen Developer Tools Together

At AIALCHEMIST, we’re not just building tools — we’re nurturing a generation of developers, innovators, and builders. One of our flagship platforms, VeyonPlace, is redefining how student developers learn and collaborate, offering a GitHub-like experience for version control, open-source contributions, and project sharing.

To make this work beautifully, we’ve integrated Supabase into our ecosystem — and it’s been a game-changer.

🛠 How We Use Supabase in AIA Projects

| Tool/Platform      | What it Does                               | How Supabase Helps                               |
| ------------------ | ------------------------------------------ | ------------------------------------------------ |
| VeyonPlace CLI | Lets users push/pull project files via CLI | Stores and versions files using Supabase Storage |
| VeyonPlace API | Handles commits, metadata, auth (Django)   | Communicates with Supabase via REST API          |
| AIA Dashboard  | Web frontend to visualize projects         | Displays files and commit logs using Supabase    |

---

🌟 Why Supabase Felt Like the Perfect Match

We chose Supabase because it aligns with the *developer-first, open-source values* we live by. Here’s what makes it shine for us:

* 🔐 Authentication that’s simple to set up and powerful enough to handle secure collaboration.
* ☁ Storage that scales with our users and keeps every version of every file safe and accessible.
* ⚡ Realtime (in progress) to enable sync notifications and future live collaboration features.
* 🗃 PostgreSQL support that fits right into our existing Django backend with minimal friction.

⚙ Our Integration in 5 Simple Steps

 1. Project Setup on Supabase

We create a new Supabase project, enable:

* Auth
* Storage
* Postgres DB
* Realtime (optional but exciting)

2. Configuring Supabase in Our Tools

In both backend (Django) and frontend (Next.js), we initialize the Supabase client.

bash
npm install @supabase/supabase-js


js
import { createClient } from '@supabase/supabase-js'
const supabase = createClient('<SUPABASE_URL>', '<SUPABASE_ANON_KEY>')


3. Uploading Files via VeyonPlace CLI

Every time a user runs veyon push, files are uploaded to Supabase Storage.

js
await supabase
  .storage
  .from('projects')
  .upload(`/${user}/${repo}/${commitId}/main.py`, fileBlob)
4. Fetching Files on AIA Dashboard

Our frontend retrieves and displays the latest version of any file.

js
await supabase
  .storage
  .from('projects')
  .download(`/${user}/${repo}/${commitId}/main.py`)

 5. Auth That Works for Teams

We use Supabase Auth to manage users and roles across repositories.

js
await supabase.auth.signInWithPassword({
  email: 'user@example.com',
  password: 'supersecurepassword'
})


🧱 Our File Structure on Supabase

plaintext
Bucket: projects
├── /ayushlal/
│   └── /my-portfolio/
│       └── /commit-abc123/
│           └── index.html
│           └── style.css


This makes it super easy to roll back, browse, or share any commit.

🚀 Realtime (Next Phase)

We’re experimenting with Supabase Realtime to enable:

* Live commit updates across teams.
* Real-time alerts when collaborators push changes.
* Collaborative coding (just like multiplayer Google Docs for code!).

🧩 Live Projects Using This Integration

* 🧱 VeyonPlace (Full-stack Git-like platform):
  [github.com/AIALCHEMIST/veyonplace](https://github.com/AIALCHEMIST/veyonplace)

* 🛠 mygit CLI tool (Git CLI reimagined):
  [github.com/AIALCHEMIST/mygit](https://github.com/AIALCHEMIST/mygit)

💬 From Us to You

> “Supabase helped us move fast, stay simple, and scale securely — all while staying open-source. It’s the kind of backend we wish we had in college — so we built it, with Supabase.”
> — Sayman Lal, Founder, AIALCHEMIST

📬 Contact

Want to collaborate, contribute, or know more?

Sayman Lal
Founder, AIALCHEMIST
📧 [aialchemist@ggits.org](mailto:aialchemist@ggits.org)
🌐 [aialchemist.vercel.app](https://aialchemist.vercel.app)
