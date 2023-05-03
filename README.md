![Onify Blueprints](https://files.readme.io/8ba3f14-onify-blueprints-logo.png)

[![Project Status: WIP – Initial development is in progress, but there has not yet been a stable, usable release suitable for the public.](https://www.repostatus.org/badges/latest/wip.svg)](https://www.repostatus.org/#wip)
![Test suite](https://github.com/onify/blueprint-onify-purge-processes/workflows/Test%20suite/badge.svg)

# Onify Blueprint: Purge processes in Onify

This blueprint show how we easy can purge processes in Onify based on process tags (`tag:purge`). It is scheduled to run every 30 minutes. See below for information how to set it up.

![Onify Blueprint: Purge processes in Onify](blueprint.jpg "Blueprint")

## Requirements

* [Onify Hub](https://github.com/onify/install)
* [Camunda Modeler](https://camunda.com/download/modeler/)

## Setup

To start purging processes you first need to start tagging the the process. This can either be done via the workflow where the tags will be inherited to the process once you start a process. Or you can in a process set the tags.

Each process that should be purged needs the following tags:

* `purge` - This is required to be part of the purge process
* `purge:{hours}:{status}` - This is the part where you specify when a process should be purged. `status` is a list of statuses that is separated with a comma.

> Note: The hours is calculated by the enddate. This means that processes missing enddate will not be purged.

### Examples 

* `purge:24:Completed` - Purge process after 24 hours if the status is Completed
* `purge:1:Completed,Stopped` - Purge process after 1 hour if the status is Completed or Stopped
* `purge:168:Stopped` - Purge process after 1 week if the status is Stopped

## Deploy

1. Open the BPMN diagram in Camunda Modeler.
2. Deploy the BPMN diagram (click `Deploy current diagram` and follow the steps).

## Support

* Community/forum: https://support.onify.co/discuss
* Documentation: https://support.onify.co/docs
* Support and SLA: https://support.onify.co/docs/get-support

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.