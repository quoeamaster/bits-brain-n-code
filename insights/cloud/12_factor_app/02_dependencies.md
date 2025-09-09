# ㊫ 📖 &nbsp; dependencies

<span style='font-size: 1.2em;'>✐ &nbsp; Explicitly declare and isolate dependencies</span>

## 🍎 study notes

### ✐&nbsp;<span style='color: #FF9900'>Site-Packages, Vendoring and Bundling</span>

A lot of modern programming languages offer a __<span style='color: #32CD32'>packaging system</span>__ for managing shared libraries.
- RUST - Cargo
- Golang - Go.Modules
- Ruby - RubyGems
- Java - Maven

Depends on the availability of the libraries, they could be categorized as the following:
- system-wide available - __<span style='color: #32CD32'>site-package</span>__ OR
- limited to a scoped environment - __<span style='color: #32CD32'>vendoring</span>__ or __<span style='color: #32CD32'>bundling</span>__

### ✐&nbsp;<span style='color: #FF9900'>dependency management</span>

A twelve-factor app would NOT rely on implicit existence of system-wide packages. Instead a __<span style='color: #32CD32'>dependency manifest</span>__ would declare all dependencies and make sure the build / run process would have the packages ready. The full and explicit dependency specification would be applied to production and development (or any environment) in the same developer experience.

<!-- notes block -->
<details>
    <summary>💡 notes</summary>
    <div style='margin-left: 40px; margin-right: 40px; padding-left: 12px; padding: 12px; margin-top: 0.5em; margin-bottom: 0.5em; background: #444;'>
    Explicit dependency management can make sure the codebase could be built on any OS platform with minimal to no modifications on build configurations. This maximizes the portability and deploy agility.
    </div>
</details>

### ✐&nbsp;<span style='color: #FF9900'>dependency isolation</span>

Certain programming languages provide not just dependency management BUT also dependency isolation. The meaning of __<span style='color: #32CD32'>ISOLATION</span>__ here refers to a running environment in which the runtime would not provide a way to access OS functions to accomplish a task.

Take an example, __<span style='color: #32CD32'>Python</span>__ provides 2 tools to facilitate such. __<span style='color: #32CD32'>pip</span>__ is the tool to manage dependencies and __<span style='color: #32CD32'>virtualenv</span>__ is for isolation.

<!-- notes block -->
<details>
    <summary>💡 notes</summary>
    <div style='margin-left: 40px; margin-right: 40px; padding-left: 12px; padding: 12px; margin-top: 0.5em; margin-bottom: 0.5em; background: #444;'>
    Strictly, dependency management + isolation is a pair to fit the twelve-factor app paradigm; however not every modern programming language does support both; typically dependency management is supported whilst isolation might not be avaiable. Hence an alternative is to battle test your built binary within a Docker container (or k3s / k8s pod) to verify it works as it is.<br/><br/>
    Take an example, if the development workstation is a MAC or Windows PC, we can always choose a Docker image (which is a Linux distribution in general) to run integration tests. If your codebase DOES rely on OS functions; then on the container, such functions might not be available OR they act in a slightly different manner (e.g. the output is different and cause your binary to interprete incorrectly); and ultimately would fail the tests.
    </div>
</details>
<br/>

---

### References
- [twelve factor app - dependencies](https://12factor.net/dependencies)