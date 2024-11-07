<h1 style="text-align:center"><strong><center>Systems Evaluation</strong></h1></center>

This is the section where we validate both systems: CrewAI agentic approach, and the system prompt approach. We have three validators in total: Andrew, Naeim, and myself. My evaluation was conducted as a blind test, meaning I had no prior knowledge of how their systems were implemented.

Let’s now discuss the blind evaluation process. I created an evaluator for each system and ran it on both Naeim's and Andrew's implementations to determine if one system performed better than the other and to help decide which one we should ultimately choose.

The purpose of designing this as a blind evaluation was to ensure objectivity and eliminate bias. By using a blind evaluator, we aimed to verify that the systems weren't inadvertently influenced by the developers' familiarity with their own work or by any emphasis they might have placed on certain aspects over others, potentially overlooking critical areas. This approach helps us confirm that each system performs consistently and effectively across all important factors.

## **Plan Outline System**

The Plan Outline Evaluation component is a critical validation step to ensure that the generated training plans are not only tailored to user-specific goals and constraints but also achievable, safe, and effective. Both systems generate running training plan outlines based on the user’s input, including the user profile, target, and minimum weekly training days. This evaluation process assesses each plan's viability against essential training criteria, yielding a comprehensive assessment of the plan's alignment with user goals and fitness best practices.

**Evaluation Process**

The evaluation function, **evaluate\_plan\_outline\_output**, is used to assess each plan's quality and appropriateness by comparing the system-generated output (plan outline) against user-specific inputs (profile, target, and training days). It is designed to be adaptable to a variety of user goals, providing a dynamic assessment that considers the user's fitness level, time availability, and desired outcomes.

The evaluation is conducted based on the following criteria, each scored out of 100. This scoring breakdown allows for a nuanced understanding of the plan’s strengths and potential areas for improvement:

 **Progression Analysis**:
   - **Weekly mileage progression rate**: Ensures the increase in mileage does not exceed a 10% weekly increase, avoiding overtraining and injury risk.
   - **Workout intensity distribution**: Evaluates the balance between hard and easy workouts to ensure proper training stimuli.
   - **Recovery week placement**: Assesses if recovery weeks are strategically placed to allow for adequate rest and performance gains.
   - **Build/recovery cycle structure**: Verifies if the training includes an appropriate balance of build and recovery phases to support long-term progress.

**Safety Assessment**:
   - **Rest day frequency and placement**: Checks for adequate rest days, preventing burnout and promoting recovery.
   - **Intensity distribution (80/20 rule)**: Ensures that 80% of training is low-intensity, with 20% being high-intensity, aligning with best practices for endurance training.
   - **Impact load management**: Focuses on managing impact load to reduce the risk of injury, particularly for long-distance runners or users with past injuries.
   - **Recovery time between hard sessions**: Evaluates the spacing of hard sessions to allow sufficient recovery and avoid overtraining.
   - **Consideration of user's health conditions**: Assesses how well the plan accounts for any specific health conditions or past injuries that could affect training.

**Feasibility Evaluation**:
   - **Alignment with user's current fitness level**: Verifies if the plan is suitable for the user’s current fitness level, avoiding overtraining or undertraining.
   - **Appropriate training frequency**: Assesses if the training frequency matches the user’s ability to recover and progress.
   - **Realistic pace progressions**: Checks if the pace progressions are realistic and achievable based on the user’s current performance.
   - **Time commitment feasibility**: Evaluates if the required time commitment for training sessions fits into the user’s schedule.
   - **Weather and seasonal considerations**: Considers potential weather or seasonal conditions that could impact training and ensures the plan is adaptable.

**Specificity Verification**:
   - **Goal race alignment**: Assesses how well the plan aligns with the user's specific race or performance goals.
   - **Training intensity appropriateness**: Ensures that the training intensity is appropriate for the user’s target race and fitness level.
   - **Workout type selection**: Verifies that the selected workouts are suitable for the user's goals, such as endurance, speed, or strength.
   - **Race-specific elements**: Ensures the plan includes race-specific training elements, such as pace work, course simulation, or nutrition strategies.
   - **Peak and taper structure**: Evaluates the plan's peak and taper strategy to ensure the user is prepared for their race day performance.

**Structural Integrity**:
   - **Logical week-to-week flow**: Verifies that the training plan has a logical progression from one week to the next, with smooth transitions between phases.
   - **Balance of workout types**: Assesses the balance between different types of workouts (e.g., long runs, interval training, rest days) to ensure a well-rounded approach.
   - **Clear progression pattern**: Ensures that the progression of intensity, volume, and frequency follows a clear and effective pattern.
   - **Appropriate peak and taper timing**: Checks that the timing of peak weeks and taper phases aligns with the user’s target race or event.
   - **Complete coverage of necessary training elements**: Verifies that the plan addresses all necessary components of training, including endurance, speed, strength, and recovery.


