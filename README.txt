########################################################################################
# AUTHOR: John Arcarese
########################################################################################
# DATE: 02/23/2021
########################################################################################
# PREREQUISITES:
########################################################################################
# The objective of the babysitter kata; produce a method where: 
# The inputs are the babysitter’s start time and the babysitter’s end time (in HH:MM(AM/PM).
# The output will be a single value denoting the amount which the babysitter is owed.
#
# The babysitter works the following shifts:
# START SHIFT:    start-of-shift time through to bedtime.
# BEDTIME SHIFT:  bedtime through to midnight.
# MIDNIGHT SHIFT: midnight through to end-of-shift time.
#
# Each shift pays at the following rates:
# START SHIFT:    $12/hr.
# BEDTIME SHIFT:  $8/hr.
# MIDNIGHT SHIFT: $16/hr.
#
# Since the babysitter is paid at different rates, we need to determine how many hours are worked under each shift
# and calculate the total amount owed to the babysitter.
#########################################################################################
# ASSUMPTIONS:
#########################################################################################
# 1. As bedtime is undefined, bedtime will be randomly generated to be within the range of 5:00PM through 4:00AM - this is being done
#    since the Kata did not specify the age of the children or suggested a bedtime range. 
#
# 2. If bedtime is after midnight, the rate for the midnight shift will supersede the rate for the bedtime “shift”.
# 
# 3. If the children are already sleeping at the start-of-shift, then the rate for bedtime shift will supersede the rate for the start-of-shift.
#
# NOTE: Assumptions 2 and 3 suggest the following order of precedence for calculating the rate:
#    - Midnight shift
#    - Bedtime shift
#    - Regular shift
# 
# 4. Once the children are asleep, they sleep through to the end-of-shift.
#
# 5. The only situation where time is worked but unaccounted for, is if the babysitter:
#   - starts work late (resulting in a fractional hour).
#   - leaves work early (resulting in a fractional hour). 
#
# In these cases, the hours worked would be rounded down to the nearest hour (as per the kata, only whole hours of work are paid for).
#########################################################################################
# SOLUTION OVERVIEW:
#########################################################################################
# 1. Validate all inputs, using the following constraints:
#    a. All input is in the form of HH:MM(AM/PM) and as per the kata be between 5:00PM to 4:00AM.
#    b. start time must be on or after 5:00PM, but before 4:00AM.
#    c. bedtime must be no earlier than the start-of-shift (I'm putting in this constraint, in the event that the code is refactored to specify a bedtime).
#    d. bedtime must be earlier than the end-of-shift (I'm putting in this constraint, in the event that the code is refactored to specify a bedtime).
#    e. bedtime can be the same as the start-of-shift or end-of-shift (I'm putting in this constraint, in the event that the code is refactored to specify a bedtime).
#    f. end time must be after start time and no later than 4:00AM.
#
# 2. To work with each input, we'll convert them to a numeric representation to simplify calculations.
#
# 3. Calculate the whole hours for each shift:
#    - from start-of-shift to bedtime shift
#    - from bedtime shift to midnight shift
#    - from midnight shift to end-of-shift.
#
# 4. Calculate the sub-totaL for each shift by multiplying each shift’s hours by the base rate for each shift.
#
# 5. Sum up the sub-totals of each shift for the total rate (in the event no hours were worked, then return a total rate of zero).
#    - Each shift will calculate the sub-total (by multiplying the ) and then add those sub-totals to return the total salary.
#    - If no hours are worked (based on the input), then a salary of 0 will be returned.
#########################################################################################
# INSTRUCTIONS FOR RUNNING SOLUTION:
#########################################################################################
# maven command to be added here when project is completed.
#########################################################################################
