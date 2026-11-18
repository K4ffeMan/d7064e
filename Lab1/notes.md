Tonic loads SHD dataset and provides it samples, labels, event, format, class names and sensor information.

``dataset = tonic.datasets.SHD(save_to="./shd", train=True)`` Tells Tonic to load the training data which contains 8k spoken digit samples in this notebook.

A channel in this context is one frequency sensitive output of simulated cochlea. SHD dataset uses a neuromorphic cochlea model to convert speech into spikes. It has 700 channels where each channel responds mainly to a different frequency range sound. Lower numbered channels generally responds to lower frequencies and higher to higher.

So from the raster spike plot each blue dot represents one spike event produced by a particular channel at a particular time. The horizontal position tells when the spike occurs and vertical which channel it came from. The color of the dot indicates the events polarity since the plot use `coolwarm` color map. The polarity indicates the type or direction of an event, where positive polairty indicate a signal increase and negative a signal decrease.

However since the sensor size (SHD event format) is `(700,1,1)` it only has one polarity value which means that all events have the same polarity and thus all events are shaded blue.

Mandatory question 4:

We use 70 input features, hidden layer of 140 neurons, a LIF after each linear layer.
20 output neurons, one per SHD digit class. Returns Spike and membrane recordings with shape approx:

* `spk2_rec`: `[time, batch, 20]`
* `mem2_rec`: `[time, batch, 20]`

Loss calculated at every timestep since membrane potential provides differentiable class scores wheres spikes are binary.

Accuracy: Since input digits have different durations and are padded, final membrane value may not always be the best classifier output. A more robust approach is to classify using accumulated membrane potentials or output spikes over time, for example



# Changes 



Changed hidden layer input from 140 to 256 

changed optimzer initial LR to 1e-3 

changed schedular factor from 0.5 -> 0.25 and patience from 5 to 2. 

Ok so these changes did really bad, Accuracy dropped from ~42% down to ~9.5%.
