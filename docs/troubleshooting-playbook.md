# Azure Troubleshooting Playbook

A structured workflow for common infrastructure problems in a learning environment.

## 1. Define the symptom

Start by identifying exactly what is failing:

- VM unavailable
- network connection failing
- service reachable from one location but not another
- permission denied
- expected log or metric missing

## 2. Resource state

Confirm the target resource exists, is running, and is in the expected subscription/resource group.

## 3. Network path

Check:

- IP configuration
- subnet placement
- source and destination
- route path
- NSG rules
- protocol and port

Avoid changing multiple controls at once; verify each layer before moving on.

## 4. Guest operating system

If Azure networking appears correct, review the VM itself:

- operating-system firewall
- service status
- listening ports
- local IP settings
- recent configuration changes

## 5. Access control

For authorization problems, verify:

- assigned role
- scope
- inherited permissions
- whether the attempted action is included in the role

## 6. Monitoring

Use Azure Monitor / Log Analytics concepts to compare resource state, metrics, activity, and logs with the time of the reported issue.

## 7. Document and retest

Record the symptom, checks performed, change made, and result after retesting. This prevents troubleshooting from becoming guesswork.

## Evidence boundary

This playbook documents the troubleshooting method practised in lab/coursework. It does not claim production incidents or outcomes that are not preserved in the project material.
