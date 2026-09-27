name: Motoran APK

on:
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Java
        uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: "17"

      - name: Extract project
        run: |
          mkdir project
          unzip -q Motoran_Cloud_Build_FIXED.zip -d project

      - name: Build APK
        run: |
          GRADLEW=$(find project -name gradlew -type f | head -n 1)
          ROOT=$(dirname "$GRADLEW")
          cd "$ROOT"
          chmod +x gradlew
          ./gradlew assembleDebug

      - name: Upload APK
        uses: actions/upload-artifact@v4
        with:
          name: Motoran-APK
          path: "**/app/build/outputs/apk/debug/app-debug.apk"