**Results of the Evaluation**

| **Criterion**                          | **Andrew’s Average Score**  | **Naeim’s Average Score**  |
|----------------------------------------|-----------------------------|----------------------------|
| **Progression and Training Development** | 84.73%                      | 84.82%                     |
| **Health and Safety Considerations**    | 83.55%                      | 82.39%                     |
| **Plan Feasibility**                   | 83.79%                      | 81.52%                     |
| **Goal Specificity and Clarity**        | 88.21%                      | 87.76%                     |
| **Structural Integrity of Plan**        | 85.42%                      | 85.79%                     |
| **Confidence Score**                    | 84.76%                      | 83.79%                     |
| **Overall Score**                       | **84.76%**                  | **84.21%**                 |


The evaluation results show that both systems perform similarly, with the **Agentic Approach** slightly outperforming the **System Prompt Approach** overall. The **Agentic Approach** excels in health and safety considerations, plan feasibility, and user confidence, providing a more comprehensive approach to addressing user concerns about injury prevention, time constraints, and the practicality of the plan. On the other hand, the **System Prompt Approach** shows slight advantages in progression and structural integrity, offering a more dynamic and well-integrated training plan. Despite these differences, the overall scores for both systems are very close, with the **Agentic Approach** leading by a small margin (84.76% vs. 84.21%). This suggests that while both systems are effective, the **Agentic Approach** is slightly more user-friendly and safety-conscious, while the **System Prompt Approach** offers a more structured and progressive approach.

## **Goal Checker System**

In this section, we evaluate the Goal Checker component in both systems—the Agentic system using Crew AI and system prompt approach—focusing on its ability to assess the achievability of user goals. Specifically, the Goal Checker is tested on the scenario where a user aims to complete a half marathon at an average pace of 05:00 per kilometer within a 12-week training period. We evaluated both systems across a diverse set of 33 user profiles to ensure robust, accurate, and unbiased results.

The primary objective of the Goal Checker is to determine whether the user’s goal is realistic and achievable based on their unique fitness profile, considering factors such as initial fitness level, potential for improvement, and any limitations. This evaluation process is essential to verify that the system provides reliable feedback, independent of any potential developer biases, and accurately interprets varied user profiles without overlooking important details.

To ensure an objective and consistent evaluation, we designed a structured blind evaluation prompt. This prompt guides the system through a step-by-step validation process to assess each system’s response to the goal. The evaluation covers critical aspects, including achievability, consideration of limiting factors, and overall response quality. Here is a breakdown of the criteria:

**Achievability Assessment:** 

- **Goal Feasibility**: Does the response accurately evaluate the achievability of the user’s target pace, distance, and time-frame, considering their current fitness and potential for improvement?
- **Training Days Suggestion**: If the goal is deemed achievable, does the response suggest a realistic number of training days based on the user’s profile, goal, and timeline?

**Consideration of Limiting Factors:**

- **Health and Physical Constraints**: Does the response account for factors like injuries, health conditions, or other considerations that may impact the user’s ability to achieve the goal?
- **Environmental and External Factors**: Does the system address relevant external aspects, such as training facilities, available resources, and other situational factors?

**Critical Review and Re-evaluation:**

- **Accuracy Check:** Each answer undergoes a “why might this be wrong?” analysis to identify potential over- or under-estimations in assessing the user’s potential or situational factors.
- **Self-Critique**: The evaluator rechecks its conclusion, ensuring no overlooked details (e.g., inconsistent training or health risks) affect the assessment.

The prompt is structured to ask the system specific sub-questions to assess achievability, limiting factors, and the overall quality of the response. Based on these sub-questions, the evaluator generates a validation result, a confidence score, and an optional explanation for incorrect responses.

**Results of the Evaluation**


Using this structured prompt, I conducted a comprehensive evaluation of both the **CrewAI Agentic Approach** and the **System Prompt Approach** on 33 user profiles:

-   **CrewAI Agentic Approach**: All 33 cases were marked as valid, with a confidence score of 95%. This indicates that the system consistently provided accurate and reliable feedback across a diverse range of user profiles.
    
-   **System Prompt Approach**: Similarly, all 33 cases passed validation with a confidence score of 95%, demonstrating that this approach also provided accurate and effective responses, matching the CrewAI Agentic Approach in performance.
    

Both systems met the high standards set by the evaluation prompt, consistently producing correct and unbiased results. The success rate across both systems confirms their robustness in accurately assessing diverse user profiles, instilling confidence that each system can reliably guide users toward realistic training goals.
## **Goal Adjuster System**

