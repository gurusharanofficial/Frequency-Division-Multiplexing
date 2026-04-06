# Frequency-Division-Multiplexing


AIM

To implement Frequency Division Multiplexing (FDM) for six different message signals using Scilab, generate the multiplexed signal, and perform demultiplexing to recover all the original message signals. The experiment also includes plotting the message signals, multiplexed signal, and demultiplexed signals.

APPARATUS REQUIRED

> Computer System

> Scilab Software

ALGORITHM

1. Set sampling frequency, time duration, and time vector.
2. Generate six message signals with different frequencies.
3. Assign six different carrier frequencies.
4. Perform DSB-SC modulation by multiplying each message with its carrier.
5. Add all modulated signals to form the multiplexed FDM signal.
6. For each channel, multiply the multiplexed signal with the same carrier (demodulation).
7. Apply a low-pass filter to extract the recovered message.
8. Plot message signals, multiplexed signal, and recovered s ignals.

THEORY

Frequency Division Multiplexing (FDM) is a technique in which multiple message signals are transmitted simultaneously over a single communication channel by assigning each signal a different carrier frequency. Each message modulates its own carrier, and all modulated signals are added to form the multiplexed signal. Since the carrier frequencies are well separated, the signals do not overlap in the frequency domain.

At the receiver, each signal is recovered by multiplying the multiplexed signal with the corresponding carrier (coherent demodulation) and passing it through a low-pass filter to extract the original baseband message. FDM is widely used in radio broadcasting, telephone systems, and cable TV.

PROGRAM

```
t = linspace(0, 1, 1000);
freqs = [5, 5.5, 6, 6.5, 7, 7.5];
signals = zeros(6, length(t));
for i = 1:6
signals(i, :) = sin(2 * %pi * freqs(i) * t);
end
fdm_signal = zeros(1, length(t));
for i = 1:6
fdm_signal = fdm_signal + signals(i, :);
end
demux_signals = zeros(6, length(t));
for i = 1:6
demux_signals(i, :) = fdm_signal .* sin(2 * %pi * freqs(i) * t);
end
scf(1);
clf;
for i = 1:6
subplot(3,2,i);
plot(t, signals(i, :));
title('Original Signal f=' + string(freqs(i)));
end
scf(2);
clf;
plot(t, fdm_signal);
title("FDM Signal");
scf(3);
clf;
for i = 1:6
subplot(3,2,i);
plot(t, demux_signals(i, :));
title('Demultiplexed Signal f=' + string(freqs(i)));
end
```

OUTPUT WAVEFORM
<img width="733" height="574" alt="Screenshot 2026-03-27 120055" src="https://github.com/user-attachments/assets/b304d874-1d4e-41bd-a5b5-d3c968256df9" />
<img width="687" height="536" alt="Screenshot 2026-03-27 120124" src="https://github.com/user-attachments/assets/fe896d78-14c9-4ebb-956f-00f32a9fe6c4" />
<img width="744" height="587" alt="Screenshot 2026-03-27 120145" src="https://github.com/user-attachments/assets/359f9a13-034d-4d50-8d4d-3600a1978cd6" />

Tabulation

![WhatsApp Image 2026-04-04 at 11 09 22](https://github.com/user-attachments/assets/311a091a-da2a-4b00-ae45-903d31190f5e)

RESULT

Six different message signals were generated and modulated using FDM. All modulated signals were added to form a multiplexed FDM signal. Each message was successfully recovered using coherent demodulation followed by low-pass filtering. The plots confirmed accurate multiplexing and demultiplexing.
