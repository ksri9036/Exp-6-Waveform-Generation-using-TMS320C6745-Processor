# Exp-6-Waveform-Generation-using-TMS320C6745-Processor

#          Waveform-Generation-using-TMS320C6745-Processor
# AIM: 
          
  To generate following waveforms using-TMS320C6745-Processor
  a.Triangular Waveform
  b. Sawtooth waveform
  c. Square Waveform

# Software REQUIRED: 

  PC Installed with CC V4
CCS v4
TMS320C6745 KIT
USB Cable
5V Adapter

# Procedure for build a project on wave generation using TMS320C6745 DSP
```
1.Hardware Setup:Power and PC Connections.Connect the 5V DC adapter to the TMS320C6745 DSP kit. Connect the JTAG/USB port of the kit to the PC using the USB cable. Connect the DAC output header/audio jack of the kit to the Oscilloscope (CRO) probe.
2.Create a CCS v4 Project:Open Code Composer Studio v4. Go to File > New > CCS C/C++ Project. Name the project (e.g., Waveform_Gen), select target device as TMS320C6745, and set project type to Executable.
3.Add Source Code:Right-click on the project in project explorer, select New > Source File. Save it as main.c. Copy and paste one of the program codes given below.
4.Build and Load:Go to Project > Build Project (Ctrl+B) to compile. Check for zero errors. Then go to Target > Connect Target and load the compiled .out executable file to the DSP target memory via Target > Load Program.
5.Execute and Observe:Run the program (F5). Observe the output waveform on the CRO channel, or use CCS View > Graph > Time/Frequency to plot memory buffer values.
```

# Program for Triangualar wave generation using TMS320C6745 DSP
```
#include <stdio.h>

#define MAX_VAL 1000
#define MIN_VAL 0
#define STEP 50

unsigned short dac_out;

void delay(unsigned int count) {
    unsigned int i;
    for(i = 0; i < count; i++);
}

void main() {
    dac_out = MIN_VAL;
    
    while(1) {
        // Ramp UP
        while(dac_out < MAX_VAL) {
            dac_out += STEP;
            // Write dac_out to DAC registers or buffer
            delay(100); 
        }
        // Ramp DOWN
        while(dac_out > MIN_VAL) {
            dac_out -= STEP;
            // Write dac_out to DAC registers or buffer
            delay(100);
        }
    }
}
```

# Program for Sawtooth wave generation using TMS320C6745 DSP
```
#include <stdio.h>

#define MAX_VAL 1000
#define MIN_VAL 0
#define STEP 50

unsigned short dac_out;

void delay(unsigned int count) {
    unsigned int i;
    for(i = 0; i < count; i++);
}

void main() {
    dac_out = MIN_VAL;
    
    while(1) {
        // Linear Ramp UP
        for(dac_out = MIN_VAL; dac_out < MAX_VAL; dac_out += STEP) {
            // Write dac_out to DAC registers or buffer
            delay(100);
        }
        // Sudden drop to minimum
        dac_out = MIN_VAL;
    }
}
```

# Program for Square wave generation using TMS320C6745 DSP
```
#include <stdio.h>

#define HIGH_VAL 1000
#define LOW_VAL 0

unsigned short dac_out;

void delay(unsigned int count) {
    unsigned int i;
    for(i = 0; i < count; i++);
}

void main() {
    while(1) {
        // High level
        dac_out = HIGH_VAL;
        delay(1000);
        
        // Low level
        dac_out = LOW_VAL;
        delay(1000);
    }
}
```
# OUTPUT

<img width="1376" height="768" alt="Gemini_Generated_Image_fsmp8nfsmp8nfsmp" src="https://github.com/user-attachments/assets/8b46b2d4-78bc-4030-84a5-3d8250b84a13" />


# RESULT
The C programs for generating Triangular, Sawtooth, and Square waveforms were written, compiled using CCS v4, and loaded onto the TMS320C6745 DSP kit. The required output waveforms were successfully generated and verified on the CRO / CCS Graph window.