The Goal Adjuster system plays a vital role in recalibrating user goals to ensure they are realistic and achievable. This evaluation section focuses on assessing how well two systems—Andrew's and Naeim's—perform in adjusting an unrealistic running target. For this test, we set an impossible target: completing a full marathon at a challenging pace of 03:00 per kilometer within just four weeks. Both systems are expected to provide three alternative, achievable goals based on user profiles, each with a suggested minimum number of training days and a descriptive rationale. The evaluation function systematically analyzes the adjusted goals generated by each system to ensure they meet specific quality and feasibility standards. 

The evaluation of the Goal Adjuster System focuses on how well the system adjusts unrealistic user goals and provides achievable, well-structured alternatives. The following updated criteria are used to assess the quality and feasibility of the alternative goals suggested by each system:

**Alternative Targets Quality Check:**
 - **Target Feasibility:** The system suggests exactly three achievable targets based on the user's current fitness data.
 - **Feasibility Assessment:** The targets are assessed against the user's all-out 30-minute pace (defined as the fastest pace a user can maintain for 30 minutes).
 - **Alignment with Original Goal:** The targets should balance ambition with achievability, aligning with the original goal’s intent.
 - **Motivational Guidance:** The targets should represent a realistic yet challenging step up from the user's current performance to ensure they remain motivated.

**Progressive Scale Validation:**
 - **Logical Progression:** The targets should logically scale in difficulty, ensuring each goal is progressively more challenging than the previous one.
 - **Adjustment to User Ability:** Each target must be achievable relative to the user’s current ability and reflect the correct adjustments to avoid injury or over-training.
 - **Gradual Improvement:** The targets should show clear signs of gradual improvement, with appropriate progression in both intensity and volume.

**Pacing Suitability for Race Distance:**
 - **Distance Appropriateness:** The target pace should be suitable for the race distance (e.g., 5K, 10K, half-marathon) the user is training for.
 - **Endurance and Speed Balance:** The pacing should strike a balance between speed and endurance, ensuring the user can sustain the pace over the course of the target race distance.

**Health, Injury Prevention, and Motivation:**
 - **Safety and Injury Prevention:** The system prioritizes user safety, with particular consideration for any past injuries or health conditions.
 - **Motivational Balance:** The goals should be challenging but not overwhelming, ensuring that the user remains motivated and engaged without risking burnout.
 - **Realism:** The targets should align with the user’s current fitness level and overall goals, ensuring the suggested targets are not overly ambitious for the user’s abilities.

