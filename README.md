# Cancelations_Prediction

## Business Situation

To reduce the uncertainty about demand, Michael wants to implement prediction
models to allow the chain’s hotels to forecast net demand based on
reservations on-the-books. With these models' estimations, Michael expects to
implement better pricing and overbooking policies and identify bookings with
high likelihood of canceling.

## Metadata

| Name                        | Meaning                                                                                                                                                                                                                                                          |
|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ADR                         | Average Daily Rate                                                                                                                                                                                                                                               |
| Adults                      | Number of adults                                                                                                                                                                                                                                                 |
| Agent                       | ID of the travel agency that made the booking                                                                                                                                                                                                                    |
| ArrivalDateDayOfMonth       | Day of the month of the arrival date                                                                                                                                                                                                                             |
| ArrivalDateMonth            | Month of arrival date with 12 categories:  “January” to “December”                                                                                                                                                                                               |
| ArrivalDateWeekNumber       | Week number of the arrival date                                                                                                                                                                                                                                  |
| ArrivalDateYear             | Year of the arrival date                                                                                                                                                                                                                                         |
| AssignedRoomType            | Code for the type of room assigned to the booking. Sometimes the assigned room type differs from the reserved room type due to hotel operation reasons (e.g. overbooking) or by customer request. Code is presented instead of designation for anonymity reasons |
| Babies                      | Number of babies                                                                                                                                                                                                                                                 |
| BookingChanges              | Number of changes/amendments made to the booking from the moment the booking was entered on the PMS until the moment of check-in or cancellation                                                                                                                 |
| Children                    | Number of children                                                                                                                                                                                                                                               |
| Company                     | ID of the company/entity that made the booking or responsible for paying the booking. ID is presented instead of designation for anonymity reasons                                                                                                               |
| Country                     | Country of origin. Categories are represented in the ISO 3155-3:2013 format                                                                                                                                                                                      |
| CustomerType                | Type of booking, assuming one of four possible categories (presented below)                                                                                                                                                                                      |
| DaysInWaitingList           | Number of days the booking was in the waiting list before it was confirmed to the customer                                                                                                                                                                       |
| DepositType                 | Indication on if the customer made a deposit to guarantee the booking. This variable can assume three categories (presented)                                                                                                                                     |
| DistributionChannel         | Booking distribution channel. The term “TA” means “Travel Agents” and “TO” means “Tour Operators”                                                                                                                                                                |
| IsCanceled                  | Value indicating if the booking was canceled (1) or not (0)                                                                                                                                                                                                      |
| IsRepeatedGuest             | Value indicating if the booking name was from a repeated guest (1) or not (0)                                                                                                                                                                                    |
| LeadTime                    | Number of days that elapsed between the entering date of the booking into the PMS and the arrival date                                                                                                                                                           |
| MarketSegment               | Market segment designation. In categories, the term “TA” means “Travel Agents” and “TO” means “Tour Operators”                                                                                                                                                   |
| Meal                        | Type of meal booked. Categories are presented in standard hospitality meal packages (presented below)                                                                                                                                                            |
| PreviousBookingsNotCanceled | Number of previous bookings not cancelled by the customer prior to the current booking                                                                                                                                                                           |
| PreviousCancellations       | Number of previous bookings that were cancelled by the customer prior to the current booking                                                                                                                                                                     |
| RequiredCarParkingSpaces    | Number of car parking spaces required by the customer                                                                                                                                                                                                            |
| ReservationStatus           | Reservation last status, assuming one of three categories (presented below)                                                                                                                                                                                      |
| ReservationStatusDate       | Date at which the last status was set. This variable can be used in conjunction with the ReservationStatus to understand when was the booking canceled or when did the customer checked-out of the hotel                                                         |
| ReservedRoomType            | Code of room type reserved. Code is presented instead of designation for anonymity reasons                                                                                                                                                                       |
| StaysInWeekendNights        | Number of weekend nights (Saturday or Sunday) the guest stayed or booked to stay at the hotel                                                                                                                                                                    |
| StaysInWeekNights           | Number of weeknights (Monday to Friday) the guest stayed or booked to stay at the hotel                                                                                                                                                                          |
| TotalOfSpecialRequests      | Number of special requests made by the customer (e.g. twin bed or high floor)                                                                                                                                                                                    |


**CustomerType** categories:
- Contract - when the booking has an allotment (pre-negotiated room) or other type of contract associated to it (related to OTAs or companies);
- Group – when the booking is associated to a group;
- Transient – when the booking is not part of a group or contract, and is not associated to other transient booking;
- Transient-party – when the booking is transient, but is associated to at least other transient booking

**DepositType** categories:
- No Deposit – no deposit was made;
- Non Refund – a deposit was made in the value of the total stay cost;
- Refundable – a deposit was made with a value under the total cost of stay.

**Meal** categories:
- Undefined/SC (self-catering) – no meal package (only room);
- BB – Bed & Breakfast;
- HB – Half board (breakfast and one other meal – usually dinner);
- FB – Full board (breakfast, lunch and dinner)

**ReservationStatus** categories:
- Canceled – booking was canceled by the customer;
- Check-Out – customer has checked in but already departed;
- No-Show – customer did not check-in and did inform the hotel of the reason why


## Additional Remarks

- Additional metadata can be found in the supplementary paper.
- The name of the individuals and company involved are anonymized to protect
confidentiality. Although, the data set provided comes from a real business.
- Net demand is defined as demand minus cancellations.
- AssignedRoomType can be different of ReservedRoomType (possible reasons: overbooking, after arrival upgrade)
- Company can be the same as Agent
- Country shouldn't be used for analysis as its quality is dependent on chek-in
- CustomerType Transient or Transient-party examples: direct booking, booking website, ...

## Expected Outcomes

1. Explore the data and build a model to predict cancellations:
    * Define a machine learning success criteria;
    * Take in consideration the business objectives and requirements when selecting the algorithm;
2. Elaborate on the business implications of employing the model and the insights obtained from model development
3. Make suggestions how could the model be deployed and its impact on the hotel’s business processes
