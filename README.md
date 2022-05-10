# About

This is a script to facilitate cough phase timing and amplitude analysis.

# Files

cough_phase_timing_script.s2s - Script to run in Spike2.
cough_phase_timing_script.s2s - Compatable with Spke2 V7.
template.xlsx - Excel file to copy script output into. Remember to use data->text to column

# Instructions

1. Run Script
2. Open/Select file (make sure the data file is the active window)
3. Finding good ABD Channel, Fix CO2 Lag, Create Analysis Window
    1. Click “Set Up”
    2. Type spike time in dialog box to find a trial/event
    3. Select your favorite ABD channel in the tool bar (both are measured but this will make the better one red) after selecting the chosen channel appears in the left of the toolbar.
    4. Use Cursor 1 & 2 to fix CO2 lag. Find a cough or augmented breath (or swallow?). Cursor 1 typically should go at the start of expiration/end of I (ESPR is good for this w/ cough). Cursor 2 should go where the CO2 starts to rise. Use best judgement for matching the appropriate CO2 burst. The calculated etco2 lag is displayed in the left of the toolbar.
    5. A new window is generated with colored Dia/ABD channels. Duplicate channels are created and original channels are rectified and smoothed based on values in the script. Original window is hidden. "Set Up Done!" printed at left of toolbar.
4. Going to a Trial
    1. Click “Go To Trial” button
    2. Enter Trial Number (TB 5 would be “5”)
    3. Enter approximate spike time for trial (no need to be exact)
    4. Use a number to represent a condition i.e. “0” for control.
    5. Trial number should appear in left of toolbar
5. Defining the stimulus period
    1. Click “Stim On/Off”
    2. Cursors 1-4 will appear. Cursor 2 is bound to Cursor 1 and Cursor 4 to Cursor 3. The position of Cursor 2 and Cursor 4 are what is actually measured.
    3. Start by moving Cursor 1 and Cursor 3, when near a TextMark then Cursor 2 and Cursor 4 will “snap” to the TextMark. You can fine tune Cursor 2 and Cursor 4 (typically only need to adjust Cursor 2 if you see the stimulus causing a behavior or noise before the TextMark. Once Cursor 2 and Cursor 4 are in position click “Ok” in the tool bar. The Stimulus duration is recorded and displayed to the left of the toolbar. Cursors 1-6 are created with Cursor 1 @ The Stimulus On position.
6. Placing Cursors
    1. Definition for cursors
        - Cursor 1 – Start of Inspiration. Variable = i_emg_start
        - Cursor 2 – Last I peak on inspiratory channel tied to Cursor 3 and precedes it by the smoothing constant. I typically only need to move cursor 3 (but look at cursor 2). You can fine tune cursor 2 if needed. Cursor 2 & 3 typically match up very well. Variable = i_emg_peak
        - Cursor 3 – End of raw inspiratory channel. Variable = i_emg_end
        - Cursor 4 – End of ballistic abdominal EMG. Variable = e1_ballistic_end
        - Cursor 5 – End of “Active” abdominal EMG. Variable = e1_active_end
        - Cursor 6 – End of E2/Start of next I phase.  e2_end
7. Recording/Measuring Cough (finally!)
    1. After cursors are placed click the appropriate button. They all measure the same thing but record to a variable if there is another behavior in the E2 phase
        - Standard Cough – Just a normal cough.
        - Cough -> Swallow – Swallow in E2.
        - Cough -> Breath – Breath in E2 (also if this is the last cough you can place this at the first post cough breath).
        - Cough -> Misc. APB – Any other airway protective behavior. Also good if there is something odd.
    2. After clicking the appropriate button data will be recorded. Keep an eye out for any anomalies that need to be fixed manually after (like a noise spike or multiple inter-cough behaviors). The Cough Number will be printed in the left of the toolbar (to note when one needs to be fixed of if you lose track). The script will move Cursor 1 to where Cursor 6 was and then use the previous phase durations to “guess” where the cursors should go for the subsequent cough. These always need to be changed but it gets theme close).
    3. Each button press prints that cough’s data to the Log window (if you want to see it click Window -> Log)
    4. Alternate between Step 6 and Step 7 until trial ends. 
8. Trial End
    1. Copy Data from Log to Excel (and I typically delete the Log window after)
    2. If you have another trial to measure just start from “Step 4”
9 Ending the Script.
    1. Just click “Quit”

	
	
	

