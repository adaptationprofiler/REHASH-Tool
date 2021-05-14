# REHASH Tool

Welcome to the REHASH Adaptation Profiler.  Here you will find all the relevant information on how to operate and utilize this tool for your benefit.  Note that this tool is still a work in progress, so unforseen errors and bugs may exist.  Use this tool at your own discresion.

The first step in operating our tool is setting up your customized configurations

 1) Move the History Array Size slider and Adaptation Step Size slider to your desired size.  Note that you MUST select a non-zero size for each of these values for the tool to work.

 2) Input your Adaptation Equations for Adapt Up and Adapt Down.  This step is optional depending on your choice for Step 3.  To see your equations rendered, type your equations manually into the text box and hit the "enter" key to view.  Note that the full range of equations that are possible are still unknown.  We are adding additional support for new equations currently.  Your variable names for the Adaptation Equations MUST conform to the following list of possible variable names: s_onTime[n], avgOnTime, s_offTime[n], avgOffTime, s_appCompTime[n],avgAppCompletionTime, s_taskCount[n], avgTaskCount, s_pFC[n], avgpowerFailureCount. Additionally, your equations MUST have either a ">" or "<" symbol in order for the tool to work.

 3) Toggle Adaptation/No Adaptation using the button

 4) Hit the "execute" button.  While the tool is performing it's calculations, the page will be frozen.  The screen will be unfrozen when your results are ready.  On average, this takes around 1 minute.  If you find that excecutions are taking longer, check your conditions above to ensure that they conform to the necessary standards.

 5) See your results displayed graphically and in the statistics section.

Note: To change IV surfaces, navigate to the gear symbol on the upper right hand corner of the screen.  There you will see a popup.  Select your IV surface from the list provided.

There are several known bugs: 1) You must refresh the page on every iteration to ensure accuracy and consistency.  2) The accuracy plots do not render immidiately.  3) The task graph can occasionally go off screen. 4) The statistics and configuration sections can ocassionally overlap.  This will make it seem as though the execute button is not working.  Try moving the screen around to the proper point where it is not obscured, and repeat. 


