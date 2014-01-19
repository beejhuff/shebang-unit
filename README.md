# Shebang unit #

> Bang bang, my baby shot me down.
> <cite>(Cher)</cite>

**Shebang Unit** is an automated testing framework for Bash 4 based on [xUnit].

Now you don't have any excuse for not practicing some sexy Test-Driven Development in Bash.

Just download it here : *[releases/shebang_unit]*. Write a kata like *[examples/fizzbuzz]* and have fun!

With **Shebang Unit** you can :
 * assert equality,
 * assert that string contains or not another string,
 * assert that array contains or not an element,
 * assert that status code is success or failure,
 * assert that command is successful or failing,
 * save a baby kitten every time you use it!

## Serious examples ##

### Basic equality for newbies ###

```bash
function can_assert_equality() {
  assertion__equal 4 $((3+1))
}
```

### Awesome string assertions ###

```bash
function can_assert_that_string_contains_another_one() {
  assertion__string_contains "Cool dog is cool" "cool"
}
```

```bash
function can_assert_that_string_does_not_contain_another_one() {
  assertion__string_does_not_contain "Monorail cat" "Caturday"
}
```

```bash
function can_assert_that_string_is_empty() {
  assertion__string_empty ""
}
```

```bash
function can_assert_that_string_is_not_empty() {
  assertion__string_not_empty "Don't feed the zombies"
}
```

### Rocket science array assertions ###

```bash
function can_assert_that_array_contains_element() {
  local lost_numbers=(4 8 15 16 23 42)

  assertion__array_contains 15 "${lost_numbers[@]}"
}
```

```bash
function can_assert_that_array_does_not_contain_element() {
  local lost_numbers=(4 8 15 16 23 42)

  assertion__array_does_not_contain 1337 "${lost_numbers[@]}"
}
```

### Magic command assertions ###

```bash
function can_assert_that_status_code_is_success() {
  true

  assertion__status_code_is_success $?
}
```

```bash
function can_assert_that_status_code_is_success() {
  false

  assertion__status_code_is_failure $?
}
```

```bash
function can_assert_that_command_is_successful() {
  assertion__successful true
}
```

```bash
function can_assert_that_command_is_failing() {
  assertion__failing false
}
```

## Usage ##

1. Copy *[releases/shebang_unit]* wherever you want,
2. Create a file suffixed by *_test.sh* like *math_test.sh* in *your_folder*,
3. Write a test function like in previous examples,
4. Run `./shebang_unit your_folder`,
5. Write production code,
6. Refactor. Enough said.

### Use colors or no ###

You can use colors in test outputs with `-c` or `--colors` options. Colors are activated by default.

`./shebang_unit --colors=no your_folder`

### Use another test file pattern ###

Test file pattern can be changed with `-p` or `--pattern` options. It can be convenient to run only few tests or totally change the default pattern (`*_test.sh`).

`./shebang_unit --pattern=this_only_test.sh your_folder`

`./shebang_unit --pattern=test_*.sh your_folder`


## Pimp your **shebang_unit** ##

If you don't like **shebang_unit** coding conventions like function names or test file names, you can hack the global variables at the top of *shebang_unit.sh*.

For instance if your private functions are prefixed by `p_` for some reason :

```bash
SBU_PRIVATE_FUNCTION_NAME_REGEX="^p_.*"
```

Or, if you would rather live in dark and definitively turn off colors :

```bash
SBU_USE_COLORS="${SBU_NO}"
```


## License ##

Copyright (C) 2013, Arpinum

**Shebang Unit** is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

**Shebang Unit** is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with **Shebang Unit**.  If not, see [http://www.gnu.org/licenses/lgpl.html].


[xUnit]: http://wikipedia.org/wiki/XUnit
[releases/shebang_unit]: https://github.com/arpinum/shebang_unit/blob/master/releases/shebang_unit
[examples/fizzbuzz]: https://github.com/arpinum/shebang_unit/tree/master/examples/fizzbuzz
[http://www.gnu.org/licenses/lgpl.html]: http://www.gnu.org/licenses/lgpl.html