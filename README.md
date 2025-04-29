## Set up remote integration

# Run the Gradle task to create the framework:

./gradlew :abmixer:assembleAbMixerXCFramework
cd abmixer/build/XCFrameworks/release
zip -r AbMixer.xcframework.zip AbMixer
swift package compute-checksum AbMixer.xcframework.zip


# Remove SMP cache:

rm -rf ~/Library/org.swift.swiftpm
rm -rf ~/Library/Caches/org.swift.swiftpm

# Check SMP dependencies

swift package reset && swift package show-dependencies --format json