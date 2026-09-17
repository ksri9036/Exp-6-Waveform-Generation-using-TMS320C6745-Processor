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

<img width="766" height="287" alt="Screenshot 2026-09-17 105427" src="https://github.com/user-attachments/assets/2202d6c2-559d-46aa-ae53-6c7045ff4bae" />

<img width="765" height="250" alt="Screenshot 2026-09-17 105443" src="https://github.com/user-attachments/assets/18748bea-f372-438f-9299-2c7ff661d72e" />

<img width="760" height="257" alt="Screenshot 2026-09-17 105516" src="https://github.com/user-attachments/assets/3e9b8ebb-3990-4d13-9626-1e8b6a2004ad" />



# RESULT
The C programs for generating Triangular, Sawtooth, and Square waveforms were written, compiled using CCS v4, and loaded onto the TMS320C6745 DSP kit. The required output waveforms were successfully generated and verified on the CRO / CCS Graph window.
