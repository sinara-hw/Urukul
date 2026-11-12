# CHANGELOG

All notable changes to the Urukul-DIOT are documented in this file.

## v2.0

**Release owner:** Mikołaj Sowiński (TS)

**Designers:** 
- Krzysztof Belewicz (WUT ISE)
- Marta Fąfara (TS)

**Reviewers:** 
- Maciej Przybysz (TS)
- Marta Fąfara (TS)

**Contributors:** 
- Mikołaj Sowiński (TS)

**Funded by:** 
- WUT ISE
- Technosystem

All schematic files updated according to DIOT template.
Change list in respect to the previous revision:

project parameters:
-added link to repository
-added version number 2.0

#88 LM75AUNN/NOPB updated along with DIOT template sync
#90 P4 removed along with DIOT template sync

Urukul.SchDoc
-ESD strips moved to Mechanical.SchDoc
-fiducials moved to Mechanical.SchDoc
-front panel mounting/grounding moved to Mechanical.SchDoc
-SMA insulating washers moved to Mechanical.SchDoc
-LEDs moved to FP_Connectors.SchDoc
-SMA connectors & Baluns moved to FP_Connetors.SchDoc
-R100/R169/R170/R147 collated into R100 and moved to DDS_OUT_channel.SchDoc
-J7 moved to CLK_INPUT.SchDoc
-Sheet symbols for DDS_channel and DDS_OUT_channel collated into repeat() blocks
-harnesses RAMP_CTL/DDS_Profile changed to individual nets to support repeat() blocks
-IC4/ IC16/ IC9 moved to CLK_SYNC.SchDoc

Power_Supplies.SchDoc
-T_R1 changed to 470, R304 changed to 1k2||1k2 (was 1k6 for T_R1, and 240R for R304). DIOT template used HSME-C110 @ ~1mA (approx 2.6mcd intensity), Urukul uses 571-0112F (previously @ ~5.4mA - appox 10.8mcd intensity, now changed to ~4.3mcd intensity to match other front panel LEDs).

Power_main_DCDC.SchDoc (previously Urukul_Supply.SchDoc)
-PWR_EN port/net changed to PSU_EN
-Power net class directive HPOWER changed to PWR to comply with template
-IC28 removed (already present in template as T_IC1)
-LD11 and R291 (P3V3_MP LED) removed, as it is already present on Power_Supplies.SchDoc
-LD7, R353, R304, T23 (PGOOD FP LED) moved to Power_Supplies.SchDoc
-R87 changed from 160 to 240 to reduce BOM count (P2V1 changes from 2.1V to 2.095V)
-R23/ R118 changed from 0603 to 0402 to reduce BOM count
-R132 changed from 0603 to 0402 to reduce BOM count
-R135 changed from 2k to 2k2 to reduce BOM count (P7V0A changes from 7V to 7.02V)
-R55/R82/R84 changed from 0603 to 0402 to reduce BOM count

FP_Connectors.SchDoc
-moved front panel SMA connectors (4xDDS out and 1x CLK in) and LEDs here from Top schematic page in previous revision
-DDS green LED resistors changed to 1k2 || 1k2 to match intensity between red and green LEDs (4.15mcd for red, 4.33mcd for green)
-aligned designators for better readability

CLK_INPUT.SchDoc
-#83 / #87 BP_CLK from DIOT backplane connected to IC24 (in parallel with J7/J10)
-one of the outputs of IC24 additionally routed to FPGA
-R163 set as DNP accross variants, as both R47/R163 were mounted

DDS_channel.SchDoc
-L19A-D set as DNP in EEM_AD9910/ DIOT_AD9910 variants as it is unused
-aligned designators, small readability improvements

DDS_OUT_channel.SchDoc
-aligned designators, small readability improvements

CLK_SYNC.SchDoc
-nets EEM0_LVDSX_N/ EEM0_LVDSX_P/ EEM1_LVDSX_N/ EEM1_LVDSX_P renamed to EEM_IO.LVDS_NX/ EEM_IO.LVDS_PX to comply with DIOT template
 (EEM0_LVDS7_P/N, EEM1_LVDS0_P/N, EEM1_LVDS1_P/N)
-nets DDS0_SYNC_OUT_P/N renamed to DDS_SYNC_OUT_P/N0 to comply with top level changes
-nets DDSX_SYNC_IN_P/N renamed to DDS_SYNC_IN_P/N[3..0] to comply with top level changes
-R150 made as DNP accross variants
-R152/R153 made as DNP in variants EEM_AD9912/ DIOT_AD9912

