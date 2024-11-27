# Exploring the Daley-Kendall Model using ABMs

A computational modeling and data science project that learns from the Daley-Kendal model to represent a mock simulation tracking the spread of misinformation and disinformation.

Project completed by Lowell Monis in fulfillment of the requirements for an Honors Option for CMSE 202 at Michigan State University, taught by Dr. Nathan Haut during the Fall of 2024.

## Instructions

Please install `imageio` to able to run this code without errors.

`pip install imageio`

The code has been provided on the `code.ipynb` file. A folder named `temp` is created while generating the animation of the simulation. The folder is then deleted with the rest of the frames that were generated. An animation of the model can be viewed in the `animations` folder. New animations can be created using the code given. The generation of the animation may take time, so the live animation can be viewed on the Jupyter notebook interface while it is being generated. You can also disable the creation of the animation by leaving the `gif_name` argument of the `simulate()` function as `None`.

## Objectives

In this project, we intend to create an isolated system that can mimic the spread of rumors.

>Can an agent-based model be created to be representative of the logic of the Daley-Kendall Models, and visualize how a rumor spreads?

The goals of this study are as follows:

1. To explore a version of the Daley-Kendall model, and create an equivalent of the ODE model as an object-oriented ABM.
2. To compare the evolution of agents within a simulation with the expected numbers from solving an initial value problem for the given ODEs.
3. To understand the applications of the model created and its potential drawbacks in modeling the spread of rumors.

## Methodology

To do this, we first understood what we are dealing with by solving the ODE system as follows:

$$\frac{dS}{dt} = -\beta IS$$

$$\frac{dI}{dt} = \beta IS - \gamma I$$

$$\frac{dR}{dt} = \gamma I$$

The following assumptions were made:

- Initial percentage of ignorant people (susceptible population), $S_0 = 0.5$

- Initial percentage of spreaders (infected population), $I_0 = 0.1$

- Initial percentage of stiflers (recovered population), $R_0 = 0.0$

- Interaction rate, $\beta = 0.3$

- Stifling rate, $\gamma = 0.1$

Upon solving the system, one could conclude that the ignorants reduce in number, the spreaders increase and are then wiped out, while the stiflers increase exponentially.

We now create a agent-based model using object-oriented Python programming.

We create a class with the following rules:

1. Only two agents can have a conversation.
2. Each agent has a conversation threshold distance between 1.0 and 3.0 units.
3. Each agent has a memory capacity between 10 and 20 time steps.
4. Each agent can either be an introvert, extrovert, or ambivert.
5. Depending on the type of combinations between each agent and their ability to socialize, a maximum conversation time of either two or five time steps is decided.
6. Each agent has a tendency to gossip, which is either a 1 or a 0.
7. If an ignorant and a spreader interact, and the tendency to gossip of the ignorant is 1, it becomes a spreader. Else, it becomes a stifler.
8. Once the memory time limit of a spreader elapses, an extroverted spreader becomes ignorant, ready for the rumor to be introduced again. An ambivert spreader becomes a stifler, no longer interested in the rumor.

## Results

We were able to make an almost accurate looking model in an isolated environment with no other information being spread. Imagine introducing a rumor about the groom in a wedding party. We were able to represent a variety of folks and how they may think or act. Although this is definitely not representative of a real scenario, we were able to closely achieve the proportions from the ODE, if not exactly.

## Discussion and Conclusion

The applications of this model are far-reaching. Misinformation, and disinformation, sometimes portrayed with new terminology like "alternate truth", is now dominating the world via social media, and sometimes, even mainstream media. It is important that contributions are made to this field in the computational sociology sectors in order to create strategies to counter such dangerous phenomena in the digital world.

This model represents an idealistic scenario. In reality, there are multiple external influences that can affect what actually happens. While I do believe the model did a great job at being mildly representative of a real life scenario, I think the model can be made more accurate with the inclusion of the complete system that includes fact-checkers in the SIR model. Another next step could be using the Maki-Thompson rumor spread model.

## References

1. https://pypi.org/project/imageio/
2. José R.C. Piqueira, Mauro Zilbovicius, Cristiane M. Batistela. (2020) "Daley–Kendal models in fake-news scenario." Physica A: Statistical Mechanics and its Applications, Volume 548, 123406, ISSN 0378-4371, https://doi.org/10.1016/j.physa.2019.123406.
3. OpenAI. Accessed on November 24, 2024 from https://chatgpt.com/. Prompt chain:{'please add a mechanism to this code to create a gif of the animation. DO NOT change the code i have entered.'} 