<h1 align="center">Kotlin Shimmer effect</h1></br>

<p align="center">
📱 This is a Modifier extension called "Shimmer effect"
</p>
<br>

![Banner](https://cdn.discordapp.com/attachments/774360587391860769/1106160370789388328/fjzdkfjepz.png)

## Stats

![](https://img.shields.io/tokei/lines/noe-gif/Dating-app-React-Native?color=orange&label=Total%20Lines&logo=kotlin&logoColor=white)
[![](https://img.shields.io/github/downloads/noe-gif/Dating-app-React-Native/total?color=orange&label=Total%20Downloads%20(GitHub)&logo=github&logoColor=white)](https://tooomm.github.io/github-release-stats/?username=noe-gif&repository=Dating-app-React-Native)
[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Fnoe-gif%2FDating-app-React-Native&count_bg=%239A3DC8&title_bg=%23555555&icon=tencentweibo.svg&icon_color=%23E7E7E7&title=Total+Visits&edge_flat=false)](https://hits.seeyoufarm.com)
[![Release](https://img.shields.io/github/v/release/noe-gif/Dating-app-React-Native?color=52be80&label=Release)](https://github.com/noe-gif/Dating-app-React-Native/releases)
![](https://img.shields.io/github/languages/count/noe-gif/Dating-app-React-Native?color=white&label=Languages)
![](https://img.shields.io/github/license/noe-gif/Dating-app-React-Native?color=red&label=License)
![](https://img.shields.io/badge/Minimum%20SDK-23%20(Marshmallow)-839192?logo=android&logoColor=white)
![](https://img.shields.io/badge/Target%20SDK-30%20(Android%2011)-566573?logo=android&logoColor=white)
[![Crowdin](https://badges.crowdin.net/inure/localized.svg)](https://crowdin.com/project/inure)

# QR code scanner

This extension will take any kind of composable unit in parameter and apply to it's shape a shimmer styles animation. Often seen when loading interface components in today's software.

<p align="center">
<img src="assets/presentation.gif" alt="androiddevnotes logo"></img>
</p>

## Installation

Add below dependancy in application build.gradle
```gradle
dependencies {
    implementation 'androidx.core:core-ktx:1.7.0'
    implementation 'androidx.lifecycle:lifecycle-runtime-ktx:2.3.1'
    implementation 'androidx.activity:activity-compose:1.3.1'
    implementation "androidx.compose.ui:ui:$compose_ui_version"
    implementation "androidx.compose.ui:ui-tooling-preview:$compose_ui_version"
    implementation 'androidx.compose.material:material:1.2.0'
    testImplementation 'junit:junit:4.13.2'
    androidTestImplementation 'androidx.test.ext:junit:1.1.5'
    androidTestImplementation 'androidx.test.espresso:espresso-core:3.5.1'
    androidTestImplementation "androidx.compose.ui:ui-test-junit4:$compose_ui_version"
    debugImplementation "androidx.compose.ui:ui-tooling:$compose_ui_version"
    debugImplementation "androidx.compose.ui:ui-test-manifest:$compose_ui_version"
}
```

Implementation of shimmerEffect Modifier extension in activity

```kotlin
/**
* Modifier extension
*/
    fun Modifier.shimmerEffect(): Modifier = composed {
    var size by remember {
        mutableStateOf(IntSize.Zero)
    }
    val transition = rememberInfiniteTransition()
    val startOffsetX by transition.animateFloat(
        initialValue = -2 * size.width.toFloat(),
        targetValue = 2 * size.width.toFloat(),
        animationSpec = infiniteRepeatable(
            animation = tween(1000)
        )
    )

    background(
        brush = Brush.linearGradient(
            colors = listOf(
                Color(0xFFB8B5B5),
                Color(0xFF8F8B8B),
                Color(0xFFB8B5B5),
            ),
            start = Offset(startOffsetX, 0f),
            end = Offset(startOffsetX + size.width.toFloat(), size.height.toFloat())
        )
    )
        .onGloballyPositioned {
            size = it.size
        }
}
```

## Project Structure

```bash
shimmerEffect-kotlin/
├── app/                        # This folder contains the main application logic and components.
| ├── src/                      # This folder contains the source code for the app.
| | ├── main/                   # This folder contains the main logic of the app.
| | | ├── java/                 # This folder contains the Java source code.
| | | | └── com/                # This folder contains the package for the app.
| | | | └── shimmereffect/      # This folder contains the main activity and components for the app.
| | | ├── res/                  # This folder contains the resource files for the app such as images, layouts and strings.
| | | └── AndroidManifest.xml   # This file contains metadata about the app, including the app name, version, and permissions.
├── build.gradle                # This file contains the configuration for the Gradle build system.
├── gradle/                     # This folder contains the Gradle wrapper files.
| └── wrapper/                  # This folder contains the Gradle wrapper files.
| ├── gradle-wrapper.jar        # This file contains the Gradle wrapper executable.
| └── gradle-wrapper.properties # This file contains the Gradle wrapper configuration.
├── gradlew                     # This file contains the Gradle wrapper executable for Unix-based systems.
├── gradlew.bat                 # This file contains the Gradle wrapper executable for Windows-based systems.
├── local.properties            # This file contains the local configuration for the project, such as the path to the Android SDK.
├── settings.gradle             # This file contains the settings for the Gradle build system.
├── proguard-rules.pro          # This file contains the configuration for the ProGuard obfuscator.
├── app.iml                     # This file contains metadata about the project, including the project name, version, and dependencies.
├── .idea/                      # This folder contains the IntelliJ IDEA project files.
```

## License

**Kotlin Shimmer effect** Copyright ©2023 - Noé Campo

**This project** can be released as open source software under
the [GPL v3](https://opensource.org/licenses/gpl-3.0.html)
license, see the [LICENSE](./LICENSE) file in the project root for the full license text.

[tutorial]: assets/presentation.gif
