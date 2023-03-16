# Weather Bot with Rasa 3.x

Learn about NLU Features of Rasa by building a bot, it uses a spacy pipeline for entity extraction and also a Synonym Mapper

## Replicating ATO-616

I am trying to replicate [ATO-616](https://rasahq.atlassian.net/browse/ATO-616). This bot uses spacy's GPE (geopolitical entity) type to extract location names from the utterances. I have created a synonym for Austria which includes,

```
- synonym: Austria
  examples: |
    - vienna
    - salzburg
    - innbruck
    - graz
```

The expected behaviors,
1. From utterance `what's the weather in berlin`, the extracted entity and value is `berlin`
1. From utterance `what's the weather in austria`, extracted entit and value is `austria`.
1. From utterance `what's the weather in vienna`, extracted entity is `vienna`, value of the entity is `Austria`

Note that the extracted value was `austria` in lowercase in the second example but an uppercase `Austria` in the third one.

Here's the bot output,
```
Bot loaded. Type a message and press enter (use '/stop' to exit): 
Your input ->  what's the weather in berlin
The weather at berlin is 12C with overcast skies
Your input ->  what's the weather in austria
The weather at austria is sunny with a chance of rain in the evening, bring your umbrella!
Your input ->  what's the weather in london
I do not know what's the weather at londo
Your input ->  what's the weather in salzburg
The weather at Austria is sunny with a chance of rain in the evening, bring your umbrella!
Your input ->  what's the weather in spain
It is raining heavily at spain right now
Your input ->  what's the weather in Austria
I do not know what's the weather at Austria
Your input ->  what's the weather in vienna
I do not know what's the weather at Austria
Your input ->  /stop
```
