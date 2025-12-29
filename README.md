# Simulation-Basketball-Game-

import random
import time


team_1 = {
    "name": "Bobcats", "score": 0, "possessions": 0
}

team_2 = {
    "name": "Hornets", "score": 0, "possessions": 0
}

team1 = team_1["name"]
team2 = team_2["name"]

print(f" Game: {team1} vs {team2}")
time.sleep(.15)
print("Tip-off!")
time.sleep(.5)
print(f"Won by {team1}!")

team1_score = team_1["score"]
team2_score = team_2["score"]

tot_poss = 100

def team_one():
    team1 = team_1["name"]
    

    number = random.random()
    turnover_percent = 0.117
    shooting_possession_percent = 1 - turnover_percent 
    field_goal_attempts = 92.7
    two_point_attempts = 53.9
    three_point_attempts = 38.8

    two_point_probability = shooting_possession_percent * (two_point_attempts / field_goal_attempts)
    three_point_probability = shooting_possession_percent * (three_point_attempts / field_goal_attempts)

    aggregated_percents_1 = turnover_percent + two_point_probability
    aggregated_percents_2 = aggregated_percents_1 + three_point_probability

    two_point_percentage = .559
    three_point_percentage = .374

    off_rebounds = 10.6
    off_rebounds = off_rebounds * 1.1
    missed_shots = (two_point_attempts * (1 - two_point_percentage)) + (three_point_attempts * (1 - three_point_percentage))
    off_reb_percent = off_rebounds / missed_shots

    t1_points = 0
    t1_poss = 0

    t1_fgm = 0
    t1_fga = 0

    tot_poss = 100



    if tot_poss:
        if number < turnover_percent:
            print(f"{team1} turnover!")
            time.sleep(.2)
            t1_poss += 1

        elif turnover_percent < number < aggregated_percents_1:
            digit = random.random()
            if digit < two_point_percentage:
                time.sleep(.2)
                print(f"{team1} makes 2 pointer!")
                t1_points += 2
                t1_poss += 1
                t1_fgm += 1
                t1_fga += 1

            else:
                time.sleep(.2)
                print(f"{team1} misses 2 pointer!")
                t1_fga += 1
                value = random.random()
                if value < off_reb_percent:
                    time.sleep(.2)
                    print(f"{team1} gets offensive rebound!")
                else:
                    t1_poss += 1
        elif aggregated_percents_1 < number < aggregated_percents_2:
            digit = random.random()
            if digit < three_point_percentage:
                time.sleep(2)
                print(f"{team1} makes 3 pointer!")
                t1_points += 3
                t1_poss += 1
                t1_fgm += 1
                t1_fga += 1

            else:
                time.sleep(.2)
                print(f"{team1} misses 3 pointer!")
                t1_fga += 1

                value = random.random()
                if value < off_reb_percent:
                    time.sleep(.2)
                    print(f"{team1} gets offensive rebound!")
                else:
                    t1_poss += 1
        else:
            print("ERROR")
    team_1["score"] += t1_points
    team_1["possessions"] += t1_poss




def team_two():
    number = random.random()
    turnover_percent = 0.117
    turnover_percent = turnover_percent * 0.9
    shooting_possession_percent = 1 - turnover_percent 
    field_goal_attempts = 92.7
    two_point_attempts = 53.9
    three_point_attempts = field_goal_attempts - two_point_attempts

    two_point_probability = shooting_possession_percent * (two_point_attempts / field_goal_attempts)
    three_point_probability = shooting_possession_percent * (three_point_attempts / field_goal_attempts)

    aggregated_percents_1 = turnover_percent + two_point_probability
    aggregated_percents_2 = aggregated_percents_1 + three_point_probability

    two_point_percentage = .559
    three_point_percentage = .374

    off_rebounds = 10.6
    missed_shots = (two_point_attempts * (1 - two_point_percentage)) + (three_point_attempts * (1 - three_point_percentage))
    off_reb_percent = off_rebounds / missed_shots

    t2_poss = 0
    t2_points = 0
    

    t2_fgm = 0
    t2_fga = 0

    tot_poss = 100

    team2 = team_2["name"]

    if tot_poss:
        if number < turnover_percent:
            print(f"{team2} turnover!")
            time.sleep(.2)
            t2_poss += 1
        elif turnover_percent < number < aggregated_percents_1:
            digit = random.random()
            if digit < two_point_percentage:
                time.sleep(.2)
                print(f"{team2} makes 2 pointer!")
                t2_points += 2
                t2_poss += 1
                t2_fgm += 1
                t2_fga += 1

            else:
                time.sleep(.2)
                print(f"{team2} misses 2 pointer!")
                t2_fga += 1
                value = random.random()
                if value < off_reb_percent:
                    time.sleep(.2)
                    print(f"{team2} gets offensive rebound!")
                else:
                    t2_poss += 1
        elif aggregated_percents_1 < number < aggregated_percents_2:
            digit = random.random()
            if digit < three_point_percentage:
                time.sleep(.2)
                print(f"{team2} makes 3 pointer!")
                t2_points += 3
                t2_poss += 1
                t2_fgm += 1
                t2_fga += 1

            else:
                time.sleep(.2)
                print(f"{team2} misses 3 pointer!")
                t2_fga += 1

                value = random.random()
                if value < off_reb_percent:
                    time.sleep(.2)
                    print(f"{team2} gets offensive rebound!")
                else:
                    t2_poss += 1
        else:
            print("ERROR")
    team_2["score"] += t2_points
    team_2["possessions"] += t2_poss

def main_game():
    while team_1["possessions"] < tot_poss and team_2["possessions"] < tot_poss:
        team_one()
        team_two()

    # Game over — show result
    print(f"\nFinal Score:")
    print(f"{team_1['name']}: {team_1['score']}")
    print(f"{team_2['name']}: {team_2['score']}")

    if team_1["score"] > team_2["score"]:
        print(f"{team_1['name']} wins!")
    elif team_2["score"] > team_1["score"]:
        print(f"{team_2['name']} wins!")
    else:
        print("It's a tie!")

if __name__ == "__main__":
    main_game()
