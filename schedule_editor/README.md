# Schedule Editor

## Main problem

A vehicle’s schedule is defined by a set of trips that occur in an order defined by their sequence number. For example, in the following schedule:

| trip_id | sequence_number | start_location | end_location | payload_kg |
|---------|-----------------|----------------|--------------|------------|
| 1 | 1 | A | B | 10,000
| 2 | 3 | A | C | 8,000
| 3 | 2 | B | A | 0

the vehicle first drives from A to B carrying 10,000kg, then from B to A empty, then finally from A to C carrying 8,000kg.

A valid schedule must always have the start_location of the next trip equal to the end_location of the previous trip (i.e. the vehicle can’t teleport!). For example, the following schedule is not valid:

| trip_id | sequence_number | start_location | end_location | payload_kg |
|---------|-----------------|----------------|--------------|------------|
| 1 | 1 | A | B | 10,000
| 2 | 2 | A | C | 8,000
| 3 | 3 | B | A | 0

Implement a function or class that enables the caller to insert a new trip into a schedule, at any point in the sequence. The schedule after inserting the new trip must be valid! This may require some additional empty (i.e. zero payload) trips to be inserted automatically around the new trip to join up any location discontinuities.


## Optional extension

Now assume that each trip also has an “energy_kWh” field, denoting the electrical energy consumed by the vehicle while completing the trip. A schedule is considered to be feasible if the sum of energy consumed between consecutive visits to charging locations never exceeds the vehicle’s battery capacity. Write a function or class to check if a given schedule is feasible, given a subset of the visited locations that are also charging locations.
