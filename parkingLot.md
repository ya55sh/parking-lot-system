# 1 VEHICLE

Handles vehicle-specific data and behaviors.

## PROPERTIES:

-plateNumber
-type (TWO_WHEELER, BUS, 4 WHEELER)
-vehicleID (INTERNAL ID)

## METHODS:

-getVehicleId()
-getType()
-getPlateNumber()

# 2 PARKING SPOT

Represents an individual parking spot.

## Properties:

-spotId
-spotType (e.g., COMPACT, LARGE, BIKE)
-isOccupied
-levelId
-currentVehicleId

## Methods:

-isAvailable()
-assignVehicle(vehicle)
-removeVehicle()
-getSpotType()

# 3 LEVEL

Represents a parking level in the lot.

## Properties:

-levelId
-spots[] (array of ParkingSpot)

## Methods:

-findAvailableSpot(vehicleType)
-getAvailableSpotCount()

# 4 PARKINGLOT

Manages the entire parking lot system.

## Properties:

-levels[]
-lotId

## Methods:

-assignSpot(vehicle)
-releaseSpot(ticketId)
-getRealTimeAvailability()
-getLotStatus()

# 5 TICKET

Handles ticket generation and time tracking.

## Properties:

-ticketId
-vehicleId
-spotId
-entryTime
-exitTime (nullable until checkout)
-levelId

## Methods:

-generateTicket(vehicle, spot)
-closeTicket(exitTime)
-getDuration()

# 6 PAYMENT

Handles fee calculation and transaction logic.

## Properties:

-rateChart (based on vehicle type)
-ticketId
-amount

## Methods:

-calculateFee(ticket)
-processPayment(ticket)
-getReceipt()

# 7 GATE CONTROLLER

Simulates entry/exit gate logic.

## Entry Methods:

-onVehicleEntry(vehicle)
-Finds spot
-Issues ticket
-Updates real-time availability

## Exit Methods:

-onVehicleExit(ticketId)
-Records exit time
-Calculates fee
-Frees up spot

# 8 AVAILABLILITY SERVICE

## Methods:

-updateAvailability(levelId, spotId, isOccupied)
-getAvailabilityByLevel()
-getOverallAvailability()

# 9

Core logic for allocating the best available spot based on type.

## Methods:

-allocateSpot(vehicleType)
-releaseSpot(spotId)
-optimizeAllocation() (optional: for intelligent spot distribution)
