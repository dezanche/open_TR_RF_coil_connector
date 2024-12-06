# Transmit/Receive RF Coil Connector
This design is the first of the [OpenConnectors](https://github.com/dezanche/Open_Connectors) collection. It is intended for use with MRI radio frequency coils that operate in transmit/receive mode and supports a maximum of 2 coaxial connections.

![exploded view](pictures/exploded_view.png)
![](pictures/connector_assembly.png)

## Connector Structure
The connector consists of a system-side and coil-side housing which are designed to mate. Each housing is made of off-the-shelf and 3D-printed parts that enclose and support the printed circuit boards (PCBs) which contain the electrical contacts.

### Connector Housing
System-side and coil-side housing parts are defined in the [FreeCAD](https://www.freecad.org/) [file](housings/connector_full_3D_model.FCStd) which contains the full 3D model of the connector. Individual parts can be exported in various formats for fabrication. The [bill of materials](housings/TR_RF_coil_connector_full_3D_BOM.md) lists off-the-shelf and other parts required to build the connector.

A project may contain more than one housing. Therefore, each housing has to be associated to a unique identifier which is used in all the filenames relevant to that housing. The string \<coil-side> or \<system-side> has to be added after the identifier in the filename to distinguish the coil-side or system-side housing component, respectively. In case the system-side housing is designed to contemporarely host more than one coil-side connection (e.g., two different RF coil for TX and RX), another identifier (e.g., \<TX>, \<RX>) has to be added before the \<coil-side> string in the filename. As an example, a housing identified as *housing1* designed for an MR system which accept different TX and RX RF coil, can be made of files whose names are:
- `housing1_system-side*.*`
- `housing1_TX_coil-side*.*`
- `housing1_RX_coil-side*.*`

In case the housing is designed for a system operating with only one RF Coil for TX and RX, the filenames would be:
- `housing1_system-side*.*`
- `housing1_coil-side*.*`

In general, all the components associated with the same housing identifier are supposed to be mated together.
All the file relevant to the housing have to be collected inside the "housings" folder. A bill of materials (BOM) file has to be created for each housing according to the template provided in the "housings" folder. The BOM text filename should report the relevant housing identifier. 3D-CAD models can be provided with any software of choice but an OpenSource software is always preferable (e.g., [FreeCAD](https://www.freecad.org/)). Despite of the 3D-CAD software used to design the housing of the connector, each part of the housing has to be designed to be effectively printed with standard FDM printers. Therefore, *stl* files have to be provided since they are the most common file format accepted by 3D printer software. These files have to be collected in the "exported" sub-folder and have to be named with the same convention described above.

### Connector Boards
KiCAD files TBD

### Mating Tables
Despite the minimum requirement of one coil-side and system-side board per housing, more boards can be designed for each housing. As a consequence, each system-side board might mate only with some of the coil-side boards and viceversa. *Mating Tables* allow to immediatly retrive this information and should be reported for each housing in a dedicated Markdown file named "MatingTables.md". An example is provided in the relevant file available with this Template Repository

### Main README File
When the repository is prepared according to the provided indications, the present README file should be used to describe the project and to report a brief description of each housing and associated board. For example, the following structure can be used
```Markdown
## <housing_identifier_1>
Connector housing designed for TX/RX coil connection and Low Field MRI applications. The design comprises a lock mechanism to avoid accidental detachments ...

### <board_identifier_1.1>
Coil-side board hosting one BNC (M) connector and 15 pins to provide DC or logic signals. The board hosts an EEPROM IC Memory for Coil Code storage adn three guide pins to assist with reliable alignement

...

### <board_identifier_2.1>
System-side board hosting one BNC (F) connector and a socket for 15 pin connections. The board is designed to host an ATmega328P microcontroller that can be programmed to acquire 10 of the 15 available signals received from the RF coil. The other 5 signal lines are available for the scanner and are used for grounding, DC supply, TX/RX gating, etc.
```
Pictures can be used in addition. In this case, they can be collected in the "picture" folder and referenced inside the README file

## LICENSE
Three license files are added (see [CERN-OHL](https://cern-ohl.web.cern.ch/)). The user can keep only the file relevant to the license that fits better the project. In the license file the user can add the proper copyright information in place of the field included within the angle brackets.

## CITATION
To help users correctly cite your project, a "CITATION.cff" file (read here about [citation files](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-citation-files)) is provided with this template and can be modified according to the specific requirements.
