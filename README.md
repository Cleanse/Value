# The Meta Value HTML Property
`<meta property="value:[type]" content="[value_(type).json/xml]">`

## Goal
The future of monetizing content has been moving towards a user supported content model (known as *"value for value"* 
in some communities). Websites like YouTube, Patreon, Twitch, and others have semi-adopted this model with their 
subscription and donation features, but still are restrictive due to "brand safety" concerns.

Giving the visitors optional methods of funding their favorite content will create less of a need to censor content 
(as the major corporations are forced to do in order to please the advertiser) and be less reliant on the mega corp 
websites as hosts; returning the power and know-how to individuals.

## The `value:[type]` Property
The `value:[type]` attribute suggests to the visitor that an optional method of funding has been suggested in place of 
more common forms of monetizing content (eg. advertising or pay walls). The content using this attribute, in spirit, 
should be free to all visitors with only a suggestion of the importance in supporting free and non-censored content.

The properties designate the type of payment method so that supporting browsers or extensions can quickly decide on 
how to handle the `content` URL.

## Example Usage
Suggested format(*), with same server url enforcement for security purposes:
```html
<meta property="value:lightning" content="//yoursite.com/value_lightning.json">
<meta property="value:paypal" content="//yoursite.com/value_paypal.json">
```
(*) Multiple value tags can be added.

Example BTC Lightning JSON:
```json
{
  "type": "lightning",
  "method": "keysend",
  "suggested": "0.00000005000",
  "frequency": "weekly",
  "recipients": [
    {
        "name": "author",
        "type": "node",
        "address": "036557ea56b3b86f08be31bcd2557cae8021b0e3a9413f0c0e52625c6696972e57",
        "split": 67
    },
    {
      "name": "developer",
      "type": "node",
      "address": "036557ea56b3b86f08be31bcd2557cae8021b0e3a9413f0c0e52625c6696972e57",
      "split": 32
    },
    {
      "name": "hosting",
      "type": "node",
      "address": "036557ea56b3b86f08be31bcd2557cae8021b0e3a9413f0c0e52625c6696972e57",
      "split": 1
    }
  ]
}
```

## Community Support
Each "monetary community" can create their own suggested JSON API structures for Open Source browser software or their 
custom extensions to handle the `value` property.

Optional custom payment values and frequencies can be built into the browser/extension settings' options in the case 
that users prefer to tip more or less than the defaults.

### Inspiration
Here is the current proposal for the podcast:value namespace:
```xml
<podcast:value type="lightning" method="keysend" suggested="0.00000005000">
    <podcast:valueRecipient name="podcaster" type="node" address="036557ea56b3b86f08be31bcd2557cae8021b0e3a9413f0c0e52625c6696972e57" split="99" />
    <podcast:valueRecipient name="hosting company" type="node" address="036557ea56b3b86f08be31bcd2557cae8021b0e3a9413f0c0e52625c6696972e57" split="1" />
</podcast:value>
```
- [https://github.com/Podcastindex-org/podcast-namespace](https://github.com/Podcastindex-org/podcast-namespace)