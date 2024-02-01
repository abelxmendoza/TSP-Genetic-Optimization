# Traveling Salesman Problem (TSP) Solution Using Genetic Algorithm

## Overview

This repository hosts a Python-based implementation aimed at solving the Traveling Salesman Problem (TSP) through a Genetic Algorithm (GA). Developed as part of a technical interview challenge for Gray Matter Robotics, this project sought to harness Genetic Algorithms for optimizing the TSP, which involves finding the shortest possible route that visits each city once and returns to the origin city.

![1706762904811](image/README/1706762904811.png)

**The Genetic Navigator: The Salesman's Odyssey**


Navigate 'The Genetic Navigator: The Salesman's Odyssey,' where the
age-old puzzle of the traveling salesman finds resolution in the elegant
 strands of genetic algorithms. This artwork captures the essence of an
epic journey through a complex network, with each connection
representing a step closer to the ultimate solution, guided by the
evolutionary wisdom of genetics.


## Project Status: Incomplete/Unfinished

The project is currently incomplete due to performance bottlenecks encountered during development. While substantial progress was made, including passing several test cases, the implementation faced significant slowdowns due to external HTTP requests used for distance calculations.

## Try It Out in Google Colab

To explore the code, run experiments, and see the algorithm in action, you can access the project through a Google Colab notebook. This interactive environment allows you to modify, execute, and interact with the code directly from your web browser, without the need for any local setup.

Click the link below to open the notebook in Google Colab:

[https://colab.research.google.com/drive/1wn09nbjjfisoyYNYA2yOQiigcUjvpBvW?usp=sharing](https://colab.research.google.com/drive/1wn09nbjjfisoyYNYA2yOQiigcUjvpBvW?usp=sharing)

### Getting Started in Colab

1. **Open the Notebook:** Click the link above to open the notebook in Google Colab.
2. **Copy to Drive:** To edit and run the notebook, make a copy by going to `File` > `Save a copy in Drive...`.
3. **Run the Code:** Navigate through the cells and run them individually by clicking the play button, or run all cells in sequence via `Runtime` > `Run all`.
4. **Experiment:** Feel free to modify parameters, experiment with different inputs, and observe the outcomes to gain deeper insights into the genetic algorithm's behavior and performance.

For any questions or issues encountered while using the notebook, please refer to the Google Colab documentation or reach out through the project's issue tracker.

## Key Challenge

The primary bottleneck was identified in the distance calculation function from `utils.py`, `calculate_haverstine_distance_hidden`, which relied on HTTP requests to an external service for determining the Haversine distance between two locations. Each call to this service significantly slowed down the algorithm, impacting the overall feasibility of the solution within the given time frame.

### Problematic Function:

```python
def calculate_haverstine_distance_hidden(loc_1: Location, loc_2: Location) -> float:
    params = {"lat_1": loc_1.latitude, "lon_1": loc_1.longitude, "lat_2": loc_2.latitude, "lon_2": loc_2.longitude }
    r = requests.get(url = 'https://<external-service-url>', params = params)
    return r.json()['distance']
```

This function's reliance on external HTTP requests for each distance
calculation introduced a significant performance bottleneck, making the
algorithm run extremely slow.

## Approach and Solutions

Initial attempts to solve the TSP utilized the provided `calculate_haverstine_distance_hidden` function from `utils.py`. However, due to the performance issues, an alternative approach was explored that eliminated the need for HTTP requests, potentially improving the algorithm's efficiency. Unfortunately, this new method could not be fully implemented and tested within the project's timeframe.

## Future Directions

To address the identified bottleneck, future work will focus on:

* Fully integrating and testing the alternative distance calculation method that does not rely on external HTTP requests from calculating the haversine distance.
* Optimizing the genetic algorithm to enhance its efficiency and effectiveness in solving TSP instances.
* Extending the project's scope to include a broader range of test cases and potentially parallelizing distance calculations to further improve performance.

## Acknowledgments

This project was initiated as part of a technical interview process with Gray Matter Robotics, aiming to explore innovative algorithmic solutions to complex optimization challenges such as the TSP.
