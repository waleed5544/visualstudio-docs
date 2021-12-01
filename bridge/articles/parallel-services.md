---
title: Debug multiple services at the same time with Bridge to Kubernetes
ms.date: 6/2/2021
description: Learn how to use Bridge to Kubernetes to connect your development computer to a Kubernetes cluster and debug multiple services at the same time with local tunnel debugging, with Visual Studio Code.
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: bridge
ms.custom: "contperf-fy22q1"
ms.topic: how-to
---
# Debug multiple services (VS Code)

Bridge to Kubernetes provides the ability to debug your Kubernetes services in a local environment, as described in [Use Bridge to Kubernetes (VS Code)](bridge-to-kubernetes-vs-code.md). With Bridge to Kubernetes, you redirect traffic to a locally running instance of a service and can debug using VS Code's debugger. However, in some scenarios, you want to work with more than one service and debug into them all at the same time. You can debug multiple services in parallel by following these steps.

## To debug multiple services at the same time

1. Make sure that your services listen on different ports locally. The port numbers are service-specific, so look to the service code to determine what ports it listens on. If multiple services you want to debug listen on the same ports, you won't be able to debug them at the same time.

1. Open the folder corresponding to your first service in VS Code.

1. In VS Code, select **File** > **Add Folder to Workspace…**, and pick the folder corresponding to your other service.

1. Open the Command Palette (**CTRL**+**SHIFT**+**P** or **Cmd**+**Shift**+**P** on a Mac), and run the command **Bridge to Kubernetes: Configure** and, for each of your services, go through the configuration steps.

    > [!WARNING]
    > If you configured your services to run isolated, make sure that they’re using the same **isolateAs** value in their `.vscode/tasks.json` files. This value is the prefix that Bridge to Kubernetes uses to direct traffic for an isolated service. By default, when configuring them, they will have different values. You can choose one of the values and hand-edit the `tasks.json` files for the other services to give them all the same value.
    >
    > ```json
    > "tasks": [
    >    {
    >        "label": "bridge-to-kubernetes.service",
    >        "type": "bridge-to-kubernetes.service",
    >        "service": "service-name",
    >        "ports": [
    >            3000
    >        ],
    >        "isolateAs": "<copy-same-value-for-all-debugged-services>",
    >        "useKubernetesServiceEnvironmentVariables": false
    >    }
    >]
    > ```

1. Set up any breakpoints that you need in each service.

1. Start debugging (**F5**) with Bridge for each of the services by launching the debugger in each service's folder. The previous step created launch configurations for each service, which VS Code's debugger uses when you start the VS Code debugger from that workspace.

## Next steps

Learn more about how Bridge to Kubernetes works at [How Bridge to Kubernetes works](overview-bridge-to-kubernetes.md).
