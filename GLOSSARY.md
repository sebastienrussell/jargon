# Jargon

Librairie Kotlin Multiplatform de localisation dont les textes sont déclarés dans un fichier JSON unique, où toutes les langues d'un même texte sont côte à côte.

## Language

**Translation file**:
Le fichier JSON qui déclare toutes les Keys et leurs Translations ; seule source de vérité des textes en v1.
_Avoid_: strings file, resource file, catalogue

**Key**:
Identifiant d'un texte localisable, déclaré dans le Translation file, écrit en lowerCamelCase et éventuellement préfixé de Groups (`welcomeText`, `onboarding.welcomeTitle`).
_Avoid_: id, string name, label

**Group**:
Segment d'une Key qui précède un `.` et rassemble plusieurs Keys sous un même nom (`onboarding` dans `onboarding.welcomeTitle`). Un nom ne peut pas être à la fois une Key et un Group.
_Avoid_: namespace, section, category

**Accessor**:
Le point d'accès typé généré pour une Key : une propriété si la Key n'a aucun Placeholder, une fonction dont les paramètres sont ses Placeholders sinon (`Jargon.welcomeText`, `Jargon.greeting(name = …)`).
_Avoid_: getter, string resource, R.string

**Translation**:
Le texte d'une Key pour une Locale donnée.
_Avoid_: value, string, wording

**Locale**:
Tag BCP 47 identifiant une langue, avec une région optionnelle (`fr`, `fr-CA`).
_Avoid_: language, lang, culture

**Supported locale**:
Une Locale pour laquelle le Translation file contient au moins une Translation.
_Avoid_: available language, enabled locale

**Default locale**:
La Supported locale utilisée en dernier recours ; chaque Key a obligatoirement une Translation pour elle.
_Avoid_: base language, fallback language

**Effective locale**:
La Locale à partir de laquelle toutes les Keys sont résolues : la Locale forcée si elle existe, sinon la première Locale préférée de l'utilisateur qui correspond à une Supported locale, sinon la Default locale.
_Avoid_: current language, active locale, app locale

**Fallback chain**:
L'ordre dans lequel les Locales sont essayées, à partir de l'Effective locale, pour trouver la Translation d'une Key : région, puis langue seule, puis Default locale (`fr-CA` → `fr` → Default locale).
_Avoid_: resolution order, cascade

**Placeholder**:
Segment nommé d'une Translation, écrit `{name}`, remplacé par une valeur fournie à l'exécution.
_Avoid_: argument, variable, token

**Showcase**:
L'application Android qui démontre l'usage de la librairie.
_Avoid_: sample, demo app, example
