# Classes

## When to create a class

- New concept: Abtract or real-world
- Low cohesion: Methods should relate
- Promote reuse: Small and targeted = reuse
- Reduce complexity: Solve once and then hide away
- Clarify parameters: Identify a group of data

## High Cohesion

> Low Cohesion

```javascript
class Vehicle {
  editVehicleOptions()
  updatePricing()
  scheduleMaintenance()
  sendMaintenanceReminder()
  selectFinancing()
  calculateMonthlyPayment()
}
```

```typescript
class Vehicle {
  editVehicleOptions();
  updatePricing();
  scheduleMaintenance();
  sendMaintenanceReminder();
  selectFinancing();
  calculateMonthlyPayment();
}
```

> High Cohesion

```javascript
class Vehicle {
  editVehicleOptions()
  updatePricing()
}
class VehicleMaintenance {
  scheduleMaintenance()
  sendMaintenanceReminder()
}
class VehicleFinance {
  selectFinancing()
  calculateMonthlyPayment()
}
```

```typescript
class Vehicle {
  editVehicleOptions();
  updatePricing();
}
class VehicleMaintenance {
  scheduleMaintenance();
  sendMaintenanceReminder();
}
class VehicleFinance {
  selectFinancing();
  calculateMonthlyPayment();
}
```

Classes responsibilties should be strongly related

- Enhances readability
- Increases likehood of reuse
- Avoid attracting lazy programmers

Watch out for

- Methods that don't interact with the rest of the class
- Fields that are only used by one method
- Classes that change often

## Primitive obsession

> Bad example

```javascript
function saveUser({ firstname, lastname, email, state, timezone, gender })
```

```typescript
interface IUser = {
  firstname: string
  lastname: string
  email: string
  state: enum
  timezone: string
  gender: enum
}

function saveUser({ firstname, lastname, email, state, timezone, gender }: IUser);
```

> Good example

```javascript
function saveUser(user)
```

```typescript
interface IUser = {
  firstname: string
  lastname: string
  email: string
  state: enum
  timezone: string
  gender: enum
}
function saveUser(user: IUser)
```

Don't pass too many parameters

- Helps reader conceptualize
- Implicit => explicit
- Encapsulates
- Aids maintenance
