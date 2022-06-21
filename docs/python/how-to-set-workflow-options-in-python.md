---
id: how-to-set-workflow-options-in-python
title: How to set Workflow options in Python
sidebar_label: Set Workflow options
description: Set Workflow options
tags:
  - developer-guide
  - sdk
  - python
---

Create the following script at `start_workflow.py`:

```python
async def main():
    # Create client connected to server at the given address
    client = await Client.connect("http://localhost:7233")

    # Start a workflow
    handle = await client.start_workflow(
        "your workflow name",
        "some arg",
        id="your-workflow-id",
        task_queue="your-task-queue",
    )

    print(f"Workflow started with ID {handle.id}")


if __name__ == "__main__":
    asyncio.run(main())
```

Assuming you have a Temporal server running on localhost, this
will start a workflow:

```bash
python start_workflow.py
```

An external Worker has to be started with this Workflow registered to actually run the Workflow.