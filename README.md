# TownGas (HK) Statistic Home-Assistant Custom-Component 

## Prerequisite
- TownGas Subscriber
- TownGas website credentials

## For `Home Assistant Container`
1. Download `custom_components/towngas` here
2. SSH or SFTP into your Home-Assistant server
3. Locate `configuration.yaml`
4. Locate `custom_components` in the same directory. Create it if not exist 
5. Put the downloaded `towngas` into `custom_components`
6. Restart Home-Assistant

## For `Home Assistant Operating System (with HACS)`
1. Setup `HACS` https://hacs.xyz/docs/setup/prerequisites
2. In `Home Assistant`, click `HACS` on the menu on the left
3. Select `integrations`
4. Click the menu button in the top right hand corner
5. Choose `custom repositories`
6. Enter `https://github.com/thematrixdev/home-assistant-towngas` and choose `Integration`, click `ADD`
7. Find and click on `TownGas` in the `custom repositories` list
8. Click the `DOWNLOAD` button in the bottom right hand corner
9. Restart Home-Assistant

## Configure in Home-Assistant
1. Add these in `configuration.yaml`
```
sensor:
  - platform: towngas
    name: 'TownGas' # whatever name you like
    username: '' # TownGas web site username
    password: '' # TownGas web site password
    timeout: 30 # connection timeout in second
```
2. Restart Home-Assistant

## Common problem
- Single entity only. More than one `towngas` entry will cause problems
- For slower hardware device, `TIMEOUT` may happen. Increase `timeout` in `configuration.yaml`

## Debug
- SSH
- `docker logs -f homeassistant`
- Look for `TownGas` wordings

## Use SSH on Home Assistant Operating System
1. Click on your username on UI
2. Turn on `Advanced Mode` on the right
3. Go to `Add-ons` -> `Add-on store`
4. Install `SSH & Web Terminal` (the community version)
5. On `Info` tab of `SSH & Web Terminal`, turn off `Protection mode`
6. On `Configuration` tab, enter a `password`, change `sftp` to `true`
7. On `Configuration` tab, turn on `share_sessions`. `Save`
8. On `Info` tab click `START`
9. SSH to `hassio@IP` with the configured password

## Development environment
- Ubuntu 22.04

## Testing environment
- Home Assistant Container 2022.7.5
- Home Assistant Operating System 2022.8.7