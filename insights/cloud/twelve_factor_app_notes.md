# ㊫ ✐ &nbsp; Twelve Factor app - study notes

Twelve Factor app is a modern way of design on how your product fits as a __Software-As-A-Service__ app / platform. 

You might ask <span style='color: #32CD32;'>what? would it not be just another web-app?</span>... 

well~ In this study notes, we would dive into the why(s) and how(s) to design for your SAAS product / platform. If you want to know what is philosophy of __twelve factor app__ click [here](#what-is-twelve-factor-app-approach-then).

---

### ? 🧠 ? &nbsp; The big WHY

Let's start with what is __SAAS__

```text
Software as a service is a cloud computing service model in which a provider delivers application software to clients while managing the required physical and software resources. SaaS is usually accessed via a web application. Unlike other software delivery models, it separates "the possession and ownership of software from its use". SaaS use began around 2000, and by 2023 was the main form of software application deployment.
```

Alright, comparing with legacy client-server style web-app; here are the major differences:
- SAAS doesn't sell the source code NOR the binary to the customer, whilst in the old days we used to sell the binary's usage under an agreement (license in general)
- in most cases, SAAS provides application services through 1 major version; which means there is no customer customization. Whilst in the old days, software companies would provide customizations as needed PLUS each customer would need a specific deployment with the customization applied.
- for SAAS, bug fix would be more straightforward as there is, for most cases, only 1 major version / trunk to update the source code. Whilst the traditional way would be applying code patches based on branches (would say the customers' branch with customizations), bug fix could be quite complicated and achievable through bug / feature back-port, patching on customized branch and twisting module logics to fit the branch.

Hm... sounds like __SAAS__ would be a better solution for modern software development after all... To be fair, each software development and deployment approach has its pros and cons, the better answer would be <span style='color: #32CD32'>choose the approach that best fit your use cases.</span>. Take an example, if your environment is air-gapped, developing a SAAS product would be challenging though you can make use of self managed intranet or VPN to overcome the network access part; and obviously to develop a standalone binary would make sense to ease the dev + deployment challenges.

---

### 📖 &nbsp;What is <span style='color: #FF9900'>Twelve Factor App</span> approach then?

In the old days when software products are limited to access the internet (for many reasons, including security concerns), most software are designed to be self-serviced, embrace as a standalone binary and not able to scale. 

In modern days, software is expected to operate on cloud service providers, able to connect to various online services (think about agentic agents asking for information as well as pushing operational actions), can scale up and down based on request traffic. At some point, customers are expecting the software to have limitless resources to process their needs.

Due to these new / expected software features, the core design approaches would need a new set of theories and that is how __Twelve Factor Apps__ emerged.

It is a methodology for building software-as-a-service apps that
- __<span style='color: #32CD32'>DECLARATIVE</span>__ - applying to setup automation. Aim is to minimize time and cost for new developers to join the development. Instead of manual configure the parameters for the source code to run / build, all such information are declared as a config file and not depending on scripts or makefiles.
- __<span style='color: #32CD32'>PORTABILITY</span>__ - reducing underlying operating system's dependencies on code logics (e.g. avoid using OS specific API or features to fulfill a software level function); hence able to maximize portability between different OS platforms.
- __<span style='color: #32CD32'>CLOUD-NATIVE</span>__ - eliminating the needs to manage servers and OS administrations.
- __<span style='color: #32CD32'>INTEGRITY</span>__ - minimize divergence between development and production, as SAAS typically maintains 1 major version instead of multiple branches or revisions hence offering maximum benefits for __Continuous Deployment__.
- __<span style='color: #32CD32'>SCALE</span>__ - able to scale up and down and yet not affecting the infrastructure and development practices.

More importantly, the __twelve-factor__ methodology is not limited to a specific programming language or a set of backing services. That actually grants us lots of freedom on picking the correct programming language as well as the backing services (database, queue, memory cache) to form a sustainable SAAS.

PS. the __twelve-factor__ methodology is written by contributors who have developed, deployed 100s of apps on the [Heroku](http://www.heroku.com/) platform. It is the essence of valued experiences and observations from many wise minds.

As the name depicts, there are 12 areas / disciplines to embrace for a sustainable SAAS, as follows:
- <span style='color: #FF9900'>[codebase](12_factor_app/01_codebase.md)</span> - Only __ONE__ codebase tracked in revision control, but __MANY__ deploys
- <span style='color: #FF9900'>[dependencies](12_factor_app/02_dependencies.md)</span> - Explicitly declare and isolate dependencies, being __DECLARATIVE__
- <span style='color: #FF9900'>config</span> - Store config in the environment (as ENVironment VARiables)
- <span style='color: #FF9900'>backing services</span><!-- - Treat backing services as attached resources -->
- <span style='color: #FF9900'>build, release, run</span><!-- - Strictly separate build and run stages -->
- <span style='color: #FF9900'>processes</span><!-- - Execute the app as one or more stateless processes, making sure the app is Scalable in return -->
- <span style='color: #FF9900'>port binding</span><!-- - Export services via port binding, each process would have its own port and operate independently -->
- <span style='color: #FF9900'>concurrency</span><!-- - Scale out via the process model -->
- <span style='color: #FF9900'>disposability</span><!-- - Able to fast startup and graceful shutdown, for dynamic deployment environment (e.g. k8s) able to quickly provision and remove pods / nodes is a key factor to success -->
- <span style='color: #FF9900'>dev / prod parity</span><!-- - Keep development, staging, and production as similar as possible, avoid unneccessary work on making an environment works -->
- <span style='color: #FF9900'>logs</span><!-- - Treat logs as event streams -->
- <span style='color: #FF9900'>admin processes</span><!-- - Run admin/management tasks as one-off processes -->

Let's get started with the [codebase](12_factor_app/01_codebase.md)

---

### References
- [twelve factor app](https://12factor.net/)
- [SAAS definition](https://en.wikipedia.org/wiki/Software_as_a_service)