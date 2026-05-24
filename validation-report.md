# Assignment 4 - Unit 5 Validation Report

## Files Created

- `home-automation-3bhk.yang`
- `multi-speciality-hospital-network.yang`
- `home-automation-3bhk.tree.txt`
- `multi-speciality-hospital-network.tree.txt`
- `home-automation-3bhk.html`
- `multi-speciality-hospital-network.html`
- `rpc-input-output.md`

## Pyang Validation

The following commands were executed from this folder:

```powershell
python -m pyang home-automation-3bhk.yang
python -m pyang multi-speciality-hospital-network.yang
```

Result:

```text
home-automation-3bhk.yang: PASS, no pyang errors
multi-speciality-hospital-network.yang: PASS, no pyang errors
```

## Tree View Generation

```powershell
python -m pyang -f tree -o home-automation-3bhk.tree.txt home-automation-3bhk.yang
python -m pyang -f tree -o multi-speciality-hospital-network.tree.txt multi-speciality-hospital-network.yang
```

Result:

```text
home-automation-3bhk.tree.txt generated
multi-speciality-hospital-network.tree.txt generated
```

## HTML View Generation

```powershell
python -m pyang -f jstree -o home-automation-3bhk.html home-automation-3bhk.yang
python -m pyang -f jstree -o multi-speciality-hospital-network.html multi-speciality-hospital-network.yang
```

Result:

```text
home-automation-3bhk.html generated
multi-speciality-hospital-network.html generated
```

## Assignment Coverage

Home Automation:

- Creates a `home-automation` object with configurable 3 BHK apartment instances.
- Supports configurable rooms, rest-rooms, kitchen, and appliance instances.
- Models appliance ID, IP address, status, type, fan speed, target temperature, and power consumption.
- Allows create/delete of rooms and appliances through configurable YANG lists.
- Provides instance actions: `switch-on`, `switch-off`, `set-fan-speed`, `set-temperature`, and `get-status`.
- Provides top-level RPCs: `create-home-automation-object` and `get-appliance-status`.
- Uses common YANG type `inet:ip-address` from `ietf-inet-types`.

Hospital Network:

- Creates a `hospital-network` object with configurable hospital instances.
- Models IP wards, operation theatre, ICU, ambulances, OP ward, emergency ward, reception, pharmacy, canteen, and patients.
- Models ward type and facilities, with a `must` rule linking bed count to ward type.
- Provides patient workflow actions: `register-patient`, `admit-patient`, `follow-up-patient`, and `get-patient-details`.
- Provides status actions: `switch-off` and `get-status`.
- Provides top-level RPCs: `create-hospital-object`, `register-patient`, `get-patient-details`, `switch-off-unit`, and `get-status`.
- Uses common YANG type `inet:ip-address` from `ietf-inet-types`.
