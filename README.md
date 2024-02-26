Important notes:



how the OpenAI API works, and how to create Prompts

we use "***ChatCompletion.create function\***" indicating, at least:

- the model to use 

- a list of messages

  - Each message in the list contains a role and the text we want to send to the model. Example of the list of messages that can be sent using the three available roles:

  - ```
    messages=[
            {"role": "system", "content": "You are an OrderBot in a fastfood restaurant."},
            {"role": "user", "content": "I have only 10 dollars, what can I order?"},
            {"role": "assistant", "content": "We have the fast menu for 7 dollars."},
            {"role": "user", "content": "Perfect! Give me one! "}
        ]
    ```

Temperature: As you know, a language generation model does not always give the same answers to the same inputs. The lower the value of ***temperature\***, the more similar the result will be for the same inputs, even repeating itself in many cases.

> I think it’s worth making a parenthesis to explain in broad terms how  this parameter works in a language generation model. The model builds  the sentence by figuring out which word it should use, choosing it from a list of words that has a percentage of chances of appearing.
>
> For example, for the sentence: ***My car is…\*** the model could return the following list of words:
>
> Fast — 45%
>
> Red — 32%
>
> Old — 20%
>
> Small — 3%
>
> With a value of 0 for temperature, the model will always return the word  ‘Fast’. But as we increase the value of temperature, the possibility of  choosing another word from the list increases.
>
> We have to be careful, because this not only increases the originality, it often increases the “hallucinations” of the model.







Now is the time for the prompt!

This is an LLM model. We are not going to program, we are going to try to  make it behave as we want by giving it some instructions. At the same  time, we must also provide it with enough information so that it can do  its job properly informed.

The prompt, or context, is divided into two parts.

- In the first one, we are indicating how he should behave and what his  objective is. The instructions are that he must act like a bot in a fast food restaurant, and that her goal is to know what the customer wants  to eat.
- In the second part of the prompt, we give the composition of the  restaurant’s menu. An element can have more than one price, we do not  indicate what these different prices correspond to. You will see in the  conversations that the model, without more information, finds out that  each one corresponds to a different size of the plate.