---
layout: default
---

BerryCrush
==========

## What is BerryCrush?

BerryCrush is a **behavior-driven development (BDD) testing framework** that generates API test code directly from your OpenAPI specification. Write tests in a human-readable `.scenario` format and let BerryCrush handle the rest.

```berrycrush
scenario: Create and retrieve a pet
  given:
    call ^createPet
      body:
        name: "Berry"
        status: "available"
  when:
    call ^getPet
      path:
        petId: ${response.body.id}
  then:
    status: 200
    body:
      name: "Berry"
```

## Key Features

<div class="features">
  <div class="feature">
    <h3>📋 OpenAPI Integration</h3>
    <p>Automatically discovers endpoints, parameters, and schemas from your OpenAPI spec</p>
  </div>
  
  <div class="feature">
    <h3>📖 Readable Syntax</h3>
    <p>Write tests in natural language that both developers and stakeholders can understand</p>
  </div>
  
  <div class="feature">
    <h3>🔄 Reusable Fragments</h3>
    <p>Create reusable test components to eliminate duplication and improve maintainability</p>
  </div>
  
  <div class="feature">
    <h3>🛠️ IDE Support</h3>
    <p>Full IDE integration with syntax highlighting, completion, and navigation</p>
  </div>
</div>

## Documentation

<div class="doc-cards">
  <a href="https://doc.berrycrush.org" class="doc-card">
    <h3>📚 Library Documentation</h3>
    <p>Core library reference, scenario syntax, and integration guides</p>
  </a>
  
  <a href="https://vscode.berrycrush.org" class="doc-card">
    <h3>💻 VS Code Extension</h3>
    <p>Install and configure the VS Code extension for BerryCrush</p>
  </a>
  
  <a href="https://intellij.berrycrush.org" class="doc-card">
    <h3>🧠 IntelliJ Plugin</h3>
    <p>IDE support for IntelliJ IDEA, WebStorm, and other JetBrains IDEs</p>
  </a>
</div>

## Quick Start

### 1. Add the dependency

**Gradle (Kotlin DSL)**
```kotlin
testImplementation("org.berrycrush:berrycrush-junit:1.0.0")
```

**Maven**
```xml
<dependency>
    <groupId>org.berrycrush</groupId>
    <artifactId>berrycrush-junit</artifactId>
    <version>1.0.0</version>
    <scope>test</scope>
</dependency>
```

### 2. Create a test suite

```java
@Suite
@IncludeEngines("berrycrush")
@BerryCrushScenarios(locations = "scenarios/*.scenario")
@BerryCrushSpec("petstore.yaml")
@BerryCrushConfiguration(bindings = PetstoreBindings.class)
public class PetstoreScenarioTest {
}
```

```java
public class PetstoreBindings implements BerryCrushBindings {
    @Override
    public Map<String, Object> getBindings() {
        return Map.of(
            BerryCrushBindings.DEFAULT_BINDING_NAME, new OpenApiSpecValue("petstore.yaml", "http://localhost:8080")
        );
    }
}
```

### 3. Write your first scenario

```berrycrush
# src/test/resources/scenarios/pets.scenario
scenario: List all pets
  when:
    call ^listPets
  then:
    status: 200
```

### 4. Run your tests

```bash
./gradlew test
```

## Get Started

- [📖 Read the Documentation](https://doc.berrycrush.org)
- [⬇️ Download VS Code Extension](https://vscode.berrycrush.org)
- [⬇️ Download IntelliJ Plugin](https://intellij.berrycrush.org)
- [🐙 View on GitHub](https://github.com/BerryCrush/berrycrush)

---

<footer>
  <p>BerryCrush is open source software licensed under the <a href="https://github.com/BerryCrush/berrycrush/blob/main/LICENSE">Apache 2.0 License</a></p>
</footer>