**Training Days Validation:**
 - **Training Frequency:** The system recommends a suitable number of training days, with a minimum of 1 day and a maximum of 7 days per week.
 - **Suitability for User's Availability:** The recommended training frequency should match the user's availability, ensuring the plan is feasible.
 - **Consistency Check:** The recommended frequency should align with the target's achievability, considering the user's fitness level, recovery potential, and experience.`
---
## **Results of the Evaluation**

### Comparison of Andrew’s and Naeim’s Goal Checker System Scores

| **Criterion**                            | **Andrew’s Average Score**  | **Naeim’s Average Score**  |
|------------------------------------------|-----------------------------|----------------------------|
| **Alternative Targets Quality Check**    | 87.58%                      | 82.88%                     |
| **Progressive Scale Validation**         | 85.00%                      | 79.39%                     |
| **Pacing Suitability for Race Distance** | 78.79%                      | 72.73%                     |
| **Health, Injury Prevention, and Motivation** | 93.64%                  | 88.94%                     |
| **Description Quality Check**            | 85.36%                      | 78.33%                     |
| **Confidence Score**                     | 86.30%                      | 80.85%                     |


Both the **CrewAI Agentic Approach** and the **System Prompt Approach** performed well across all criteria, with the CrewAI Agentic Approach generally outperforming the System Prompt Approach in most areas. The CrewAI Agentic Approach showed stronger results in areas such as **Alternative Targets Quality Check**, **Progressive Scale Validation**, and **Description Quality Check**, indicating that it provides more comprehensive and accurate feedback for users with varying needs and goals. Additionally, it scored higher in **Confidence Score**, suggesting more reliable and confident assessments.

While the System Prompt Approach also performed well, it scored slightly lower overall, particularly in **Pacing Suitability for Race Distance** and **Progressive Scale Validation**, which may suggest it is less precise in adapting to specific race goals and training progressions. However, the System Prompt Approach performed strongly in **Health, Injury Prevention, and Motivation**, with a score very close to that of the CrewAI Agentic Approach.

In terms of overall performance, the CrewAI Agentic Approach demonstrated a higher degree of consistency and reliability across the various evaluation criteria, making it the stronger performer in this Goal Checker evaluation. Both systems, however, are highly effective and provide accurate assessments of user goals.

## **Goal Recommender System**

In the **Goal Recommender Evaluation**, we assessed the validity and feasibility of the recommended race goals generated by both Andrew’s and Naeim’s systems for a fixed race distance of 10K over a 12-week training period. This evaluation aimed to determine whether the goals set for each user were achievable, realistic, and aligned with safe and effective training principles.

The validation was designed to assess the realism and safety of each system’s recommended goals based on user-specific data and training duration. The evaluation focused on comparing the user’s current fitness, training history, and progression feasibility within the available timeframe. Each recommendation underwent a detailed review to ensure alignment with effective training principles and the user’s personal strengths or limitations.

The evaluation considered several key aspects to validate if the suggested race pace and training plan were suitable for the user. The evaluation prompt was structured to simulate a fitness coach’s thought process, breaking down each recommendation logically and systematically. The following criteria were used:

### Criteria for Evaluation

**Alignment with User Data and History**:

   - **Sub-question:** Does the recommended pace align with the user’s fitness metrics (e.g., recent 30-minute all-out pace, recent sessions, or average speed over similar distances)?
   - Does it reflect the user’s past performance or recent improvements?
   - Cross-check the user’s running history to ensure the recommendation is realistic.
   - **Critique:** Is the recommendation too ambitious or too conservative based on the user's running background?


**Progression Feasibility within Available Time**:

   - **Sub-question:** Is the suggested pace achievable within the remaining training time without risking injury or overtraining?
   - Verify whether the timeline allows for safe, gradual improvements (e.g., 10% weekly increases).
   - **Critique:** Is the recommended progression too aggressive or too slow for the user's current level?

**Pacing for the Specific Race Distance**:

   - **Sub-question:** Is the recommended pace appropriate for the user’s desired race distance (5K, 10K, half-marathon, marathon)?
   - Does the recommendation balance speed and endurance to fit the race distance?
   - **Critique:** Could the pace be too fast, leading to burnout, or too slow, limiting performance?


**Health and Injury Prevention**:

   - **Sub-question:** Does the recommended target prioritize injury prevention?
   - Is there a reasonable progression to avoid overtraining?
   - Does the pace take into account the user’s injury history or health risks?


**Realism and Motivation**:

   - **Sub-question:** Is the recommended pace motivating and realistic?
   - Does it strike a balance between challenge and attainability?
   - Will the user feel encouraged or discouraged by the goal?


**Clarity of Explanation**:

   - **Sub-question:** Is the reasoning behind the recommendation clear and well-justified?
   - Are the links between user fitness, race goals, and pace progression clearly explained?


**Results of the Evaluation**
### Comparison of Andrew’s and Naeim’s Goal Recommender System Scores

| **Criterion**                           | **Andrew’s Average Score**  | **Naeim’s Average Score**  |
|-----------------------------------------|-----------------------------|----------------------------|
| **Alignment with User Data and History**| 81.52%                      | 83.03%                     |
| **Progression Feasibility within Available Time** | 80.00%               | 81.97%                     |
| **Pacing for the Specific Race Distance** | 85.45%                     | 87.42%                     |
| **Health and Injury Prevention**        | 86.06%                      | 87.88%                     |
| **Realism and Motivation**              | 85.30%                      | 86.97%                     |
| **Clarity of Explanation**              | 89.55%                      | 90.76%                     |
| **Confidence Score**                    | 84.58%                      | 86.27%                     |


Both the **CrewAI Agentic Approach** and the **System Prompt Approach** performed well in recommending realistic, achievable, and safe goals for users. The System Prompt Approach slightly outperformed the CrewAI Agentic Approach in several areas, particularly in **Alignment with User Data and History** and **Pacing for the Specific Race Distance**, where it achieved higher scores. Its **Health and Injury Prevention** and **Realism and Motivation** scores were also notably better, suggesting that the System Prompt Approach may better account for user limitations while encouraging achievable challenges.

Conversely, the CrewAI Agentic Approach excelled in **Clarity of Explanation** with a slightly lower but still strong **Confidence Score**. Overall, both systems provided realistic and motivating recommendations for 10K race goals, with the System Prompt Approach achieving higher scores in most criteria. Its slightly higher Confidence Score also suggests that its recommendations may have been perceived as more reliable or reassuring.

In conclusion, both systems met the validation criteria for feasible and motivating training goals, with the System Prompt Approach showing a small but consistent advantage in most areas. Nonetheless, both approaches effectively supported goal-setting for users, promoting a balanced approach to training progression and injury prevention.
