# Spike and Faye's Constrained Sum Game

Spike and Faye are playing an enhanced version of the Sum Game called the Constrained Sum Game. They start with a number \(N\), and their goal is to reach a target number \(T\). They take turns, with Spike going first. The game can be explained as:

1. On their turn, the player chooses any proper divisor \(d\) of \(N\) (except \(N\) itself) and subtracts it from \(N\).
2. The new value of \(N\) is then used for the next round.
3. If a player cannot make a valid move (i.e., \(N\) has no proper divisors), they lose the game.
4. The player must reach the target number \(T\) exactly. If a player makes a move that results in \(N\) being less than \(T\), they lose the game.

The players are gods of number theory and always play optimally. Your task is to determine the winner of each game given the starting value \(N\) and the target number \(T\).

## Input Format

- The first line contains an integer \(t\) (\(1 \leq t \leq 100\)) representing the number of games.
- The next \(t\) lines each contain two integers \(N\) and \(T\) (\(2 \leq T < N \leq 10^9\)) representing the starting value and the target number for each game.

## Output Format

- For each game, print “Spike” if Spike wins, or “Faye” if Faye wins.

## Constraints

- \(2 \leq T < N \leq 10^9\)

## Example

**Input:**
3
10 2
15 5
20 4

**Output:**

Spike
Faye
Spike


## Explanation

- In the first game, Spike can subtract 8 from 10 to reach 2.
- In the second game, no matter what divisor Spike chooses, Faye can always force a win.
- In the third game, Spike can subtract 16 from 20 to reach 4.
