# Renouveau OTA Updates List

A list of the latest updates for each officially supported device

## Submitting updates (for device maintainers only)

When you compile an updated Renouveau build for your device, you'll received a generated line of JSON as part of the success output (which is also saved to `/out/target/product/{codename}/{codename}.json`). This JSON contains the response data that the LineageOS Updater app built-in to Renouveau will expect when checking for this new update. Once you've uploaded your updated Renouveau build to the GitHub Releases section for your device's manifest repository, you should fork this repo, overwrite the data in your device's specific JSON file, and then submit a pull request for review.

An example of this JSON file might look like the below output for the `nobleltetmo` device:
```JSON
{ "response": [ { "datetime": 1561144107, "filename": "Renouveau-v9.0-20190621-nobleltetmo-Release.zip", "id": "9c4d083fd9221e9fd79841916bc93c8c8428ae0be4efda19bbd92d5f57dfb41d", "romtype": "Release", "size": 669041481, "url": "https://github.com/RenouveauOS/android_device_samsung_nobleltetmo/releases/download/v9.0-20190621-Release/Renouveau-v9.0-20190621-nobleltetmo-Release.zip", "version": "9.0"  }]}
```

When uploading a new release to the GitHub releases section for your device's manifest repository, make sure you're tagging the releases according to the `v$1-$2-$3` format, where `$1` is the Renouveau version number of your build, `$2` is the date of your build, and `$3` is the type of your build. All three of these values can be inferred from the generated filename of your build, as seen by the example JSON above. If you fail to do so, your device will not receive an OTA update for this build, as we will simply reject your pull request for your updated JSON.
