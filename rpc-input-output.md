# RPC and Action Input/Output Evidence

This file lists the RPCs and YANG 1.1 actions implemented for the assignment.
The full schema output is available in:

- `home-automation-3bhk.tree.txt`
- `multi-speciality-hospital-network.tree.txt`

## Home Automation RPCs

```text
rpcs:
  +---x create-home-automation-object
  |  +---w input
  |  |  +---w apartment-id             string
  |  |  +---w controller-ip-address    inet:ip-address
  |  +--ro output
  |     +--ro result?         string
  |     +--ro apartment-id?   string
  +---x get-appliance-status
     +---w input
     |  +---w apartment-id    string
     |  +---w room-id         string
     |  +---w appliance-id    string
     +--ro output
        +--ro status?       appliance-status
        +--ro ip-address?   inet:ip-address
```

## Home Automation Appliance Actions

```text
+---x switch-on
|  +---w input
|  |  +---w requested-by?   string
|  +--ro output
|     +--ro result?   string
|     +--ro status?   appliance-status
+---x switch-off
|  +---w input
|  |  +---w requested-by?   string
|  +--ro output
|     +--ro result?   string
|     +--ro status?   appliance-status
+---x set-fan-speed
|  +---w input
|  |  +---w speed    uint8
|  +--ro output
|     +--ro result?          string
|     +--ro applied-speed?   uint8
+---x set-temperature
|  +---w input
|  |  +---w temperature-celsius    decimal64
|  +--ro output
|     +--ro result?                        string
|     +--ro applied-temperature-celsius?   decimal64
+---x get-status
   +--ro output
      +--ro id?           string
      +--ro status?       appliance-status
      +--ro ip-address?   inet:ip-address
```

## Hospital Network RPCs

```text
rpcs:
  +---x create-hospital-object
  |  +---w input
  |  |  +---w hospital-id              string
  |  |  +---w hospital-name            string
  |  |  +---w controller-ip-address    inet:ip-address
  |  +--ro output
  |     +--ro result?        string
  |     +--ro hospital-id?   string
  +---x register-patient
  |  +---w input
  |  |  +---w hospital-id     string
  |  |  +---w patient-id      string
  |  |  +---w patient-name    string
  |  |  +---w department?     string
  |  +--ro output
  |     +--ro result?       string
  |     +--ro patient-id?   string
  |     +--ro state?        patient-state
  +---x get-patient-details
  |  +---w input
  |  |  +---w hospital-id    string
  |  |  +---w patient-id     string
  |  +--ro output
  |     +--ro patient-id?         string
  |     +--ro patient-name?       string
  |     +--ro state?              patient-state
  |     +--ro assigned-unit-id?   string
  +---x switch-off-unit
  |  +---w input
  |  |  +---w hospital-id    string
  |  |  +---w unit-id        string
  |  |  +---w reason?        string
  |  +--ro output
  |     +--ro result?   string
  |     +--ro status?   unit-status
  +---x get-status
     +---w input
     |  +---w hospital-id    string
     |  +---w unit-id        string
     +--ro output
        +--ro id?           string
        +--ro ip-address?   inet:ip-address
        +--ro status?       unit-status
```

## Hospital Patient Workflow Actions

```text
+---x register-patient
|  +---w input
|  |  +---w patient-id      string
|  |  +---w patient-name    string
|  |  +---w age?            uint8
|  |  +---w department?     string
|  +--ro output
|     +--ro result?       string
|     +--ro patient-id?   string
|     +--ro state?        patient-state
+---x admit-patient
|  +---w input
|  |  +---w patient-id          string
|  |  +---w assigned-unit-id?   string
|  +--ro output
|     +--ro result?   string
|     +--ro state?    patient-state
+---x follow-up-patient
|  +---w input
|  |  +---w patient-id         string
|  |  +---w follow-up-notes?   string
|  +--ro output
|     +--ro result?   string
|     +--ro state?    patient-state
+---x get-patient-details
   +---w input
   |  +---w patient-id    string
   +--ro output
      +--ro patient-id?         string
      +--ro patient-name?       string
      +--ro state?              patient-state
      +--ro assigned-unit-id?   string
```

## Hospital Unit Status Actions

```text
+---x switch-off
|  +---w input
|  |  +---w reason?   string
|  +--ro output
|     +--ro result?   string
|     +--ro status?   unit-status
+---x get-status
   +--ro output
      +--ro id?           string
      +--ro ip-address?   inet:ip-address
      +--ro status?       unit-status
```
