# TFM_UPC
Master Thesis - MESIO - 2025
Solar and Wind Potential Analysis in Europe
# Summary
This work investigates technological, spatial, and temporal complementarities between wind, solar, and electricity demand in Europe through a generalized portfolio-based approach rooted in Modern Portfolio Theory (MPT). It introduces the theoretical basis of MPT for energy planning and uses descriptive statistics to characterize wind and solar resources across the continent. The analysis highlights complementarities across technologies and regions and employs a mean-variance optimization framework solved via quadratic programming to determine optimal renewable energy mixes. This methodology aims to maximize capacity factors and reduce output variability, thus enhancing system reliability through diversification.
In this context, a novel methodology is presented to incorporate electricity demand into a literature-based analysis of wind and solar resource complementarities in Europe. The proposed approach is applied in a case study that focuses on electricity demand metrics and their implications for capacity planning. Demand is examined at multiple temporal scales - yearly, monthly, daily, and hourly - providing a detailed view of consumption patterns across Europe. The study further explores the role of different demand metrics in shaping capacity allocation strategies and presents comparative visualizations of demand dynamics. Using a generalized version of portfolio optimization, it evaluates optimal renewable capacity allocation under various capacity factor constraints, emphasizing regional differences and the use of average demand as a target. Furthermore, the Levelized Cost of Electricity (LCOE) is assessed at the country level to evaluate cost-effectiveness, highlighting opportunities for technological switching to minimize generation costs.
# Data
This project utilizes data from the following sources:
- Renewables.ninja – Provides modeled capacity factors (CFs) for wind and solar energy based on historical weather data across countries.
- ENTSO-E Transparency Platform – Offers real historical generation data and energy demand across European countries.
These datasets provide complementary insights into historical generation patterns and modeled renewable energy performance across regions.
# Key Functions and Analytical Components in R
This project integrates statistical optimization and data visualization to analyze and optimize renewable energy capacity factors across European countries. The following *R functions* and workflows were central to the analysis:

*optimize_portfolio()*:
Custom function applying Modern Portfolio Theory to identify optimal wind and solar capacity mixes. It computes the efficient frontier based on mean capacity factor, standard deviation, and Sharpe ratio, and identifies three key portfolios:

-Minimum variance
-Maximum capacity factor
-Maximum Sharpe ratio

*Visualization with ggplot2*:
A series of visualizations was produced using the ggplot2 package to explore hourly and regional renewable performance:

-Line plots of hourly capacity factors for wind energy 
-Scatterplots of technology-specific capacity factors across hours 
-Efficient frontiers by region
-Stacked bar charts of optimized installed capacity shares by technology and country

*Data manipulation with dplyr and tibble*:
-Used for reshaping, filtering, and aggregating data to prepare inputs for both optimization and plotting.

*Output generation*:
-Figures were saved as .png files using write.png() to systematically store visual results for each portfolio and country.

# Key Functions and Processes in Python Optimization
This project implements an optimization framework to determine the optimal installed capacities of wind and solar energy across European countries, using historical capacity factors and electricity demand. The key components include:

*Optimization Model*
Objective Function (objective): Minimizes the squared error between total energy produced (across both wind and solar) and the maximum electricity demand for each country:

*Solver*
Uses scipy.optimize.minimize() with the 'trust-constr' method for constrained nonlinear optimization.

🔄 Dynamic Target CF Sweep
A loop evaluates different target capacity factors from 0.18 to 0.32, solving a new constrained optimization problem for each value.

For each target CF, the code:
- Solves the constrained optimization
- Extracts the optimal wind/solar mix per country
- Computes Absolute Error between produced energy and demand

📊 Result Aggregation and Visualization
- Absolute Error Aggregation by Region
- Average Absolute Error is computed for four country groups:

Northern Europe
Western/Central Europe
Southern/Eastern Europe
All Countries

*Plotting*
Uses matplotlib to visualize average Absolute Error vs. target CF across regions:

-Facilitates identification of the target CF with the best overall performance.
-Outputs saved as high-resolution PNG files.

💾 Data Requirements
-Capacity Factor Matrix (matrix_CF): Country × Technology matrix (e.g., 29 × 2) with modeled CFs
- Maximum Demand Vector (demand_array): 1D array with demand per country

# Conclusions
This project presents a detailed, data-driven analysis of wind and solar energy dynamics across Europe, revealing the complementary nature of these technologies. Offshore wind stands out as the most stable and productive resource, while solar exhibits high midday output but greater variability. The study highlights strong geographical differences in renewable generation patterns and emphasizes the need for region-specific planning strategies.

By applying a mean-variance optimization framework, the analysis identifies optimal renewable mixes that balance energy output with variability. A target capacity factor (TCF) of around 0.17 is proposed as a practical benchmark for system planning. The results show that current infrastructure often deviates from optimal configurations, underscoring the potential for improvement through better siting, hybrid systems, and storage solutions.

Overall, the findings advocate for flexible, data-informed, and regionally adaptive energy strategies to support the efficient and resilient integration of variable renewable energy sources.
