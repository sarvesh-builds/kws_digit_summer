# ESP32-Based Keyword Spotting Digit Summer

An offline keyword-spotting system implemented on an ESP32 for recognizing
spoken digits and maintaining their cumulative sum in real time.

## Overview

This project implements a lightweight **keyword spotting (KWS) system** that
recognizes spoken digits using an **ESP32** and an **INMP441 I2S MEMS
microphone**.

The audio signal is captured by the ESP32 and processed to extract
speech features. An ML model developed using **Edge Impulse** is used to
classify the spoken digit locally on the ESP32.

Each recognized digit is added to a running total, which is displayed on
an LCD. The complete system operates **offline**, without requiring an
internet connection or cloud-based inference.

## Demo

### Video Demonstration

The video below demonstrates the complete system, including spoken-digit
recognition and cumulative-sum display.

https://github.com/user-attachments/assets/736c6c18-6632-4cd6-99d2-e30327d8ae8d

## System Architecture

```text
              ┌─────────────────────┐
              │  INMP441 Microphone │
              └──────────┬──────────┘
                         │ I2S
                         ▼
              ┌─────────────────────┐
              │        ESP32        │
              │   Audio Acquisition │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │  Audio Processing   │
              │  & Feature          │
              │     Extraction      │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │   Edge Impulse ML   │
              │       Model         │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │   Digit Recognition │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │ Cumulative Summation│
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │     LCD Display     │
              └─────────────────────┘
