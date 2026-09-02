# ExpNo 5: Implement Simple Hill Climbing Algorithm

**Name: Mithun Sai P**

**Register Number: 212225100026**

## Aim

Implement Simple Hill Climbing Algorithm and generate a string by mutating a single character at each iteration.

## Theory

Hill climbing is a variant of **Generate and Test** in which feedback from the test procedure is used to help the generator decide which direction to move in the search space.

The feedback is provided in terms of a **heuristic function**.

## Algorithm

1. Evaluate the initial state.

   * If it is a goal state, return it and quit.
   * Otherwise, continue with the initial state as the current state.

2. Loop until a solution is found or there are no new operators left to be applied in the current state:

   * Select an operator that has not yet been applied to the current state and apply it to produce a new state.
   * Evaluate the new state:

     * If it is a goal state, return it and quit.
     * If it is not a goal state but is better than the current state, make the new state the current state.
     * If it is not better than the current state, continue the loop.

---

## Steps Applied

### Step 1

Generate a random string of the length equal to the given string.

### Step 2

Mutate the randomized string one character at a time.

### Step 3

Evaluate the fitness function or heuristic function.

### Step 4

Loop through **Step 2** and **Step 3** until we achieve a score of zero to achieve the **Global Minima**.

---

## Sample Input and Output

### Sample String

```text
Artificial Intelligence
```

### Output

```text
Score: 643  Solution :  8RzF:oG ]%;CPORRMe!zGvk
Score: 609  Solution :  8RzF:oG ]%;CPqRRMe!zGvk
Score: 604  Solution :  8RzF:oG ]%;CPqRRMe!zGqk
Score: 594  Solution :  8RzF:oG ]%;CPqRRWe!zGqk
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk
....................................................
..................................................
................................................
Score: 1  Solution :  Artificial Intelligencf
Score: 1  Solution :  Artificial Intelligencf
Score: 1  Solution :  Artificial Intelligencf
Score: 1  Solution :  Artificial Intelligencf
Score: 0  Solution :  Artificial Intelligence
```

## Program

```python
import random
import string

target = input("Sample String: ")

characters = string.ascii_letters + string.punctuation + " "

# Generate random solution
solution = ''.join(random.choice(characters) for _ in target)


# Calculate score
def score(solution):
    return sum(a != b for a, b in zip(solution, target))


# Hill Climbing
current_score = score(solution)

while current_score > 0:

    # Select a random position
    position = random.randint(0, len(target) - 1)

    # Create a new solution
    new_solution = list(solution)
    new_solution[position] = random.choice(characters)
    new_solution = ''.join(new_solution)

    new_score = score(new_solution)

    # Keep the new solution only if it is better
    if new_score < current_score:
        solution = new_solution
        current_score = new_score

    print("Score:", current_score, "Solution:", solution)

print("\nTarget reached!")
print("Score:", current_score, "Solution:", solution)
```

## Output

```text
Sample String: Artificial Intelligence
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObFm#?c$:ORPlf;
Score: 23 Solution: ,&^|!#VObKFm#?c$:ORPlf;
....................................................
Score: 1 Solution: Artificial In?elligence
Score: 1 Solution: Artificial In?elligence
Score: 1 Solution: Artificial In?elligence
Score: 1 Solution: Artificial In?elligence
Score: 1 Solution: Artificial In?elligence
Score: 1 Solution: Artificial In?elligence
Score: 1 Solution: Artificial In?elligence
Score: 1 Solution: Artificial In?elligence
Score: 1 Solution: Artificial In?elligence
Score: 0 Solution: Artificial Intelligence

Target reached!
Score: 0 Solution: Artificial Intelligence
```

## Result

Thus, the **Simple Hill Climbing Algorithm** was implemented successfully by generating a random string and mutating one character at a time until the target string **"Artificial Intelligence"** was reached with a score of **0**.
