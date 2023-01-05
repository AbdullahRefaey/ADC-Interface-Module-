# ADC-Interface-Module
This is an interface module in Verilog to capture and transfer the digital outputs of an external ADC into an FPGA. 
The code is in Verilog that implements an interface to an external ADC (analog-to-digital converter). 

The ADC interface module has six input and output ports:
clk: This is the clock input, which is used to synchronize the operation of the ADC interface.
rst: This is the reset input, which is used to reset the internal state of the ADC interface.
adc_conv_done: This is an input port that is used to indicate when an ADC conversion is done. When adc_conv_done is 1, the ADC has finished a conversion and the digital output is ready to be transferred.
adc_data: This is an input port that is used to receive the digital output from the ADC. The adc_data port is a 16-bit port, so it can receive a 16-bit digital output from the ADC.
adc_rdy: This is an output port that is used to indicate when the ADC interface is ready to transfer data. When adc_rdy is 1, the ADC interface is ready to transfer the digital output from the ADC to the adc_out output port.
adc_out: This is an output port that is used to transfer the digital output from the ADC to the rest of the system.
The module uses a finite state machine (FSM) to control the transfer of data from the ADC to the rest of the system. The FSM has two states: IDLE and DATA_TRANSFER.

In the IDLE state, the adc_rdy output is set to 0 and the module waits for the adc_conv_done input to go high, indicating that an ADC conversion is done. When adc_conv_done goes high, the FSM transitions to the DATA_TRANSFER state.

In the DATA_TRANSFER state, the adc_rdy output is set to 1 and the adc_data input is transferred to the adc_out output. After the data transfer is complete, the FSM transitions back to the IDLE state and the process starts over again.
