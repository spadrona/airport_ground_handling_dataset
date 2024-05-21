The dataset comprises 10 problem instances designed to emulate busy commercial airports operating with a single runway. 
For reference, we examined airports that handle at least 10 million passengers annually. 

Each problem instance name is defined using the:
- Demand profile: pattern of flight arrival schedules throughout the considered horizon {F,P,FP,PF,PP}
 {F: mostly flat, P: a single peak, FP: a peak in the second half of the horizon, PF: a peak in the first half, PP: two peaks (one in each half)}

- Distribution of operations across services providers (SP) operating at the airport
{E: Even, U: Uneven}

Each problem instance features:

An identical demand level, based on the number of aircraft arrivals undergoing a turnaround within a specified time frame. 
{65 aircraft arrivals within a two-hour period} performed by 5 SPs

idOperation: Identifier for each operation required for aircraft handling during a time frame, considering all involved turnarounds.
name: Name associated to idOperation.
duration: Deterministic time required to complete idOperation.
successors: Direct successors of idOperation.
resourceType: Type of resource required to process idOperation.
SP: Handling company in charge of deliver idOperation.
requiredResourceUnits: Number of units of the resource type required to process idOperation.
consumption: Supply/pick up requirements of idOperation
IdTurnaround: Identifier for the turnaround to which idOperation belongs.
SIBT/TIBT: Earliest start time for idOperation based on the known SIBT/TIBT of the corresponding turnaround
SOBT/TOBT: Latest start time for idOperation based on the known SIBT/TIBT of the corresponding turnaround
idStand: Identifier for the stand where idOperation is perfomed

Traveling time instance:
Deterministic time in minutes, required to move between two stands, with the first stand corresponding to the depot 

Time variability definition:
sibt: sibt + gamma(shape = 4.8, scale = 1.4, thresh = −5)
duration/refilling: triangular(duration*(1 − φl), duration, duration*(1 + φu))
φmediuml = 0.1, φmediumu = 0.3, φhighl = 0.2, φhighu = 0.6
travellingTime: travellingTime + expo(travellingTime*φ), φmedium = 0.3, φhigh = 0.6

Capacitated resources: 100
