# bmh-label-controller

This ansible-based controller demonstrates how you can easily add labels to
BareMetalHost resources based on inspecting arbitrary hardware attributes.
You can make your own similar controller, and then use Ansible's ability to
form expressions that are as simple or complex as your needs demand.

## Use Case

When managing BareMetalHosts, it can be useful to label or annotate the hosts based on
your organization's custom policies or procedures. A controller is a handy
way to automate that labeling, and using Ansible gives you a quick and easy
path to creating your own controller with custom labeling logic.

## How it Works

Check out the [tasks file](roles/baremetalhost/tasks/main.yml), which
includes all of the logic. It contains several examples of how you could
label hosts based on their attributes.

## How to Make Your Own

These are the rough steps I took. I threw together this PoC quickly, but it
does work when run locally via `operator-sdk run --local`.

* Use operator-sdk to create a new ansible-based operator. Make up any GVK for the required parameters.
* Change the [`watches.yaml`](watches.yaml) file to look exactly like this one.
* Delete `deploy/crds`.
* Edit the [tasks file](roles/baremetalhost/tasks/main.yml) to to add logic for appling labels and/or annotations.