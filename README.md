# REHASH Tool
​
Welcome to the REHASH Adaptation Profiler. Here you will find all the relevant information on how to operate and utilize this tool for developing and testing new heuristics. Note that this tool is still a work in progress, so unforeseen errors and bugs may exist. We are fixing bugs as we are integrating more and more applications.
​
#### General guidelines for using REHASH-explorer

i. If the page does not render properly on your screen, please zoom in/out until it fits on your screen. The task graph can occasionally go off screen or the statistics and configuration sections can occasionally overlap. This will make it seem as though the "Execute" and "Adapt" buttons are not working. Try zooming in/out or moving the screen around to the proper point where it is not obscured.

ii. Be patient as the simulation is running, it may take a while to complete (usually one minute).

iii. The accuracy plot also take some time to render properly after the execution is finished.

iv. Whenever you want to try a new configuration (IV surface, heuristic, etc.) close the browser window and access the page again in a new window. Changing configuration in the old tab may not work.
​
#### Simulating with REHASH-explorer
​
REHASH-explorer is currently integrated with MNIST application and there are two different ways you can run it 
 1) Without Adaptation
 2) With Adaptation
​
To run the application without adaptation, do the following:

i. Click on the gear button (top right) and select the desired IV surface. All five IV surfaces used in the paper are available in REHASH-explorer.

ii. Skip directly to step 3 and press "Execute" button.

iii. The page will be frozen while running the simulation. Wait for the simulation to end and note down the statistics reported.

iv. You can repeat the same steps with a different IV surface but following the general guidelines mentioned above.
​
After simulating MNIST without adaptation, you can now run it with heuristic based adaptation and compare different settings. For that, you need to configure the simulation by following below steps. 

i. Click on the gear button (top right) and choose the IV surface

ii. Adjust the "History Array Size" slider; this will determine how many values can be stored of a particular signal from previous app completion cycles. For reference, we use a history size of 2 for most of our experiments on MSP430. (Note: you MUST select a non-zero size for the simulation to work)

iii. Adjust the "Step Size" slider; this will determine the amount by which up or down adaptation will be triggered for a particular execution cycle. For reference, we use a step size of 1 for most of our experiments on MSP430 so that we don't adapt too much immediately. (Note: you MUST select a non-zero size for the simulation to work)

iv. Enter equation for "Adapt Up" and "Adapt Down" and press "enter" key to see the equations rendered. Note that the all possible equations are still unknown and we are adding additional support for new equations currently. The variable names for the adaptation equations MUST conform to the following list of possible variable names. The signals and their corresponding variable names are as follows

| Signal              | History Variable       | Average Variable           |
|---------------------|------------------------|----------------------------|
| On-Time             | ```s_onTime[n]```      | ```avgOnTime```            |
| Off-Time            | ```s_offTime[n]```     | ```avgOffTime```           |
| App-Completion-Time | ```s_appCompTime[n]``` | ```avgAppCompletionTime``` |
| Task-Count          | ``` s_taskCount[n]```  | ```avgTaskCount```         |
| Power-Failure-Count | ```s_pFC[n]```         | ```avgpowerFailureCount``` |
​
Where, the length of the array is History Size + 1. 0th index is the most recent signal value, and last index (n-1) is the oldest. Additionally, your equations MUST have either a ">" or "<" symbol in order for the tool to work. Following are some examples that you can use to run the simulation.
​
| Signal              | Adapt-Up                                    | Adapt-Down                                  |
|---------------------|---------------------------------------------|---------------------------------------------|
| On-Time             | ```s_onTime[0]``` < ```avgOnTime```         | ```s_onTime[0]``` > ```avgOnTime```         |
| Off-Time            | ```s_offTime[0]``` < ```avgOffTime```       | ```s_offTime[0]``` > ```avgOffTime```       |
| App-Completion-Time | ```s_appCompTime[0]``` < 940                | ```avgAppCompletionTime``` > 940            |
| Task-Count          | ``` s_taskCount[0]``` < ```avgTaskCount```  | ``` s_taskCount[0]``` > ```avgTaskCount```  |
| Power-Failure-Count | ```s_pFC[0]``` < ```avgpowerFailureCount``` | ```s_pFC[0]``` > ```avgpowerFailureCount``` |

v. Toggle "Adapt" button

vi. The page will be frozen while running the simulation. Wait for the simulation to end and note down the statistics reported. If the executions are taking longer, check your equations to ensure that they conform to the necessary standards.

vii. Check the accuracy of each classification w.r.t changing energy. If it is following the trend of energy, the heuristic is good. Otherwise repeat the process with a different heuristic.

