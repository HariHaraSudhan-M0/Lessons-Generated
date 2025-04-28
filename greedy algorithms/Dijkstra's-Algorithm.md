Ever found yourself wanting the quickest way to your favorite candy in a store? Imagine there's a way to find the shortest path every time. That's what **Dijkstra's Algorithm** does! It's like a smart guide that helps you find the quickest way in a world full of paths.

### Learning Objectives

In this lesson, you'll learn:

*   What **Dijkstra's Algorithm** is and what it does.
*   When you can use it to solve problems.
*   How to use it to find the shortest paths in simple situations.
*   Solve easy problems about finding the shortest path.
*   How **Dijkstra's Algorithm** helps with bigger problem-solving ideas.

---

## Introduction to Dijkstra's Algorithm

Imagine you are trying to find the fastest route to your friend's house. There are many ways to get there, but some routes might be longer because of traffic or road work. **Dijkstra’s Algorithm** is like a super helper that finds the shortest and fastest way to reach your friend, considering all the different routes and travel times.

**Dijkstra's Algorithm** is a simple way to find the shortest paths from one starting point to all other points in a network, especially when the distances are positive. It's used in apps like Google Maps and in managing computer networks. You don't need to know what **networks** are right now; just think of it as a way to find the quickest route on a map!

## Understanding Networks

Before we dive into the algorithm, let’s talk about **networks**. Think of a **network** like a map of your city. In our **network**:

*   **Nodes**: These are the places, like your home, your school, or a store. We call these "nodes."
*   **Edges**: These are the roads that connect the places. We call these "edges."

Each road (**edge**) has a distance (**weight**), showing how long or costly it is to travel that road. The **weight** could be the length of the road or the time it takes to drive it. This distance (**weight**) is important for **Dijkstra’s Algorithm** because it helps us find the “cheapest” way to get from one place to another.

## The Core Idea Behind Dijkstra's Algorithm

Imagine you're standing at your starting point, like your house. **Dijkstra's Algorithm** helps you find the shortest path to all the other places in the network, one step at a time.

Here’s the main idea:

1.  **Start**: Begin at your starting point.
2.  **Explore**: Look at all the places you can go to directly from where you are.
3.  **Choose**: Pick the nearest place you haven't visited yet.
4.  **Repeat**: Keep doing this until you've found the shortest path to every other place.

**Dijkstra’s Algorithm** uses a **greedy** approach. This means it always picks the best option *right now*, without worrying too much about the future. It's like always choosing the closest candy in the store. It might seem like a simple approach, but it guarantees that you'll find the shortest path in networks where all the distances are positive.

## Step-by-Step Explanation of Dijkstra's Algorithm

Let’s break down **Dijkstra's Algorithm** into simple steps:

