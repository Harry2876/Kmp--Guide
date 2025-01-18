

The Tale of Codey the Adventurer

Once upon a time in the land of Kotlinia, there was a brave adventurer named Codey. Codey loved solving problems but was tired of writing the same code over and over again for Android, iOS, and desktop. Every time Codey faced a new platform, it felt like learning a whole new language to speak with it.

One day, Codey met a wise sage named Kotlin Multiplatform. The sage said, “Codey, you don’t need to repeat yourself! Use your skills wisely and share your knowledge across all lands—be it Androidia, iOSia, or even Desktoporia.”

Codey’s eyes lit up. “But how?” he asked.

The sage explained the path of advanced project structures and said, “You must organize your code in a way that lets you share only what needs to be shared and specialize when necessary.”

The Journey: Building a Multiplatform Kingdom

To build a strong kingdom, Codey had to organize it into modules, much like dividing a castle into sections: some for common use, others unique to specific regions.

1. Common Code Module: The Heart of the Kingdom

“This is your commonMain module,” said Kotlin Multiplatform. “It’s where you put everything that can be shared across platforms—like your core logic, algorithms, and business rules. For example, if you’re building a weather app, this is where you calculate temperatures or fetch weather data from an API.”

Imagine this as the library of the kingdom—books and resources everyone in Kotlinia can access.

2. Platform-Specific Modules: Regional Traditions

“Not everything can be shared,” the sage continued. “Each land has its quirks. Androidia loves XML layouts, while iOSia is a fan of SwiftUI.”

So, Codey created platform-specific modules:
	•	androidMain: For Android-specific things like working with Activities or XML resources.
	•	iosMain: For iOS-specific details like handling UIKit.

This was like setting up local traditions in each part of the kingdom.

3. Intermediate Modules: A Middle Ground

Sometimes, Codey realized that two lands shared similar needs but not exactly everything. For instance:
	•	Both Androidia and iOSia liked HTTP requests, but Android used OkHttp while iOS used NSURLSession.

To handle this, the sage introduced intermediate modules, like jvmMain or nativeMain. These modules acted like regional councils—bridging the gap between the global common module and specific platforms.

Special Tools for the Job

Codey needed tools to help build and manage this kingdom:
	1.	Source Sets: Imagine these as blueprints to decide what belongs to whom. The commonMain, androidMain, and iosMain source sets help Kotlin decide where the code will run.
	2.	Dependencies: Each module needed resources to thrive. Codey added dependencies to each source set. For instance:
	•	commonMain could use a shared library like kotlinx.serialization.
	•	androidMain could rely on Android libraries like Room.
	3.	Gradle Configuration: The sage handed Codey a scroll with magical Gradle scripts to connect everything together. Using the kotlin-multiplatform plugin, Codey could define which targets (Android, iOS, desktop, etc.) to include.

The Kingdom’s Prosperity

With everything in place:
	•	Codey wrote most of the code in commonMain, which was shared everywhere.
	•	Specialized quirks for Androidia and iOSia went into their respective modules.
	•	The project was easy to maintain and could grow to support new lands like Desktoporia or Webovia.

The kingdom of Kotlinia flourished, and Codey became known as the wise architect who brought harmony to the lands.

Moral of the Story

When building a Kotlin Multiplatform project, think of it like managing a kingdom:
	•	commonMain is the shared heart.
	•	Platform-specific modules cater to each land’s unique needs.
	•	Intermediate modules smooth over regional differences.
	•	Use tools like source sets and dependencies to keep things organized.



**The Advanced Chronicles of Codey: Mastering the Multiplatform Realms**

After Codey mastered the basics of the **Kotlin Multiplatform Kingdom**, the wise sage **Kotlin Multiplatform** returned with more secrets. "Codey," the sage began, *"to truly harmonize your kingdom, you must master the advanced arts: managing dependencies, crafting hierarchies, and ensuring your code is in sync."*

**1\. The Web of Dependencies: The Art of dependsOn**

The sage started by introducing dependsOn, a magical link that connected parts of the kingdom.

*"Some modules share common knowledge,"* the sage explained.

"For example, **androidMain** and **iosMain** might both need access to the secrets of the **nativeMain**. Instead of duplicating code, make **nativeMain** a trusted advisor by using dependsOn."*

-  **Common Use Case:**

Say **nativeMain** holds platform-specific utilities, like managing memory. Both **androidMain** and **iosMain** can now dependsOn it. This avoids duplication and ensures consistency.

**Visualizing the Web:**

