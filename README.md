# why a style guide?

i like:
1. consistency
2. file structure

# tabs vs spaces

tabs because: 
1. single character
2. configurable

# indents

1. i make my tab width 8 characters
2. i HATE going over 3 tabs
3. i like my code structured as a cooking recipe

# casing

1. PascalCase for types
2. snake_case for everything else, including filenames
3. chose those two because they look very different
4. chose snake case as primary because it just looks nice to me :)... and because its easy to tell if words are supposed to be spaced

# naming

1. no single letter names unless its math
2. constants must have `k_` prefix (like google)
3. past tense for booleans
4. full words (if conflicting with library then have a commonly used shortening)

# comments

at the top of files:

```luau
--[[
    filename.luau

    credits

    justification for why this module/abstraction exists

    other details

    { note: dont describe what module does, name and types should make it self explanatory }
]]
```

why?
1. top comments just look nice i picked it up from the emacs users
2. justify your abstractions before using them, if you cant justify them then they should not be added
3. you need to iron out some technical details sometimes

function documentation should only be used to justify why something exists, never to explain what it does

# file structure

no singleton type architecture

NOT what we're doing:
```
server
+
|- runtime.server.luau
|- services
|-- round_manager.luau
|-- ghost_mode.luau
|-- datastores.luau
```

what we're doing: 
```
server
+
|- round_manager
|-- init.server.luau
|-- ghost_mode.luau
|- datastores.luau
```

i dont have a particularly intelligent reason for why i dont use the singleton architecture,,,, i just dont like it and never found a use case for it

# modules

start with C-style function headers (maybe with some shared variables and constants too)

why?
1. im impatient and want to get the details of an abstraction ASAP
2. its like psuedo documentation

```luau
--[[
    chef.luau

    anyone can cook
]]

type ChefModule = {
    k_energy: number,
    make_sandwich: (tip: number) -> boolean
}
```
define constants and initial variables

```luau
local k_energy = 10
```

FULLY TYPED functions

why?
1. when you jump to it on your lsp you get all the details without looking at the header type
2. appeases the LSP

```luau
local function make_sandwich(tip: number): boolean
    if k_energy + tip < 5 then
        print("no i dont wanna")
        return false
    end

    print("ok")
    print("---")
    print("ooo")
    print("---")

    return true
end
```

gather your children

why?
1. when you give it the type directly the LSP is more strict with its properties complying with the given types
2. you can introduce some changes and mutability afterward if need be

```luau
local chef_module: ChefModule = {
    k_energy = 10,
    make_sandwich = make_sandwich
}

return chef_module
```

if it seems weird... thats because it is...

its how i like making my modules though, so im going to keep doing it

# metatables

1. i dont like to use them at all
2. no smart reason for this either, they just irk me :(

# classes

we use [imperative approach](https://www.youtube.com/watch?v=-E_L6-Yo8yQ), not much else to it :)

# conclusion

1. my programs should look like cookie recipes and you should be able to follow them in a linear fashion
2. from the prerequisite information given by the names, header comments, and header types, you should be able to understand the purpose of an abstraction immediately
3. changes to programming structure and function should be justified with doc comments

thank you for reading :^)
