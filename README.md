# FIPO FPGA ITCH Parser & OrderBook

This project is designed for FPGA-based processing of NASDAQ ITCH 4.1 market data. It includes parsing ITCH messages and maintaining an OrderBook, with both host-based and FPGA-based test harnesses to validate the processing components.

## Overview

The `FIPO FPGA ITCH Parser & OrderBook` project contains multiple components organized into the following categories:

- **ItchParser**: Responsible for parsing NASDAQ ITCH 4.1 messages.
- **OrderBook**: Maintains and updates the order book based on parsed ITCH messages.
- **FPGA Target**: Simulation and testing of the ITCH parser and OrderBook on FPGA hardware (PXIe-6592R).

## Project Structure

### My Computer
- **Tests**
  - **ItchParser**
    - `Host-ItchParser-TestHarness.vi`: Host-based test harness for ITCH parser.
    - `Host-ItchParser-TestHarness-Typedctl`: Type definitions for ITCH parser test harness.
    - `Host-ItchParser-SendData.vi`: Sends test data to the ITCH parser.
    - `Host-ItchParser-Deserialize-Results.vi`: Deserializes and checks results from ITCH parser.
  - **OrderBook**
    - `Host-OrderBook-TestHarness.vi`: Host-based test harness for OrderBook.
    - `Host-OrderBook-TestHarness-Typedctl`: Type definitions for OrderBook test harness.
    - `Host-OrderBook-SendData.vi`: Sends test data to the OrderBook.
    - `Host-OrderBook-Deserialize-Results.vi`: Deserializes and checks results from OrderBook.

### FPGA Target (PXIe-6592R, Simulation)
- **Tests**
  - **Fpga-ItchParser-TestHarness.vi**: FPGA-based test harness for ITCH parser.
  - **Fpga-OrderBook-TestHarness.vi**: FPGA-based test harness for OrderBook.
  - `HT-TEST_IN`, `HT-TEST_OUT`, `TS-FEED_IN`, `TS-FEED_OUT`: Test data inputs/outputs for the harnesses.
- **ItchParser**
  - `Fpga-ItchParser.vi`: FPGA implementation of the ITCH parser.
- **OrderBook**
  - `Fpga-OrderBook.vi`: FPGA implementation of the OrderBook.

### Common Utilities
- **Utilities**
  - `Fpga-Get-Integer8.vi`, `Fpga-Get-Integer32.vi`, `Fpga-Get-Integer64.vi`: Utility VIs for handling integers of different sizes on the FPGA.
  - `Fpga-OrderBook-Command.ctl`: Control definitions for OrderBook commands.
  - `40 MHz Onboard Clock.vi`: Onboard clock settings for the FPGA.

### IP Builder
- **PXIe-6592R IO Socket v1**: I/O socket configuration for the PXIe-6592R FPGA target.

## Dependencies
- **Build Specifications**
  - `Fpga-ItchParser-TestHarness`: Build specification for the FPGA ITCH Parser Test Harness.
  - `Fpga-OrderBook-TestHarness`: Build specification for the FPGA OrderBook Test Harness.

## Getting Started

1. **Clone the Repository**: Ensure you have the latest version of the project.
   ```bash
   git clone https://github.com/hftconsultancy/FIPO


- **Open in LabVIEW**  
  Open the `.lvproj` file using **LabVIEW FPGA Module (2020 or later)**.

- **Build FPGA Bitfiles**  
  Go to `Project Explorer > Build Specifications`  
  Right-click `Fpga-ItchParser-TestHarness` or `Fpga-OrderBook-TestHarness`  
  Select **Build**

- **Run Host Test Harnesses**  
  Use host VIs under **My Computer** to validate ITCH parsing and order book logic.

- **Simulate or Deploy to FPGA**  
  Run in **Simulation Mode** using the **PXIe-6592R** simulation target  
  Or deploy to actual **PXIe-6592R FPGA hardware**
