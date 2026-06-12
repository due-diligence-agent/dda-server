# Notes

This is a due-diligence-agent for Swiss companies. The idea is to have a LangGraph workflow which validates defined flags. To do that, it scrapes the website, background-checks key employees, crawls extrenal registries, and aggregates all retrieved information to then deterministically set the flags. These flags have different weight and can range from informative to critical. Therefore, in a later step, a machine learning model can be trained on these flags to evaluate their importants and output a risk score between 0 and 1. To remain compliant to data privacy regulations, absolutely no personal data is permanently stored. A few first flags to validate could be (just as first draft / idea):

ON WEBSITE:
- Website address does not match registered seat/contact address.
- UID stated on website belongs to unrelated entity.
- Frequent Schweizerisches Handelsamtsblatt mutations.
- Relevant information about the company status found in publications / registries.
- Website claims “Swiss company” but no Swiss entity is found.
- Domain/contact address suggests different jurisdiction.
- No imprint/contact/legal information found.
- AI generated images present (check via SynthID or ChatGPT AI Detector)
- Evtl. AI generated text present
- Unrealistic partners mentioned on site

ON EMPLOYEES:
- Search for suspicious information in publications / registries about managing employees 

IF ZEFIX AVAILABLE:
- Very recent incorporation.
- No Swiss registry entity found.
- Multiple possible Swiss entities found.
- Legal name stated on website does not match registry name.
- Entity is in liquidation.
- Entity is deleted/inactive.

LATER:
- Interpret public financial statements 

# rdd-server

This project uses [Gradle](https://gradle.org/).
To build and run the application, use the *Gradle* tool window by clicking the Gradle icon in the right-hand toolbar,
or run it directly from the terminal:

* Run `./gradlew run` to build and run the application.
* Run `./gradlew build` to only build the application.
* Run `./gradlew check` to run all checks, including tests.
* Run `./gradlew clean` to clean all build outputs.

Note the usage of the Gradle Wrapper (`./gradlew`).
This is the suggested way to use Gradle in production projects.

[Learn more about the Gradle Wrapper](https://docs.gradle.org/current/userguide/gradle_wrapper.html).

[Learn more about Gradle tasks](https://docs.gradle.org/current/userguide/command_line_interface.html#common_tasks).

This project follows the suggested multi-module setup and consists of the `app` and `utils` subprojects.
The shared build logic was extracted to a convention plugin located in `buildSrc`.

This project uses a version catalog (see `gradle/libs.versions.toml`) to declare and version dependencies
and both a build cache and a configuration cache (see `gradle.properties`).