1.  **Setup**:
    *   Write down how far away each place is from your starting point. Start with 0 for your starting point (since you're already there) and "infinity" (meaning "very far away" or "unknown") for all other places.
    *   Make a list of all the places you haven't visited yet.
2.  **Looking Around**:
    *   For the place you're currently at, look at all its neighbors (the places you can directly reach from here) that you haven't visited yet.
    *   Figure out how far away those neighbors are from your starting point if you go through your current location.
    *   If any of these new distances are shorter than what you had written down before, update the distances.
3.  **Done for Now**:
    *   When you've checked all the neighbors of your current location, mark it as visited so you don't come back here again.
4.  **Next Stop**:
    *   Look at all the places you haven't visited yet and pick the one that's closest to your starting point. Go there and repeat from step 2.
5.  **Finished**:
    *   Keep going until you've visited every place, or until you've found the place you were trying to reach.

## Example Scenario

Let’s use a simple example to understand **Dijkstra’s Algorithm**. Imagine we have five cities (A, B, C, D, E) connected by roads with different lengths. We want to find the shortest path from city A to all the other cities.

Here’s how the cities are connected and how far apart they are:

*   A to B: 4
*   A to C: 2
*   B to C: 1
*   B to D: 5
*   C to D: 8
*   C to E: 10
*   D to E: 2

Let's use **Dijkstra’s Algorithm** to find the shortest paths:

1.  **Setup**:
    *   Distances: A=0, B=∞, C=∞, D=∞, E=∞
    *   Unvisited: {A, B, C, D, E}
2.  **First Step (Start at A)**:
    *   From A, we can go to B (distance 4) or C (distance 2).
    *   Update distances: B=4, C=2
    *   Mark A as visited.
3.  **Second Step (Move to C, the closest unvisited city)**:
    *   From C, we can go to B (distance 1), D (distance 8), or E (distance 10).
    *   Update distances: B=2+1=3 (shorter than 4), D=2+8=10, E=2+10=12
    *   Mark C as visited.
4.  **Third Step (Move to B, the closest unvisited city)**:
    *   From B, we can go to D (distance 5).
    *   Update distances: D=3+5=8 (shorter than 10)
    *   Mark B as visited.
5.  **Fourth Step (Move to D, the closest unvisited city)**:
    *   From D, we can go to E (distance 2).
    *   Update distances: E=8+2=10 (shorter than 12)
    *   Mark D as visited.
6.  **Fifth Step (Move to E, the last city)**:
    *   No more unvisited cities.
    *   Mark E as visited.

Shortest paths from A:

*   A to B: 3
*   A to C: 2
*   A to D: 8
*   A to E: 10

So, in simple terms, we start from one city and gradually find the shortest way to each of the other cities by always choosing the closest unvisited city. This way, we can efficiently determine the shortest paths from our starting point to all other destinations.

---

## Implementing Dijkstra's Algorithm

Let's explore how you can use **Dijkstra's algorithm** with **pseudo code** to solidify your understanding of the algorithm and its practical application.

First, you'll need to represent the network.

```
Network = {
    'A': [('B', 4), ('C', 2)],
    'B': [('C', 1), ('D', 5)],
    'C': [('D', 8), ('E', 10)],
    'D': [('E', 2)],
    'E': []
}
```

Here’s how you can write it in simple steps (**pseudo code**):

```
Function Dijkstra(Network, Start):
    // Setup:
    For each Node in Network:
        Distance[Node] = Infinity  // Unknown distance
    Distance[Start] = 0  // Starting point
    Unvisited = all Nodes in Network

    // Find shortest paths:
    While Unvisited is not empty:
        Current = Node in Unvisited with smallest Distance
        Remove Current from Unvisited

        For each Neighbor and Weight in Network[Current]:
            NewDistance = Distance[Current] + Weight
            If NewDistance < Distance[Neighbor]:
                Distance[Neighbor] = NewDistance

    Return Distance  // Shortest distances from Start to all nodes

// Example usage:
Network = {
    'A': [('B', 4), ('C', 2)],
    'B': [('C', 1), ('D', 5)],
    'C': [('D', 8), ('E', 10)],
    'D': [('E', 2)],
    'E': []
}

StartNode = 'A'
ShortestDistances = Dijkstra(Network, StartNode)
Print "Shortest distances from " + StartNode + ": " + ShortestDistances
```

## Real-World Applications

Dijkstra's Algorithm is used in many things you use every day:

*   **Maps**: When you use Google Maps to find the shortest route, it uses Dijkstra’s Algorithm.
*   **Internet**: It helps send data across the internet in the fastest way.
*   **Delivery**: Companies like UPS and FedEx use it to plan the best delivery routes.
*   **Games**: Video games use it to help characters find the quickest way around the game world.

## Advantages and Limitations

Like everything, Dijkstra's Algorithm has good and bad sides.

**Advantages:**

*   It’s good at finding the shortest path from one place to all other places.
*   It’s not too hard to understand and use.
*   It works well for many real-world problems.

**Limitations:**

*   It doesn’t work if you have negative distances (**negative edge weights**).
*   It can be slow for very big networks.
*   It only finds the shortest paths from one starting point.

---

## Summary

In this lesson, you've learned about **Dijkstra's Algorithm**, a simple tool for finding the shortest paths in networks. You've seen how it works step by step, learned how to use it, and seen where it's used in the real world. Understanding **Dijkstra's Algorithm** is a great first step in learning about network **algorithms** and solving tricky problems.

Now that you know how Dijkstra's Algorithm works, can you think of a real-world problem you could solve using it?

Additional Resources for you:

*   [https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm)