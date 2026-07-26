# Snapshots and Recovery

## Purpose

Snapshots were created to save a clean version of both virtual machines before performing any security simulations.

If a virtual machine becomes damaged or misconfigured, the snapshot can be used to restore it.

## Snapshots Created

| Virtual Machine | Snapshot Name                    | Status    |
| --------------- | -------------------------------- | --------- |
| Kali Linux      | Kali-Baseline-Network-Ready      | Completed |
| Windows 11      | Windows11-Baseline-Network-Ready | Completed |

## How the Snapshots Were Created

1. Shut down the virtual machine.
2. Selected the virtual machine in VirtualBox.
3. Opened the **Snapshots** section.
4. Clicked **Take Snapshot**.
5. Entered the snapshot name.
6. Confirmed the snapshot was created.

## Recovery Process

To restore a virtual machine:

1. Open VirtualBox.
2. Select the virtual machine.
3. Open the **Snapshots** section.
4. Select the clean snapshot.
5. Click **Restore**.
6. Start the virtual machine and confirm it works.

## Screenshots

```markdown
![Kali Linux snapshot](../screenshots/05-kali-snapshot-created.png)

*Figure 1: Clean Kali Linux snapshot created.*

![Windows 11 snapshot](../screenshots/05-windows11-snapshot-created.png)

*Figure 2: Clean Windows 11 snapshot created.*

![VirtualBox snapshot overview](../screenshots/05-virtualbox-snapshot-overview.png)

*Figure 3: Snapshot overview showing both clean restore points.*
```

## Completion

This step is complete when clean snapshots exist for both Kali Linux and Windows 11.