Urukul_FPGA.SchDoc
-RFSW_CTRL0/1/2/3 ports changed to single RFSW[3..0] port to comply with top level changes
-DDS_SYNC_CLK0 port changed to DDS_SYNC_CLK[3..0] port to comply with top level changes
-EEM0_SCL/EEM0_SDA renamed to EEM0_INT_I2C.SCL/ EEM0_INT_I2C.SDA to comply with template
-EEM1_SCL/EEM1_SDA renamed to EEM1_INT_I2C.SCL/ EEM1_INT_I2C.SDA to comply with template
-aligned designators, small readability improvements

Urukul_FPGA_Config.SchDoc
-fixed missing CBSEL.PNG file
-I2C0_SDA/ I2C0_SCL renamed to EEM0_I2C.SDA/ EEM0_I2C.SCL to comply with template
-added changes from #86

Urukul_FPGA_LVDS.SchDoc
-120R resistors rearanged for better readability
-nets EEM0_X_N/ EEM0_X_P/ EEM1_X_N/ EEM1_X_P renamed to EEM_IO.LVDS_NX/ EEM_IO.LVDS_PX to comply with DIOT template

Urukul_FPGA_Supply.SchDoc
-rearanged PLL decoupling for better readability


Floating R195 removed
DAC_OUT_P/ DAC_OUT_N sheet entries moved to avoid bus crossings on Urukul.SchDoc
Authors corrected
C189/C194, C213/C214 replaced with 0R jumpers; C189/C194 re-added and moved in front of 0R jumpers to retain AC coupling
BP_CLK re-routed to CPCIS_CLK connector, adjusted variants to default to BP_CLK in DIOT boards
P_version changed to 1.6
Testpoints/power LEDs moved as per the new template
U1 pin N14 unconnected from GND
Re-added draftsman file previously present in the project
Removed files: outjob, front panel drawings for both variants

Fixed DELOCK SMA footprint
Front panel LEDs/SMAs aligned
Added new front panel model to the project

Added new FPGA flashing circuit as per the template

Changes in RF section to fit new mounting holes for the enclosure:
R15 A-D moved to top layer
R113/R140 A-D moved to top layer
R104/R105/R106/R107 A-D rearanged on bottom layer
R96/R97/R98/R99 A-D rearanged on bottom layer
R93/R94 A-D rearanged on bottom layer
L19/L20 A-D rearanged on bottom layer
rearanged passive components around IC13 A-D on top layer (aligned decoupling capacitors, rotated C115 to fit components from bottom layer)
previous layout differed for each channel (A-D) - placement/traces have been unified
unified DDS DAC/output channel differences (eg ground connection of C108D vs C108A-C)

rotated J10 to better align with J7

removed components from backplane-connector area (#91)
Corrected silkscreen (#89)

Corrected silkscreen - soldermask/copper colisions

Reduced duplicated values in different cases (BOM count) where possible:
T_R89 (R0603_1K3_1%_0.1W_100PPM changed to R0402_1K3_1%_0.0625W_100PPM)
T_C13/T_C16-T_C19 (CC0402_10NF_50V_5%_X7R changed to CC0402_10NF_16V_10%_X7R)
T_C3-T_C6/T_C8/T_C14/T_C15/T_C20-T_C23  (CC0402_100NF_50V_10%_X7R changed to CC0402_100NF_16V_10%_X5R)
T_R6/T_R9 (R0402_1K6_1%_0.0625W_100PPM changed to R0603_1K5_1%_0.1W_100PPM)

-updated project parameters
-updated schematic sheet templates
-updated Temperature_monitoring.SchDoc IC
-updated 100nF 0402 passives to match template
-updated 10nF 0402 passives to match template
-C3, C213, C223, C228 changed from CC0603_1UF_25V_10%_X7R to CC0402_1UF_16V_10%_X5R
-C4, C258 changed from CC0805_10UF_16V_10%_X5R to CC0805_10UF_25V_10%_X5R
-updated FPGA decoupling to match template
-FPGA_Supply.SchDoc changed from A3 to A4
-modified sheet order in the project
-updated Draftsman file


- R108 and R110 changed from 10k to 4k7 to improve resistor divider with IC19 internal 25k pull-up. Low state is now below VIL max
- Capacitors 22uF changed to 20V rating instead of 10V.
- HWREV resistors (R171-R174) changed to 10k to limit pin input current.
- R38 and  R54 DNP in 9912 variants as written in note next to them

- R100 replaced by resistor divider (R100-R102) to lower the signal level coming to FPGA input pin
- AFE_PWR signal is not used, but power sequence is kept
- Missing power good signals for P1V2, P2V5 and P5V0A created using comparator
- Additional PG_Logic.SchDoc created to improve readability.
- PCB updated according to above desribed modifications


---

## Prior releases

**Designers:**
- Grzegorz Kasprowicz (WUT)
- Maciej Przybysz (TS)
- Paweł Kulik (WUT)
- Filip Świątkowski (WUT)

**Reviewers:**
- unspecified

**Contributors:**
- Marcin Magdziak (TS)