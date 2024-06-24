# why make a programming style

i like consistency

i like when code structured good

i hate when code is structured bad

# tabs vs spaces

we use tabs in this household

1. its one character so i can just do `x` instead of `dw`
2. i dont give a damn if it looks the same for everybody just configure your tab width and call it a day

# indents

i dont like to put more than three indents in any of my files

thats why i make my tab width 8 characters in my editor

if theres over 3 indents separate it or guard clause it whatever you people do

# casing

PascalCase for types

snake_case for everything else

i also like snake_case for my files

why snake_case? it looks really different from the commonly used PascalCase so we can separate our stuff from our types and default instances/libraries

i also just think it looks nice

# naming

no single letter names, unless there like complicated equations or something then just specify its math and which math thing youre using

if you want to make a constant then do what google does and put a `k_` before the variable name

past tense for booleans (no need for is{present tense})

present tense for everything else

full words

# comments

at the top of the file 

```luau
--[[
    filename.luau

    credits
    justification for why this module/abstraction exists

    other details
]]
```

try not to describe what the module does, the name/types should make that self explanatory

why add the top comment?

1. it looks cool
2. sometimes i have no idea why a certain abstraction is there, you gotta prove it isnt unnecessary
3. i also just like some juicy details

names of variables/functions should be self explanatory, only use documentation/moonwave style comment to justify why the module/abstraction exists

# programming paradigm

we use imperative programming in this household

object oriented programming and functional programming hurt my brain

youre not banned from using the other two styles, but make sure theyre confined to their individual module and you have a justification for why youre using it

# script structure

we're not doing that thing where its a single script calling a bunch of other scripts and their methods

this is just going to be a normal programming structure where its a small bundle of server scripts and client scripts that may have a few modules inside

NOT what we're gonna do
```
server
+
|- runtime.server.luau
|- services
|-- round_manager.luau
|-- ghost_mode.luau
|-- datastores.luau
```

what we're gonna do
```
server
+
|- round_manager
|-- init.server.luau
|-- ghost_mode.luau
|- datastores.luau
```

# modules

this is how i style my modules!

```luau
--[[
    chef.luau

    sudo make me a sandwich
]]

type ChefModule = {
    k_energy: number,
    make_sandwich: (tip: number) -> boolean
}

local k_energy = 10

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

return {
    k_energy = 10,
    make_sandwich = make_sandwich
} :: ChefModule
```

# metatables

i dont believe in metatables

they just... disturb me... they come off as hacky

im sure theyre loveable in some way... but i would just prefer not to use them... i hope you understand :(

# classes

we take [mr. sleitnicks approach for this one](https://www.youtube.com/watch?v=-E_L6-Yo8yQ)

```luau
export type Person = {
    first_name: string,
    last_name: string,
    age: number,
    pets: number
}

type PersonModule = {
    give_pet: (person: Person, amount: number) -> ()
}

--- cuz we gotta see how happy theyd be
local function give_pet(person: Person, amount: number)
    person.pets += amount
end

return {
    give_pet = give_pet
} :: PersonModule
```

# process

only abstract when you need to, no premature abtractions please :(

i dont like dependencies... i have no intellectual reason why they just give me the jeepers

# thank you

thank you for reading :^)
