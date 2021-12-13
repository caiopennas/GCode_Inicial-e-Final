-- CURA --


CURA - inicial

//Preparo de Temperatura 
M104 S{material_print_temperature} ;Start heating extruder
M140 S{material_bed_temperature} ;Start heating bed
M109 S{material_print_temperature} ;Wait for extruder to reach temp before proceeding
M190 S{material_bed_temperature} ;Wait for bed to reach temp before proceeding
G92 E0 ; Reset Extruder

//Nivelamento
G28 ; Home all axes
G29 ;
M109 S{material_print_temperature} ;Wait for extruder to reach temp before proceeding
M190 S{material_bed_temperature} ;Wait for bed to reach temp before proceeding

//Limpeza de bico antes da impressão
G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed
G1 X0.1 Y20 Z0.3 F5000.0 ; Move to start position
G1 X0.1 Y200.0 Z0.3 F1500.0 E15 ; Draw the first line
G1 X0.4 Y200.0 Z0.3 F5000.0 ; Move to side a little
G1 X0.4 Y20 Z0.3 F1500.0 E30 ; Draw the second line
G92 E0 ; Reset Extruder
G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed
G1 X5 Y20 Z0.3 F5000.0 ; Move over to prevent blob squish


CURA - final

G1 X0 Y{machine_depth} ;Present print
M106 S0 ;Turn-off fan
M104 S0 ;Turn-off hotend
M140 S0 ;Turn-off bed
M300 S440 P200
M84 X Y E ;Disable all steppers but Z

-- PrusaSlicer --

PRUSA - inicial

//Preparo de Temperatura 
M140 S[first_layer_bed_temperature] ; Set bed temp
M190 S[first_layer_bed_temperature] ; Wait for bed temp
M104 S[first_layer_temperature] ; Set extruder temp
M109 S[first_layer_temperature] ; Wait for extruder temp

//Nivelamento
G28 ;Home
G29 ;
G92 E0 ;Reset Extruder

//Limpeza de bico antes da impressão
G1 X10.1 Y20 Z0.28 F5000.0 ;Move to start position
G1 X10.1 Y200.0 Z0.28 F1500.0 E15 ;Draw the first line
G1 X10.4 Y200.0 Z0.28 F5000.0 ;Move to side a little
G1 X10.4 Y20 Z0.28 F1500.0 E30 ;Draw the second line
G92 E0 ;Reset Extruder
G1 Z2.0 F3000 ;Move Bed up

PRUSA - final
M104 S0 ; turn off temperature
M140 S0 ; turn off temperature
G28 X0  ; home X axis
M84     ; disable motors
M300 S440 P200
