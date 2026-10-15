# my-flo

ESPHome configuration for the iFLO bottle dispenser (ESP32-S2). The unit runs standalone (on-device schedule, clock and limits); Home Assistant is an optional controller and history front end.

- Hardware notes, pin map and protocol info: https://github.com/jaas666/my-flo/wiki
- Config: [esphome/iflo.yaml](esphome/iflo.yaml). Draft, not yet tested on hardware.

## Development environment

All tooling runs in a container, so nothing needs installing on your machine except Docker.

**VS Code:** open the folder and choose "Reopen in Container" (needs the Dev Containers extension).

**Command line:**

```
cp esphome/secrets.yaml.example esphome/secrets.yaml   # then edit the values
docker compose run --rm esphome esphome config iflo.yaml
docker compose run --rm esphome esphome compile iflo.yaml
```

The first compile downloads the ESP-IDF toolchain (about 2 GB) into a Docker volume; later builds reuse it. The container builds only. To flash a unit, take the generated firmware file from `esphome/.esphome/build/iflo-dispenser/build/` (`firmware.factory.bin`) and flash it from your host, for example with the ESPHome web flasher in Chrome.
