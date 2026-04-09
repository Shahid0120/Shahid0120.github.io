---
layout: single
classes: wide
title: "Introduction to Pricing Strategies"
categories:
    - Strategy
author_profile: true
---

# Understanding the World of Pricing Analytics

I have been recently working with my of my friend's at universitory whose studying marketing and was working on creating wanted to do a critical analysis for an organisation to use Value-based pricing model. 

Recently I have had a buzz over the word 'criticial anlaysis' from works, and on our senior spoke about dissecting report and undertsanding the pro's and con's. This got me really exited, when I heard this word again in the context of product strategy. 



Haugom (2021) argues that pricing strategies can qualitatively be placed into the following categories:

- Cost-plus pricing (CP): Calculating costs and adding a margin when setting the price.  
- Market-based pricing (MB): Setting prices based on competitors’ actions.  
- Customer-driven pricing (CD): Placing the customer at the center of the pricing decision.  
- Value-based pricing (VB): Setting the price based on estimates of how customers value the product or service.  

Implicitly, when creating a pricing strategy—or building a model—one must incorporate all four aspects into a unified approach. Conceptually, we can think of the pricing function as a combination of these four components:  

$$
\text{Pricing Strategy}(w_1, w_2, w_3, w_4) = w_1 \cdot CP + w_2 \cdot MB + w_3 \cdot CD + w_4 \cdot VB
$$  

This is, of course, an extremely simplified representation. It assumes linearity and no interdependence among the different pricing methods, which is not functionally accurate in practice. However, it effectively illustrates the conceptual idea Haugom aimed to explain: that an integrated pricing strategy involves balancing multiple dimensions of pricing strategies simultaneously.

## Econometric Pricing Analytics – Elasticity

Diving deeper into our pricing function, Paczkowski (2018) presents a two-layered pricing strategy:

$$
\text{Pricing Strategy}(w_i) = \text{function(Pricing Level, Pricing Structure)}
$$

$$
\text{Pricing Strategy}(w_i) = w_1 \cdot CP + w_2 \cdot MB + w_3 \cdot CD + w_4 \cdot VB
$$

- **Pricing structure** refers to *how the pricing is designed*, for example, subscription-based or dynamic pricing.  
- **Price level** refers to *how much you charge for the product*, e.g., a coffee costs \$5.


### Pricing Structure vs Price Level

**Pricing structure** refers to how the pricing is designed—for example, subscription-based or dynamic pricing.  
**Price level**, on the other hand, concerns how much you charge for the product, e.g., a coffee costs $5.

---

### Obtaining Data

Two methods of obtaining data for pricing analytics:

- **Quantitative Data**: Experimental and observational  
- **Qualitative Data**: In-depth interviews, expert opinions, and focus groups  

Using quantitative data, one can build **statistical econometric models** based on the economic paradigm of consumer demand.

Within quantitative data, there are two distinctions:

- **Observational data** (aka revealed preference data): Refers to actual customer behavior  
- **Experimental data** (aka stated preference data): Refers to customers explicitly stating their preferences  

---

### Role of Quantitative Data in Pricing Analytics

Paczkowski (2018) justifies the role of quantitative data as acting like a **prior** (referring to Bayesian statistical thought), providing additional information to aid in our statistical model. It acts as a starting point to ensure our model is accurate. Alone, qualitative data cannot form the basis of a pricing model.

---

### Three Layers of Quantitative Pricing Analytics

Paczkowski (2018) separates pricing analytics into three distinct layers:

- **Layer 1 – Theory foundation**: Economic theory of consumer demand  
- **Layer 2 – Data analysis**: Data cleaning and transformation  
- **Layer 3 – Statistical model**: Non-parametric or parametric modeling  

This means that our statistical model (Layer 3) is **founded on economic theory** (Layer 1).

---

## Other Approaches to Obtain a Pricing Strategy

### Van Westendorp's Price Sensitivity Meter (1976)

This technique determines consumer price preference through a series of four questions:

1. At what price would you consider the product to be **so expensive that you would not consider buying it**? (Too expensive)  
2. At what price would you consider the product **so low that you would feel the quality couldn't be very good**? (Too cheap)  
3. At what price would you consider the product **starting to get expensive, so that it is not out of the question, but you would have to give some thought to buying it**? (Expensive/High Side)  
4. At what price would you consider the product to be a **bargain—a great buy for the money**? (Cheap/Good Value)  

The cumulative frequency is plotted for each, and then a recommended price is interpreted from the intersection points.

---

### Gabor-Granger Method

- Present 5 different price points to a consumer.  
- The consumer chooses the top two they would consider buying.  
- Then the consumer is re-tested with new price points based on the previous answers until they consistently indicate the **“definitely buy”** and **“probably buy”** price points.  

This method finds the **optimal price range** where consumers are most likely to purchase.

---

# Conclusion

This concludes the introduction to pricing analytics. In the next blog, we will dive deeper into the **statistical model introduction** as described by Paczkowski (2018).

### References 

Haugom, E., & Alnes, P. K. (2021). Essentials of Pricing Analytics: Tools and Implementation with Excel . Routledge.

Paczkowski, W. R. (2018). Pricing analytics: Models and advanced quantitative techniques for product pricing. Routledge.