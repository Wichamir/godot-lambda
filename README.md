# GDLambda

![icon](icon.png)

GDLambda is a small, experimental, pure GDScript library adding lambdas and basic functional programming features to Godot 3. Most of these are already available in Godot 4.

## Installation

Copy `addons/lambda` directory into the `addons` directory of your project.

## Usage

```gdscript
var lambda := gdl.lambda("func(x): return x*x*x")
print(lambda.execute(4)) # 64
```

```gdscript
var units := get_children()
units.sort_custom( # sort units by their initiative
    gdl.lambda("func(a, b): return a.initiative > b.initiative").as_funcref(),
    "call_func"
)
```

See [examples.gd](examples.gd).

## Security

Parsing strings as code can be dangerous and potentially allow for remote code execution exploits. To reduce the risk only parse variables via the `Dictionary` method explained in [examples.gd](examples.gd) under the `capturing_environment` function.

The plugin is mostly an experiment to test out the capabilities of the built-in `Expression` class. It was not tested on serious projects.