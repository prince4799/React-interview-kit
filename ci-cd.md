[Go back](./Index.md)


# CI/CD Interview Preparation

## 1. Introduction to CI/CD
### What is CI/CD?
- **CI (Continuous Integration)**: Automates the process of integrating code changes into a shared repository multiple times a day.
- **CD (Continuous Deployment/Delivery)**:
  - **Continuous Delivery**: Ensures code is always deployable but requires manual approval for release.
  - **Continuous Deployment**: Fully automates deployment without manual intervention.

### Benefits of CI/CD
- Reduces integration issues
- Automates testing and deployment
- Speeds up software releases
- Improves code quality and reliability

---

## 2. Popular CI/CD Tools
- **Jenkins** – Open-source automation server
- **GitHub Actions** – Built-in CI/CD for GitHub
- **GitLab CI/CD** – Integrated CI/CD in GitLab
- **CircleCI** – Cloud-based CI/CD
- **Travis CI** – CI/CD for open-source projects
- **Bitrise** – Mobile-focused CI/CD (React Native, iOS, Android)
- **Azure DevOps** – Microsoft’s CI/CD solution
- **Fastlane** – Automates mobile app builds and releases

---

## 3. CI/CD Workflow for React & React Native
### Steps to Set Up CI/CD Pipeline
1. **Code Push**: Developers push code to a Git repository.
2. **Build**: CI/CD tool pulls the latest code and installs dependencies.
3. **Testing**: Runs unit tests, integration tests, and UI tests.
4. **Linting & Code Analysis**: Ensures code quality (ESLint, Prettier, SonarQube).
5. **Build & Package**:
   - React: Bundling using Webpack/Vite.
   - React Native: Android (Gradle), iOS (Xcode).
6. **Deployment**:
   - React: Deploy to Vercel, Netlify, Firebase Hosting, AWS.
   - React Native: Deploy to Google Play Store, Apple App Store (via Fastlane/Bitrise).

---

## 4. Common CI/CD Interview Questions
| Question | Answer |
|----------|--------|
| What is the difference between CI and CD? | CI automates code integration & testing. CD automates deployment. |
| How do you set up CI/CD for a React project? | Use GitHub Actions, Jenkins, or GitLab CI to automate builds, tests, and deployments. |
| How do you handle environment variables in CI/CD? | Use `.env` files, GitHub secrets, or environment-specific config files. |
| How does Fastlane help in React Native CI/CD? | Automates builds, signing, and deployment for iOS/Android apps. |
| What are some challenges in CI/CD for mobile apps? | Long build times, signing issues, testing on real devices. |
| How do you integrate automated testing in CI/CD? | Use Jest, React Testing Library, and Detox for automated testing before deployment. |
| What is the role of Docker in CI/CD? | Docker helps in creating consistent environments for builds and deployments. |

---

## 5. CI/CD Best Practices
- **Keep Pipelines Fast**: Optimize test and build times.
- **Use Caching**: Cache dependencies to speed up builds.
- **Fail Fast**: Detect failures early in the pipeline.
- **Implement Automated Rollbacks**: Ensure safe deployments.
- **Monitor Pipelines**: Use logging and alerts to detect issues.

---

## 6. Hands-on Practice
1. **Set up GitHub Actions for a React project**
2. **Deploy a React App to Vercel/Firebase using CI/CD**
3. **Use Fastlane to automate iOS & Android app deployments**
4. **Integrate Jest & Detox in a React Native pipeline**

---

## 7. Resources to Learn More
- [Official GitHub Actions Docs](https://docs.github.com/en/actions)
- [Jenkins CI/CD Guide](https://www.jenkins.io/doc/book/pipeline/)
- [GitLab CI/CD Documentation](https://docs.gitlab.com/ee/ci/)
- [Fastlane Setup for React Native](https://docs.fastlane.tools/getting-started/react-native/)

---

### **Final Tip** 🚀
"Mastering CI/CD is about **hands-on practice**. Set up your own pipeline, debug failures, and optimize the process."

