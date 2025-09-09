# ㊫ 📖 &nbsp; codebase

<span style='font-size: 1.2em;'>✐ &nbsp; One codebase tracked in revision control, many deploys</span>

## 🍎 study notes

### ✐&nbsp;<span style='color: #FF9900'>Codebase and Repository</span>

A __twelve-factor__ app is always tracked in a version control system, example 
  - Git, 
  - Mercurial, 
  - Subversion or
  - others

A copy of the revision tracking database is known as a <span style='color: #32CD32'>code repository</span>, often referred as <span style='color: #32CD32'>code repo</span> or simply <span style='color: #32CD32'>repo</span>. A codebase is any single repo (such as Subversion) or any set of repos who share a root commit (in a decentralized revision control system like Git).

### ✐&nbsp;<span style='color: #FF9900'>There is always a one-to-one correlation between the codebase and the app</span>
- If there are multiple codebases, it is a <span style='color: #32CD32'>Distributed System</span>. 
- Each component in a distributed system is an <span style='color: #32CD32'>app</span>. 
- Each component / app can embrace the twelve-factor principles separately. 

<!-- notes block -->
<div style='margin-left: 40px; margin-right: 40px; padding-left: 12px; padding: 12px; margin-top: 0.5em; margin-bottom: 0.5em; background: #444;'>
Simply means 1 codebase = 1 app, many app(s) join together to become a distributed system. <br/>
At a point, we can say an app is providing functions on a specific area, whilst a combo of related apps formed the system that chains up the functions.
</div>

- Multiple apps sharing the same code is a violation of twelve-factor. 
- The shared code should have been factored out as libraries which can be included through the dependency manager (e.g. Cargo for RUST, Go-Modules for Golang)

<!-- notes block -->
<div style='margin-left: 40px; margin-right: 40px; padding-left: 12px; padding: 12px; margin-top: 0.5em; margin-bottom: 0.5em; background: #444;'>
take an example, the logging logic could be factored out as a shared library between apps.
</div>
<br/>

### ✐&nbsp;<span style='color: #FF9900'>There is only one codebase per app, but there will be many deploys of the app</span>

A __DEPLOY__ is a __running instance__ of the app. This is typically a production site, and one or more staging sites. Also, every developer has a copy of the app running in their local development environment, each of which also qualifies as a deploy.

<!-- notes block -->
<div style='margin-left: 40px; margin-right: 40px; padding-left: 12px; padding: 12px; margin-top: 0.5em; margin-bottom: 0.5em; background: #444;'>
in general, a running / runnable instance of the app is a deployment; it doesn't need to be production or staging or uat, local running instance is also treated as a deployment.
</div>

The codebase is the same across all deploys, BUT different versions may be active in each deploy. For example, a developer has some commits not yet deployed to staging; staging has some commits not yet deployed to production. But they all share the same codebase, thus making them identifiable as different deploys of the same app.

<!-- notes block -->
<details>
<div style='margin-left: 40px; margin-right: 40px; padding-left: 12px; padding: 12px; margin-top: 0.5em; margin-bottom: 0.5em; background: #444;'>
A more practical use case is when the latest major version of a SAAS is v22.6.1.0; whilst most of the existing customers' deployment is still running the previous major version v22.4.9.13. This is exactly 1 app (same codebase) many deploys (diff versions for diff sets of customers). Ultimately, the remaining set of customers would enjoy the upgrade of their deployment to reach the latest v22.6.1.0
</div>
</details>
<br/>

---

### References
- [twelve factor app - codebase](https://12factor.net/codebase)