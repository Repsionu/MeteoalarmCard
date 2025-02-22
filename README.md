# Meteoalarm Card

[![version](https://img.shields.io/npm/v/meteoalarm-card?label=version)](https://www.npmjs.com/package/meteoalarm-card) [![hacs badge](https://img.shields.io/badge/HACS-default-orange.svg)](https://hacs.xyz) [![build status](https://img.shields.io/github/workflow/status/MrBartusek/MeteoalarmCard/Lint)](https://github.com/MrBartusek/MeteoalarmCard/actions) [![downloads](https://img.shields.io/github/downloads/MrBartusek/MeteoalarmCard/total?color=brightgreen)](https://github.com/MrBartusek/MeteoalarmCard/releases)

By default [Home Assistant](https://www.home-assistant.io/) does not provide any card for [Meteoalarm integration](https://www.home-assistant.io/integrations/meteoalarm/). This simple card shows you the current active meteorological warnings.

![cover](https://i.imgur.com/jsLOGIv.png)

## Installing

### HACS

We recommend installing meteoalarm card via [Home Assistant Community Store](https://hacs.xyz)

Just search for `Meteoalarm Card` in `Frontend` tab.

### Manual Installation

1. Download `meteoalarm-card.js` file from the [latest release](https://github.com/MrBartusek/MeteoalarmCard/releases/latest).
2. Put `meteoalarm-card.js` file into your `config/www` folder. You can use _File Editor_ add-on.
3. Add reference to `meteoalarm-card.js` in Lovelace. There's two way to do that:
   1. **Using UI:** [Navigate to Lovelace Resources](https://my.home-assistant.io/redirect/lovelace_resources/) → Click Plus button → Set _URL_ as `/local/meteoalarm-card.js` → Set _Resource type_ as `JavaScript Module`.<br>
   **Note:** If you do not see the Resources Tab, you will need to enable _Advanced Mode_ in your [User Profile](https://my.home-assistant.io/redirect/profile/)
   2. **Using YAML:** Add following code to `lovelace` section.
      ```yaml
      resources:
        - url: /local/meteoalarm-card.js
          type: module
      ```
4. Add `custom:meteoalarm-card` to Lovelace UI as any other card.

## Using the card

After completing installation you can add this card like any other to your dashboard.

1. Navigate to your dashboard → click 3 dots in the top left corner.
2. Select _Edit Dashboard_
3. Click _+ New Card_ button
4. Select `Custom: Meteoalarm Card`
5. Select meteoalarm entity. If you don't see one make sure you have configured [Meteoalarm integration](https://www.home-assistant.io/integrations/meteoalarm/)
```yaml
type: 'custom:meteoalarm-card'
entity: 'binary_sensor.meteoalarm'
```

## Supported languages

This card supports translations. Please, help to add more translations and improve existing ones. Here's a list of supported languages:

<!-- Languages are sorted alphabetically -->
- English (Default language)
- Deutsch (German)
- Eesti (Estonian)
- Français (French)
- Italiano (Italian)
- Nederlands (Dutch)
- Polski (Polish)
- Español (Spanish)
- [_Your language?_](./CONTRIBUTING.md#how-to-add-translation)

## Supported integrations

This card supports many other integrations.

- [Core Meteoalarm](https://www.home-assistant.io/integrations/meteoalarm/) - Home Assistant core integration based on ATOM Feed.
- [Core Météo-France](https://www.home-assistant.io/integrations/meteo_france/) - Home Assistant core integration based on Météo France alert.
- [xlcnd/meteoalarmeu](https://github.com/xlcnd/meteoalarmeu) - RRS Feed alternative for countries that does not use ATOM anymore [_Read more_](https://github.com/xlcnd/meteoalarmeu/issues/1).
- [_New integration?_](https://github.com/MrBartusek/MeteoalarmCard/issues/new/choose)

Currently the card will try to auto detect the "sourceType" of your entity but in case this doesn't work or you want to manually override this value just add "sourceType" key into your card configuration and choose one of these type.
In case of problem check you use the right entity for each integration.

---

| Integration        | SourceType   | Entity                     |
| ------------------ | ------------ | -------------------------- |
| Core Meteoalarm    | meteoalarm   | binary_sensor.meteoalarm   |
| Core Météo-France  | meteofrance  | sensor.XX_weather_alert    |
| xlcnd/meteoalarmeu | meteoalarmeu | binary_sensor.meteoalarmeu |

---

Like this for example

```yaml
type: 'custom:meteoalarm-card'
entity: 'sensor.75_weather_alert'
sourceType: 'meteofrance'
```

## Contributing

Want to contribute to the project?

First of all, thanks! Check [contributing guideline](./CONTRIBUTING.md) for more information.
