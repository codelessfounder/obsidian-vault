---

---

---

shareable links:

- Users can share their wins with people, creating free marketing 

---

Sports betting

---

high value item scanning (cars, watches, boats etc)




---

- [x] Pricing using web search API (openAI)

---

- [x] Multiple cart items with one scan 
- [ ] Geo locate web search results
- [x] Update cart display pre game
- [x] Update cart display during game to display cart, not cart_items
- [ ] Update initial display
- [x]  add disco ball to image analysis 
- [ ] Outcomes need to be based on an RNG engine
- [ ] Update font 
- [ ] Update Google meta data 


---

Geo web search prices:

# **User location**

To refine search results based on geography, you can specify an approximate user location using country, city, region, and/or timezone.

- The `city` and `region` fields are free text strings, like `Minneapolis` and `Minnesota` respectively.
- The `country` field is a two-letter [ISO country code](https://en.wikipedia.org/wiki/ISO_3166-1), like `US`.
- The `timezone` field is an [IANA timezone](https://timeapi.io/documentation/iana-timezones) like `America/Chicago`.

Note that user location is not supported for deep research models using web search.

Customizing user location

`import OpenAI from "openai";
const client = new OpenAI();

const completion = await client.chat.completions.create({
    model: "gpt-4o-search-preview",
    web_search_options: {
        user_location: {
            type: "approximate",
            approximate: {
                country: "GB",
                city: "London",
                region: "London",
            },
        },
    },
    messages: [{
        "role": "user",
        "content": "What are the best restaurants around Granary Square?",
    }],
});
console.log(completion.choices[0].message.content);`

source- openAI docs

---

Promotions for different brands - sneaker brands etc 

---


Head to head social betting 

---

cart item cross of the list

- when a user wins the amount of an item in the cart, the UI should expand the cart dropdown and cross off something from the list, like they’ve gotten it for free. 

---

It doesn’t really feel like you win or you lose - your balance just goes up/down


---

Personal analytics

- I want to be able to track how I’ve been doing since I opened my account 
- 2nd tab needs to be way more detailed

Make wins shareable 

---

Admin dashboard with analytics linked to Disco email 

Disco AI Pay agent 

---

Disco API 

*every product needs an API *

- other ecommerce stores can plugin Disco into their site to have users play for instant discounts


---

the ability to gamble your win if you get 100% of your items

AI RNG decider 

[[AI PRNG]]

---

search function to scour the internet for product to buy and then play for in Disco 

---

sweepstakes version of disco for the US - Disco Bucks 

- see [Stake.us](http://stake.us/) vs stake.com

---

URL analysis for Desktop 

---

Desktop version?


---

### cart context

- Ghost progressbar that shows where the user COULD get to if they place a certain bet size
- crossing off each item 
- animated cart draining

---

sounds 

---

perplexity item search with AI 

- consider new ways to connect what the user is buying/bought with Disco - uploading a photo is only one possible way. 

---

need to focus on the success of winning UI - why does it matter that I win?

---

security updates to make:


**Recommendations (Priority Order):**

1. **URGENT**: Remove hardcoded credentials or move to environment variables
2. **HIGH**: Remove unused client-side RNG functions (generateBombIndex, HomePage Math.random)
3. **HIGH**: Move all session total calculations to Edge Functions (server-side)
4. **MEDIUM**: Add Supabase Row Level Security (RLS) policies to prevent direct database manipulation
5. **MEDIUM**: Implement rate limiting on Edge Functions to prevent abuse
6. **LOW**: Demo balance is cosmetic, but consider moving to session storage instead of window object

---

Double or nothing after you get to 100% 

---

Limits on bet amounts

---

next games:

7. Dice 
8. Slots 
9. Plinko


---

Sounds

---

Disco casino machines that is prettty much like an internet acfe

- people come into gamble and win items 

---

Disco coin to buy things on the site with

[Introduction to SHFL | SHFL Tokenomics](https://shfl.shuffle.com/)

gitbook 

---

giveaways like LCMT+

- houses, cars, boats
- Entries are purchased with DSCO

---

discount game API for restaurants (look into eatclub model)



