## 5.2 Pseudocode
```
Function ComputePriorityScore(revenue, timeRemaining, serviceLevel):
    score = 0.5 * revenue + 0.3 * (1 / timeRemaining) + 0.7 * serviceLevel
    return rounded score

Function ReadCSV(filepath):
    Initialize empty list of shipments
    For each line in the CSV file:
        Parse id, revenue, timeRemaining, serviceLevel, weight
        Compute priorityScore using ComputePriorityScore()
        Add shipment to the list
    Return list of shipments

Function KnapsackOptimization(shipments, maxWeight):
    Initialize 2D array dp[n+1][W+1] for dynamic programming
    Initialize 2D array keep[n+1][W+1] to track selections

    For i from 1 to n:
        For w from 0 to W:
            If shipment[i-1].weight <= w:
                include = shipment[i-1].priorityScore + dp[i-1][w - weight]
                exclude = dp[i-1][w]
                If include > exclude:
                    dp[i][w] = include
                    keep[i][w] = true
                Else:
                    dp[i][w] = exclude
            Else:
                dp[i][w] = dp[i-1][w]

    Backtrack using keep[][] to get list of selected shipments
    Return selected shipment IDs, total weight, and total score
```
