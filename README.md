# Exploring CircleCI + GitHub Check

We have the following workflow named `ci` on CircleCI.

`test` and `lint` jobs are the jobs we deemed necessary to pass before any GitHub pull requests (PRs) can be merged.

As a solution, I added a "catch-these-necessary-jobs" surrogate Job named `github_status_checked` that requires `test` and `lint`.
> See [config.yml here](.circleci/config.yml)

<img width="773" alt="Screen Shot 2021-10-07 at 9 49 26" src="https://user-images.githubusercontent.com/2164346/136303291-13f27cd3-04f1-4283-825c-57d7b3886b6b.png">


[Link to actual build on CircleCI](https://app.circleci.com/pipelines/github/kelvintaywl/circleci-github-check-exploration/3/workflows/cc620e08-241d-45d5-b4ae-afb5b7c0e809)

You can also see the branch protection rule on this project's GitHub settings.

> Note that I've used `*` for the branch name pattern; 
> You can adjust this to fit your needs (e.g., `pr/*` if your team has a branch naming convention that all PRs are prefixed with `pr/`)

<img width="1552" alt="Screen Shot 2021-10-07 at 9 53 45" src="https://user-images.githubusercontent.com/2164346/136303551-a6ccea99-e211-4a96-aaf2-e5bc6c440c81.png">

A subsequent PR (#2) reveals that the required `github_status_checked` job on CircleCI passed and therefore is good to merge.

<img width="1552" alt="Screen Shot 2021-10-07 at 9 57 54" src="https://user-images.githubusercontent.com/2164346/136304138-978ec546-b7cb-428c-b74c-3f97bc76e3dc.png">
