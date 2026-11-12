Tonic loads SHD dataset and provides it samples, labels, event, format, class names and sensor information.

```dataset = tonic.datasets.SHD(save_to="./shd", train=True)``` Tells Tonic to load the training data which contains 8k spoken digit samples in this notebook.

A channel in this context is one frequency sensitive output of simulated cochlea. SHD dataset uses a neuromorphic cochlea model to convert speech into spikes. It has 700 channels where each channel responds mainly to a different frequency range sound. Lower numbered channels generally responds to lower frequencies and higher to higher. 

So from the raster spike plot each blue dot represents one spike event produced by a particular channel at a particular time. The horizontal position tells when the spike occurs and vertical which channel it came from. The color of the dot indicates the events polarity since the plot use `coolwarm` color map. The polarity indicates the type or direction of an event, where positive polairty indicate a signal increase and negative a signal decrease.

However since the sensor size (SHD event format) is `(700,1,1)` it only has one polarity value which means that all events have the same polarity and thus all events are shaded blue. 