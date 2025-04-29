# ee447-experiment-5---analog-to-digital-converter-solved
**TO GET THIS SOLUTION VISIT:** [EE447 Experiment 5 – Analog to Digital Converter Solved](https://www.ankitcodinghub.com/product/ee447-solved-5/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;112896&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;EE447 Experiment 5 - Analog to Digital Converter Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
Objectives

The TM4C is equipped with an analog-to-digital (ATD) conversion system that samples an analog (continuous) signal at regular intervals and then converts each of these analog samples into its corresponding binary value using the successive approximation technique [1]. While doing this lab, you will learn,

How to program the TM4C ATD converter system.

How to display the ATD converted analog signal on the termite.

1 Background Information

The TM4C analog-to-digital (ATD) conversion system:

The TM4C ATD conversion system consists of a 12-channel, 12-bit, multiplexed input analog-to-digital converter block. Like many peripherals, in order to use the ATD feature, you must first “power up” one of the ATD modules. To do this, we again use the Run Clock Gate Control register like in Lab 2, only this time for the ATD (RCGCADC at address 0x400F.E638). Set bit 0 of the RCGCADC register to 1 in order to use ATD module 0 (ADC0). Since the ATD module will need access to the external signal being sampled, a GPIO port must be configured to “connect” an external pin to the ATD. Therefore, we must also “power up” the GPIO peripheral just like in Lab 2 using the RCGCGPIO register. Each of the ATD input channels are associated with a pin on the board. For this lab, we will use pin PE3. Figure 1 shows the assignment of each channel.

Since this lab will be fairly straight forward in that there is only one signal to sample at a relatively slow sample rate, sequencer 3 (SS3) will work perfectly.

Figure 1: ATD channel – pin assignments (Table 13-1 of the datasheet)

Figure 2: ATD channel – pin assignments (ATD Sequencer list (Table 13-2 of the datasheet) )

GPIO Setup

As mentioned before, the ATD needs access to the outside world via the GPIO port, so it is a good idea to set this up first. We need to configure the GPIO port so that it can receive a signal (input), and then send that signal to the ATD for sampling. (Refer to Lab 2 or datasheet for a reminder of GPIO registers). After the RCGCGPIO register has been configured to enable port E (by setting bit 4), the Alternate Function register (AFSEL) will need to be set for pin 3. The Alternate Function register tells the TM4C that we will not be using PE3 as a simple on/off switch like we did in Lab 2. Instead, enabling the AFSEL register tells the TM4C that we would like to “connect” the associated pin with some other peripheral in the TM4C. Since we are using PE3 (pin 3 of port E), set bit 3 in the AFSEL register associated with port E. When using an alternate function, the next step is normally to configure the PCTL register to tell the TM4C which of the many peripherals available we would like to use as the alternate function. However, in this case, AIN0 happens to be the default for PE3. Next, set the direction of PE3 to input by setting bit 3 to 1 in the DIR register. Since we will be measuring a continuous (analog) signal, we must enable analog on PE3 by setting bit 3 to 1 in the AMSEL register.

ATD Setup

The base address for the ADC0 configuration registers is 0x4003.8000, and the following configuration registers will be referenced by their offset instead of their full address. Changes to the ATD configuration should only be made while the ATD is disabled! Controlling the ATD is done by controlling its associated “sequencer”. The sequencers control when a sample should be taken, and which sequencer is activated is controlled by the ADC Active Sample Sequencer register (ADCACTSS, offset 0x000). For this lab we will be using sequencer 3, therefore, in order to disable sequencer 3, clear bit 3 of the ADCACTSS.

Figure 3: The ADC Active Sample Sequencer register

The TM4C has the capability to trigger a sample based on a variety of signals. For instance, a sample can start on the edge of a square wave, by software, or from the timer module. Again, like the interrupts, the trigger to start an ATD conversion is sequencer specific. What triggers the sequencer is configured using the ADC Event Multiplexer Select register (ADCEMUX, offset 0x014). We will be triggering each sample in software for this lab, therefore, bits 15:12 need to be cleared.

Figure 4: ADC Event Multiplexer Select register

So far we have told the TM4C that we need to create an input through GPIO to be used to receive our signal to be sampled, we have told which ATD module and which sequencer to use. However, we have not told the ATD module which channel to use. To do this, write 0x0 (meaning AIN0) to section 0 (meaning the first sample) of the ADC Sample Sequence Input Multiplexer Select 3 register (meaning sample sequencer 3) to select channel AIN0. The offset for this register ADCSSMUX3 is 0x0A0. The default channel is already AIN0 and SS3 already takes a single sample, so you can as well skip this step.

Figure 5: ADC Sample Sequence Input Multiplexer Select 0 register

Next, we will use a polling method in order to know when a sample is ready. To do this we monitor the interrupt flags in the RIS register. However, in order to tell the TM4C to set flags in the RIS register, we must set the IE0 bit in the ADC Sample Sequence Control register (ADCSSCTL3, offset 0x0A4). (Note that we are using SSCTL3 because we are using sequencer 3.) We also need to set the END0 bit to tell the sequencer to stop sampling after one sample. This seems redundant since sequencer 3 only takes one sample, but it is required. Note, that if you were using a different sequencer that had the capability to take many samples, the appropriate SSCTL register is where you would specify the number of samples desired.

Figure 6: ADC Sample Sequence Control 3 register

ATD sampling rate is controlled by the ADC Peripheral Configuration register (ADCPC, offset 0xFC4). The ATD can sample at 125 kilo-samples per second (ksps), 250 ksps, 500 ksps, and 1 Mega-samples per second (Msps). Since we are triggering via software, and doing so on a relatively slow interval, we can choose a sample rate of 125 ksps. Set bits 3:0 to 0x01 in the ADCPC register to select 125 ksps.

Figure 7: ADC Peripheral Configuration register

The ATD system is now configured and can be enabled. Once enabled, (by setting bit 3 of the ADCACTSS register) the ATD system is ready to start sampling on your trigger.

Sampling

Since we set the ATD module up to initiate a sample from a software trigger, the program needs to tell the ATD module (specifically, the sequencer we are using) to start sampling. This is done using the ADC Processor Sample Sequence Initiate register (ADCPSSI, offset 0x028). Bits 3:0 represent each sequencer. Since we are using sequencer 3, setting bit 3 to 1 tells the sequencer to start sampling.

Figure 8: ADC Processor Sample Sequence register

A sampling sequence will take a few clock cycles, so we have to monitor when the sequence is complete. The ADC Raw Interrupt Status register (ADCRIS, offset 0x004) contains flags corresponding to each sequencer (bits 3:0) that are set to 1 when a sequence has completed. In our case, checking bit 3 monitors if / when sequencer 3 is done sampling.

Figure 9: ADC Raw Interrupt Status register

Each sequencer stores its results in its own FIFO buffer register (ADCSSFIFOn). Address offset: ADCSSFIFO0 0x048 ADCSSFIFO1 0x068 ADCSSFIFO2 0x088 ADCSSFIFO3 0x0A8 Once sampling is complete on sequencer 3, the value of the oldest sample will be in ADC Sample Sequence Result FIFO 3 (ADCSSFIFO3, offset 0x0A8).

Figure 10: ADC Sample Sequence Result FIFO n register

The ADC lets us know a sample value is ready for us by setting the appropriate bit in the ISR, then it waits for us to load the sample from the FIFO register. Therefore, we need to tell the ADC we are ready for it to continue sampling. To do this, we set bit 3 (for sequencer 3) of the Interrupt Status and Clear Register (ADCISC, offset 0x00C).

Figure 11: ADC Interrupt Status and Clear register

2 Preliminary Work

1. (40%) Program the ATD conversion system on the board, in C language, to convert the analog signal to a 12-bit number between 0x000 and 0xFFF (4095). The input will be taken from PE3. The output value should be stored in an integer variable. Put a screenshot of Keil showing this variable on your report.

2. (5%) Assume that there is a 1.65 Volt DC offset in your input. Subtract the value corresponding to this offset from your reading. Note that new result is a signed number.

3. (20%) Convert the resulting value to a char array containing a decimal representation with two decimal places (X.YZ) between -1.65 and 1.65. Put a screenshot on your report.

3 Parts List

1 x Potentiometer 1 x TM4C123G Board

References

[1] TI, “Tiva tm4c123gh6pm microcontroller data sheet.” http://www.ti.com/lit/ds/spms376e/ spms376e.pdf.
