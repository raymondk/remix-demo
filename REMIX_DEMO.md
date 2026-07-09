# Remix Demo

This repository is setup to show how remixing an app could work.

## User Story

* I'm a user, and I've deployed an application from a market place to my cloud engine.
* I decide I want to tweak my application, so I ask the agent to do it for me.
* Eventually, I might want to pickup updates from the upstream.

## Limitations of the demo

* All the canisters of the app are contained in a single repository.
  * We are making some PoC to make it easier to work with cross project dependencies.
* There is a canister id mapping file in the repo
  * In practice, that file wouldn't be in the repo. We would fetch the canister ids from the canister's environment variables instead. I'm not doing it for this demo to keep things simple.
* The skill doesn't have instructions for picking up changes from the upstream
  * This is a matter of adding instructions (the hard work is going to be for the agent to make it work)

## How it works

* Deployed canisters have metadata attached that tell it the repo and commit they were deployed from.
* There's an agent skill [icp-remix](https://github.com/open-saas-and-aiware/skills) that has instructions for:
  * Fetching the metadata
  * Make sure the identity has permissions to modify the app
  * cloning the repo
  * Making changes and updating the app

## Next Steps

For more complicated project like open-saas, the tooling should have a concept of icp project dependencies. For example, open-hr might depend on open-email. If the tooling understands this, then a similar approach to this poc could be used, except now we might be forking some repos in the repo dependency chain.
