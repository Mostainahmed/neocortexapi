# ML22/23-13 Investigate Influence of parameter MaxNewSynapseCount

## Introduction

The parameter MaxNewSynapseCount plays a crucial role in the functioning of Hierarchical Temporal Memory (HTM) networks, particularly in the context of the Temporal Memory (TM) algorithm. This project aims to explore how variations in ```MaxNewSynapseCount``` affect learning efficacy and prediction accuracy within an HTM network specifically in ```Multisequencelearning```. Understanding this influence is pivotal for optimizing HTM configurations to enhance performance on specific tasks.

## Brief Summary

- **Investigated the Influence of `MaxNewSynapseCount` Parameter**: Explored how different settings of `MaxNewSynapseCount` impact the learning efficiency and prediction accuracy in Hierarchical Temporal Memory (HTM) networks.

- **Modified the `MultiSequenceLearning` Class**: Adapted the constructor to accept `MaxNewSynapseCount` as a parameter, allowing dynamic experimentation with various synapse counts.

- **Conducted Systematic Experiments**: Performed a series of experiments with varying `MaxNewSynapseCount` values to observe the parameter's effect on the network's ability to learn and predict sequences.

- **Implemented Detailed Logging**: Enhanced the experiment code to log detailed information about each run, including start and end times, configuration settings, learning cycles, and accuracy results.

- **Analyzed Learning Speed and Prediction Accuracy**: Compared the number of learning cycles required and the prediction accuracy achieved at different `MaxNewSynapseCount` settings.

- **Generated Comparative Results**: Produced tables summarizing the learning speed and prediction accuracy across various `MaxNewSynapseCount` settings, providing clear insights into the parameter's impact.

- **Utilized the NeoCortexApi Framework**: Leveraged the capabilities of the NeoCortexApi to simulate HTM networks and implement the temporal memory algorithm with custom `MaxNewSynapseCount` settings.

- **Observed Performance Trends**: Identified trends in how increased `MaxNewSynapseCount` values can lead to faster learning and higher accuracy, albeit with diminishing returns at higher settings.

- **Drew Key Conclusions**: Concluded that `MaxNewSynapseCount` is a critical parameter for optimizing HTM networks, with a significant influence on learning capabilities and prediction performance.

- **Laid Groundwork for Future Work**: Established a foundation for further exploration into HTM parameter tuning, suggesting avenues for additional studies on other HTM configurations and their effects on network performance possible over the Cloud as in the local machine it consumes more resources.


## Architecture:

![Architecture](images/architecture_image.png)

Flow Chart of the work process:

![Untitled Diagram drawio](https://github.com/Mostainahmed/variable-i/assets/20146137/aa25fd5e-7ae4-40a2-97e0-43f97505a20e)

Figure: Work process flow chart

Temporal Memory Architecture:

![image](images/UnderstandingTM.jpg)

## Approach

Our work approach encompasses a comprehensive analysis, starting with a theoretical overview of HTM's TM algorithm and identifying the expected impact of ```MaxNewSynapseCount``` on ```Multisequencelearning``` and its ```Run()``` . We proceed with a systematic experimentation phase, wherein we alter ```MaxNewSynapseCount``` across a range of values and observe its effect on ```Multisequencelearning``` 's learning speed and prediction accuracy.

## Implementation details

A significant adjustment in our approach was the modification of the MultiSequenceLearning class, specifically to introduce flexibility in setting the MaxNewSynapseCount. This parameter controls the maximum number of new synapses the TM algorithm can create for each cell that becomes active during learning.

### Constructor Update
To facilitate experimental variation of ```MaxNewSynapseCount```, we modified the constructor of ```MultiSequenceLearning```:

```csharp
public MultiSequenceLearning(int maxNewSynapseCount)
{
    this.maxNewSynapseCount = maxNewSynapseCount;
}


```
This alteration allows each experiment run to specify a different ```MaxNewSynapseCount```, enabling a systematic analysis across a range of values.

### Experiment Configuration
Each experiment instance configures an HTM network with the given MaxNewSynapseCount, alongside other essential parameters within the HtmConfig setup:

```csharp
HtmConfig cfg = new HtmConfig(new int[] { inputBits }, new int[] { numColumns })
{
    // Other configuration settings omitted for brevity
    MaxNewSynapseCount = this.maxNewSynapseCount,
};

```
### Experiment Execution

The ```Program.cs``` file orchestrates the execution of learning experiments with varying ```MaxNewSynapseCount``` settings. For each experiment, a set of sequences is learned, and the system's predictive accuracy is evaluated.

Running Experiments with Different Parameters
Experiments are initiated with specific ```MaxNewSynapseCount``` values, allowing us to observe and compare the effects of this parameter on learning outcomes:

```csharp
RunMultiSequenceLearningExperiment(20);

```

### Data Logging and Result Generation

To capture the experiment outcomes, we introduced logging within the ```RunExperiment``` method of ```MultiSequenceLearning```. This includes writing the start time, ```MaxNewSynapseCount``` setting, cycle information, match accuracy, and the experiment's end time to a text file:

```csharp
using (StreamWriter writer = new StreamWriter(filePath, true))
{
    // Logging experiment details
    writer.WriteLine($"Experiment Start: {DateTime.Now}");
    writer.WriteLine($"MaxNewSynapseCount: {cfg.MaxNewSynapseCount}");
    // Additional details and results logging
}

```

## 