commonMain

 ↳ nativeMain

 ↳ androidMain

 ↳ iosMain

It's like creating **sub-royalties**---Androidia and iOSia respect the native traditions of **nativeMain**, which itself is built on the laws of **commonMain**.

**2\. Source Set Hierarchies: Building the Kingdom's Blueprint**

Next, the sage taught Codey about **source set hierarchies**, the organizational blueprint for the entire kingdom.

*"Think of your source sets as a family tree,"* the sage said.

*"Each child source set inherits from its parent and can add its own special flavor."*

For example:

-  **commonMain** is the ancestor---it defines the core rules.

-  **jvmMain** inherits from **commonMain**, customizing things for JVM-based platforms.

-  **androidMain** inherits from **jvmMain**, adding Android-specific tweaks.

**Hierarchy in Action:**

commonMain

 ↳ jvmMain

 ↳ androidMain

 ↳ nativeMain

 ↳ iosMain

This structure allows Codey to reuse shared knowledge while respecting each region's quirks.

**3\. Declaring Custom Source Sets: Tailoring Regional Councils**

As the kingdom grew, new lands emerged---like **WearOSia** or **TvLandia**. These lands needed their own councils, so Codey declared **custom source sets**.

*"To declare a new council,"* said the sage, *"simply define a new source set and connect it to the hierarchy."*

**Example: Creating a WearOS source set**

kotlin {

 sourceSets {

 val wearOsMain by creating {

 dependsOn(commonMain)

 }

 androidMain.dependsOn(wearOsMain)

 }

}

This allowed **wearOsMain** to have its own unique flavor while still relying on the wisdom of **commonMain**.

**4\. Dependencies on Libraries or Projects: Importing Magical Tools**

Codey needed powerful tools to rule efficiently, so the sage showed how to add **dependencies**.

*"Whether it's a shared library or a specific resource, dependencies empower your modules,"* the sage explained.

-  **Adding a Dependency to** commonMain**:**

For shared tools like kotlinx.serialization:

commonMain {

 dependencies {

 implementation("org.jetbrains.kotlinx:kotlinx-serialization-core:1.5.0")

 }

}

-  **Platform-Specific Dependencies:**

For Android-only tools like Room:

androidMain {

 dependencies {

 implementation("androidx.room:room-runtime:2.5.0")

 }

}

**Pro Tip:** Always check if a library supports Kotlin Multiplatform to avoid surprises!

**5\. Aligning Versions of Common Dependencies: Avoiding Conflicts**

One day, chaos broke out in the kingdom---**androidMain** and **iosMain** were fighting over different versions of the same library.

*"This can't continue!"* cried Codey.

The sage explained: *"You must align the versions of common dependencies to maintain peace."*

Codey used **version alignment**:

kotlin {

 sourceSets {

 all {

 dependencies {

 implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.7.0")

 }

 }

 }

}

This ensured everyone---**commonMain**, **androidMain**, and **iosMain**---used the same version of kotlinx-coroutines-core.

**6\. Compilations: The Engines of the Kingdom**

Finally, the sage revealed the secret of **compilations**, the engines that turned Codey's work into something the world could use.

*"Each target---Android, iOS, desktop---needs a separate engine,"* the sage said. *"Your job is to configure these engines to work seamlessly."*

Codey learned that each source set is compiled separately for its target:

-  **JVM Compilation:** Produces bytecode for Android and JVM.

-  **Native Compilation:** Produces binaries for iOS, macOS, and Linux.

-  **JS Compilation:** Produces JavaScript for web platforms.

With Gradle's help, Codey configured the compilations:

kotlin {

jvm() *// Configure JVM compilation*

ios() *// Configure iOS compilation*

 js() *// Configure JS compilation*

}

By fine-tuning these engines, Codey ensured the kingdom's creations worked perfectly across all platforms.

**The Kingdom Flourishes**

With these advanced concepts mastered, Codey's kingdom of Kotlinia thrived. Every module was organized, dependencies were aligned, and the engines of compilation churned out efficient builds for all lands.

The sage smiled. *"Codey, you are now a true master of the Multiplatform Kingdom. Go forth and build great things."*

**Moral of the Story**

-  dependsOn**:** Link related modules to share common code.

-  **Source Set Hierarchies:** Structure your project like a family tree.

-  **Custom Source Sets:** Create new modules for unique needs.

-  **Dependencies:** Equip your modules with the tools they need.

-  **Version Alignment:** Keep dependencies consistent across modules.

-  **Compilations:** Configure builds for every platform.


