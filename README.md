# streamdeck-action

## Usage Example

```yaml
name: Compile And Release

on:
  push:
    tags:
      - '*' # Only run this if a tag is pushed

jobs:
  build:
    runs-on: [macos-latest] # This action only works on macOS, due to the distribution tool Elgato provides
    steps:
      - uses: actions/checkout@v4
      # Do you stuff to build the project
      - uses: AlexHaible/streamdeck-action@v0.0.3
        with:
          input-directory: "/src/com.elgato.template.sdPlugin" # Where is your code? Usually just the '.com.elgato.template' part needs replacing
          output-directory: "/release" # Where do you want the .streamDeckPlugin file?
      # Create an artifact to download it
      - name: Upload .streamDeckPlugin artifact
        uses: actions/upload-artifact@v4.0.0
        with:
          name: com.elgato.template.streamDeckPlugin # Rename this to suit your plugin
          path: ./release/
```

Simply put the above into a standard Github Actions workflow .yml file, make your edits, and you're off to the races!

## Used by
- [`AlexHaible/beledars-spawn-countdown`](https://github.com/AlexHaible/beledars-spawn-countdown)
