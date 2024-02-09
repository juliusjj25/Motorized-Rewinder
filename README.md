# Motorized-Rewinder

## WARNING: STILL VERY MUCH IN DEVELOPMENT, USE AT YOUR OWN RISK!!!!
### Motorized Rewinder with Clutch
![image](https://github.com/juliusjj25/Motorized-Rewinder/assets/118471600/0ce2d7f8-e23a-4497-9682-00c0f56b82d2)

This system uses an inexpensive TT motor to rewind filament back onto the spool instead of a buffer system. To reduce friction during printing, there is an electromagnetic clutch that is disengaged during printing but engaged during the rewind cycle. The rewind is driven at the spool rim to ensure no slack on the spool during rewind. 
![image](https://github.com/juliusjj25/Motorized-Rewinder/assets/118471600/9dcd6422-6ecc-4b5d-8173-8c6b66ea7dd6)
![image](https://github.com/juliusjj25/Motorized-Rewinder/assets/118471600/ab354256-a75d-4d94-8fd8-9afac2fb6526)

## Mechanical Bill of Materials (Per Gate)
| Item            | Quantity | Notes                                      | Source                                               |
| --------------- | -------- | ------------------------------------------ | ---------------------------------------------------- |
| TT Motor        | 1        |                                            | https://www.amazon.com/dp/B0BJ22YVXW/                |
| Clutch          | 1        |                                            | https://www.aliexpress.us/item/3256805231540827.html |
| ECAS04 Fitting  | 1        |                                            | https://www.amazon.com/dp/B099NPWSFB/                |
| M3x40mm SHCS    | 1        | Used to stiffen adapter, may not be needed |                                                      |
| M3x25mm SHCS    | 2        |                                            |                                                      |
| M3x6mm SHCS     | 1        |                                            |                                                      |
| M3x12mm FHCS    | 4        | Minimum 12mm, could be any length          |                                                      |
| M3x8mm FHCS     | 2        |                                            |                                                      |
| M3 Heat Set     | 4        |                                            |                                                      |

## Pending Electrical Bill of Materials
| Item            | Quantity | Notes                                      | Source                                               |
| --------------- | -------- | ------------------------------------------ | ---------------------------------------------------- |
| SX1509 Board    | 1        | Can handle 16 motors but need 1 clutch out |                                                      |
| DRV8833         | See Note | Each can drive 4 motors                    |                                                      |
| LM2596          | 1        |                                            |                                                      |
| Circuit Parts   | TBD      | See example circuit below [Not Finalized]  |                                                      |

### Things to figure out:
- Software integration with HappyHare:
  -   Need to be able to drive the motor when the MMU goes into retract
  -   Need to be able to engage the clutch when the MMU goes into retract
- Electronics:
  -   Will likely use an SX1509 I2C expansion board for additional pinouts
  -   Will likely use DRV8833 H-Bridge modules to drive the motors, motors only need to spin one direction, so each module can drive 4 motors
  -   Motors need 6V so LM2596 can be used to step down from 24V to 6V
  -   Clutches need 24V but since only one spool is in action at a time, all clutches could be in parallel with each other
  -   A circuit similar to this could be used to control the clutches:
![image](https://github.com/juliusjj25/Motorized-Rewinder/assets/118471600/a1d88c90-322a-4eee-97c7-6bda4a43e0b4)
