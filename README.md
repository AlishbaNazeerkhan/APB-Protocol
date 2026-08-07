AMBA APB Protocol Implementation 

Welcome to the AMBA APB (Advanced Peripheral Bus) protocol project repository! This repository contains a detailed implementation and breakdown of the ARM AMBA APB protocol, Used for low-power, low-bandwidth peripheral communication within System-on-Chip (SoC) designs.

Project Process & Workflow

This project is structured to simulate and verify standard APB non-pipelined communication states. The execution model moves through distinct operational phases:

    IDLE State: The default state of the bus where no data transfers are taking place, and PENABLE and PSELx remain low.

    SETUP Phase (T1):

        When a transfer is required, the master asserts the select signal (PSELx), drives the target address onto PADDR, sets the transfer direction via PWRITE, and puts write data on PWDATA (if it's a write operation).

        The bus stays in this state for only one clock cycle before transitioning on the next rising edge of PCLK.

    ACCESS Phase (T2 onwards):

        The master asserts PENABLE to signify the start of the access cycle.

        The slave uses PREADY to either complete the transfer immediately or insert wait states by pulling PREADY low if it requires extra processing time.

        Once PREADY and PENABLE are both high at the rising edge of PCLK, the transaction wraps up successfully, bringing the bus back to IDLE or moving straight into a subsequent setup phase.
