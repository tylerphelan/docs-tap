# Install Developer Conventions

This document describes how to install Developer Conventions
from the Tanzu Application Platform package repository.

>**Note:** Use the instructions on this page if you do not want to use a profile to install packages.
Both the full and light profiles include Developer Conventions.
For more information about profiles, see [Installing the Tanzu Application Platform Package and Profiles](../install.md).

## <a id='dc-prereqs'></a>Prerequisites

Before installing Developer Conventions:

- Complete all prerequisites to install Tanzu Application Platform. For more information, see [Prerequisites](../prerequisites.md).
- Install [Convention Service](../convention-service/install-conv-serv.md).

## <a id='dc-install'></a>Install

To install Developer Conventions:

1. Get the exact name and version information for the Developer Conventions package to be installed
by running:

    ```
    tanzu package available list developer-conventions.tanzu.vmware.com --namespace tap-install
    ```

    For example:

    ```
    $ tanzu package available list developer-conventions.tanzu.vmware.com --namespace tap-install
    - Retrieving package versions for developer-conventions.tanzu.vmware.com
      NAME                                    VERSION        RELEASED-AT
      developer-conventions.tanzu.vmware.com  0.3.0          2021-10-19T00:00:00Z
    ```

1. Install the package by running:

    ```
    tanzu package install developer-conventions \
      --package-name developer-conventions.tanzu.vmware.com \
      --version 0.3.0 \
      --namespace tap-install
    ```

1. Verify the package install by running:

    ```
    tanzu package installed get developer-conventions --namespace tap-install
    ```

    For example:

    ```
    tanzu package installed get developer-conventions -n tap-install
    | Retrieving installation details for developer-conventions...
    NAME:                    developer-conventions
    PACKAGE-NAME:            developer-conventions.tanzu.vmware.com
    PACKAGE-VERSION:         0.3.0
    STATUS:                  Reconcile succeeded
    CONDITIONS:              [{ReconcileSucceeded True  }]
    USEFUL-ERROR-MESSAGE:
    ```

    Verify that `STATUS` is `Reconcile succeeded`
