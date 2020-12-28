# Why I like Rust (and how to get into it)

Rust is a language that is booming in popularity. Here's 10 reasons I love the language. (And 5 reasons why I don't)

It's been ranked as one of the most loved languages on stack overflow for many years running!

Here is an insight into why that might be:

# 1. It's fast
The first point is that it is an incredibly fast language, it consistently benches just behind C and C++ (the unrivaled champions of speed in higher level languages).

This is partly due to the large number of optimisations it has. The speed is a feature in the language that actually unlocks many other uses for it.

# 2. It's tooling is outstanding

### Cargo
Rust has an ecosystem of "crates". The package manager that handles crat
es is called "cargo". It helps you create new projects, manage dependencies, compile your code, upload your libraries to the crates ecosystem and install rust applications. It can even be extended with plugins (we'll discuss this later).

### Rustc

The Rust compiler, rustc, is very very helpful when it comes to errors. It will point you to exactly where the error came from and can even help you to fix the bug by suggesting things to put there.

You can see that this error message is very descriptive, telling you exactly where the error is, what the error is and how to fix it:

![](https://i.postimg.cc/gJHDvPg3/unknown.png)

It provides help when you mistype something:

![](https://i.postimg.cc/C1bF7c8G/image.png)

It even provides help with the language if you are unfamiliar with it:

```rust
fn main() {
    let name: &str;
    println!("Hello {}!", name)
}
```

![](https://i.postimg.cc/BvQnBrc2/image.png)

Notice that part at the bottom? `For more information about this error, try rustc --explain E0381?`

Let's try running that command!

![](https://i.postimg.cc/SsHQqJ0G/image.png)

You see that it gives a lot of information about the language and more detail on why the code errors.
It makes debugging errors really nice and simple.

### Rustfmt

Rustfmt is a tool that very quickly formats your codebase into a readable, clean and professional looking code. It also makes a great teacher on how best to write the syntax of the language. It does things like ensure that no lines are too long and that everything isn't bunched up into some unreadable code.

### Clippy

Clippy is one of the most amazing things I've ever seen in a language ecosystem, it's a linter. It provides you with suggestions to rewrite your code in a way that makes it more efficient and more "rust-like". 

It has many suggestions and you are bound to be able to rewrite your code in a better way. Clippy can even fix a lot of problems with your code automatically if you tell it to. 

A good example of this is using a counter variable in a for loop, clippy will detect that you've used a verbose and unclear implementation that isn't recommended.

Clippy will teach you how to write good rust code in the future, it teaches you things beyond the tutorial and really helps your code.

Here is some code that can be improved:

```rust
fn main() {
    let mut counter = 0;
    let languages = vec!["Rust", "Ruby", "Javascript", "Python", "Lua"];
    for language in languages {
        println!("{}, {}", language, counter);
        counter += 1;
    }
}
```

It prints out

```
Rust, 0
Ruby, 1
Javascript, 2
Python, 3
Lua, 4
```

When running clippy:

![](https://i.postimg.cc/CM3wXT7j/image.png)

It suggests this line should become `languages.into_iter().enumerate()`

It also provides a link to a website which will tell you about why this is a bad idea and how to fix it.

This way is a much better (and more "rust-like") way of looping over a vector with a counter to support it.

Here's the final code with the changes:

```rust
fn main() {
    let languages = vec!["Rust", "Ruby", "Javascript", "Python", "Lua"];
    for (counter, language) in languages.into_iter().enumerate() {
        println!("{}, {}", language, counter);
    }
}
```

# 3. It creates defensive applications
Everything in Rust is checked at compile time. It'll check for syntax errors, type mismatches, problems with threads, memory errors, unrecognized identifiers, unused variables and a whole lot more.

When the compiler, rustfmt and clippy say that your code is all OK, you've constructed robust code that will most likely never break. It gets your code to be as perfect as possible before it is released into the wild.

It's also baked into the language design itself, it has an innovative way of handling errors, null types, memory and threads. All of these designs make sense when you get your head around them and allow your code to handle most problems before they happen. I'll go over these later.

# 4. You can truly build just about anything
People are already building Operating Systems in Rust *(https://www.redox-os.org/)* and there are tutorials appearing *(https://os.phil-opp.com/)*. Traditioinally, you'd use C to do this sort of thing.

At the other end of the spectrum, people are building lightning fast full stack web applications with Rust working on the back end and the front end. There are many tutorials on this and frameworks similar to React have appeared. *(https://yew.rs)*. Traditionally, you'd write javascript for these things.

You can build just about anything with Rust and more importantly it is practical to do so due to its syntax borrowed from many high level languages. It's not as difficult and dangerous as C and not as abstracted and high level as JS, it takes the best of both worlds and combines them.

# 5. The documentation is pretty complete

Rust has a tool for writing rust documentation called rustdoc. It allows you to write documentation from within your code and generate a book for users on how to use the language. It's quite amazing!

Rust's standard library has a lot of complete documentation too, you'll be able to find a method for just about anything you'd need. There are also many websites to learn from, such as https://rust-lang.github.io/rust-clippy/master/index.html for explainations on best practices for the language and solving errors, https://lib.rs/ to help find libraries to use in your program and https://docs.rs/ for documentation of the standard library and other libraries.

There is also a book called "the book" which goes over Rust from the beginning and describes what things do. 

Here are a list of websites to help you learn Rust:

- "The Book" - https://doc.rust-lang.org/stable/book/
- Rust by Example - https://doc.rust-lang.org/stable/rust-by-example/
- Rust Cookbook - https://rust-lang-nursery.github.io/rust-cookbook/
- Tour of Rust - https://tourofrust.com/
- Easy Rust - https://fongyoong.github.io/easy_rust/
- Rustlings - https://github.com/rust-lang/rustlings/blob/main/README.md
- TensorProgramming Rust Videos - https://www.youtube.com/watch?v=EYqceb2AnkU&list=PLJbE2Yu2zumDF6BX6_RdPisRVHgzV02NW

There are also plenty of tutorials for building things by example (I sorted them roughly with the easiest closer to the top):

- Build your own ASCII Rouge-Like Game in Rust: https://tomassedovic.github.io/roguelike-tutorial/
- Build your own Command Line Todo List Application in Rust: https://github.com/hariamoor/todo-cli/tree/master/content
- Build your own 2D Game in Rust: https://a5huynh.github.io/posts/2018/adventures-in-rust/
- Build your own Text Editor in Rust: https://www.philippflenker.com/hecto/
- Build your own Discord Bot in Rust: https://medium.com/better-programming/writing-a-discord-bot-in-rust-2d0e50869f64
- Build your own Color Picker in Rust: https://pauljmiller.com/posts/druid-widget-tutorial.html
- Build your own Todo List Application in Rust: https://bodil.lol/vgtk/
- Build your own Baseball Data Web Scraper in Rust: https://github.com/elibenporat/learn-to-code-rust-baseball/tree/master/articles
- Build your own Web Application in Rust: https://www.sheshbabu.com/posts/rust-wasm-yew-single-page-application/
- Build your own Shell in Rust: https://www.joshmcguigan.com/blog/build-your-own-shell-rust/
- Build your own DNS Server in Rust: https://github.com/EmilHernvall/dnsguide/blob/master/README.md
- Build your own Web Browser Engine in Rust: https://limpet.net/mbrubeck/2014/08/08/toy-layout-engine-1.html
- Build your own Chat Service in Rust: https://nbaksalyar.github.io/2015/07/10/writing-chat-in-rust.html
- Build your own Media Player in Rust: https://www.youtube.com/watch?v=enxqU3bhCEs
- Build your own 3D Renders in Rust: https://www.falseidolfactory.com/projects/learning-gfx-hal/
- Build your own Compiled Programming Langauge in Rust: https://createlang.rs/
- Build your own Interpreted Programming Language in Rust: https://arzg.github.io/lang/
- Build your own Operating System in Rust: https://os.phil-opp.com/

There are so many ways you can learn Rust, if one tutorial or method doesn't work for you, there are always others.

Rust does have a steep learning curve but I recommend learning some of the basics and then building a few things to get you used to the language. You'll get it eventually!

# 6. Companies are starting to hire more and more Rust devs
Google, Facebook, AirBnB, Apple Amazon and Mozilla. These are all companies who are hiring Rust developers. It has really started to take off in the past year and it shows no signs of slowing down.

Check out:
https://rust.careers/

As of writing this it has jobs everywhere from the USA to Hungary.

Take a look here too:

https://stackoverflow.com/jobs?q=rust


# 7. Its highly modular and extensible

## Macros
Macros are a language feature that allows you to extend the language syntax. Here are some of the coolest uses of macros:

#### For executing shell commands as they are
A library (https://github.com/rust-shell-script/rust_cmd_lib) allows you to write shell commands right into Rust itself:

```rust
// Running a shell command
run_cmd!(du -ah . | sort -hr | head -n 10)?;

// Another example
let n = run_fun!(echo "the quick brown fox jumped over the lazy dog" | wc -w).unwrap();
eprintln!("There are {} words in above sentence", n);
```

Using strings for this is now old news! Macros are much more appropriate.

#### For allowing HTML to be written directly into the language
A library called yew (https://yew.rs/docs/en/concepts/html) has a html macro that allows you to write HTML right into Rust:

```rust  
html! {
    <Container>
        <h4>{ "Hi" }</h4>
        <div>{ "Hello" }</div>
    </Container>
}  
```

This might remind you of JSX if you are into React.js 

#### For formatting strings
You use macros for formatting strings in Rust.

```rust
let name = "curlpipe";
format!("Hello, {}, have a nice day!", name); // Will return "Hello, curlpipe, have a nice day!"
format!("{name} is {age} years old", name="kevin", age=25); // Will return "Kevin is 25 years old"
format!("{:.3}", 3.1415926); // Will return "3.142" as it has been rounded to 3 decimal places by the format macro
```

The formatting macro gets so much more advanced, check the things you can do with it here:
https://doc.rust-lang.org/std/fmt/index.html

## Attributes
Attributes are another cool language feature that add information to files, functions and variables. They allow you to tell the compiler what you wish to do with the parts of the language.

#### For ignoring parts of code in test coverage
A testing library (https://github.com/xd009642/tarpaulin) uses attributes to allow users to tell it to ignore parts of the code that it doesn't want to have coverage on.

```rust
#[cfg(not(tarpaulin_include))]
fn main() {
    println!("I won't be included in results");
}
```

#### For defining endpoints in the back end of a web app
Rocket (https://github.com/SergioBenitez/Rocket) is a web framework library that creatively uses attributes to define endpoints.

```rust
#[get("/<name>/<age>")]
fn hello(name: String, age: u8) -> String {
    format!("Hello, {} year old named {}!", age, name)
}

#[launch]
fn rocket() -> rocket::Rocket {
    rocket::ignite().mount("/hello", routes![hello])
}
```

Visiting `localhost:8000/hello/John/58`, for example, will trigger the hello route resulting in the string `Hello, 58 year old named John!` being sent to the browser. If an `<age>` string was passed in that can't be parsed as a `u8`, the route won't get called, resulting in a 404 error.

This is very readable and very clever.

#### For telling Rust what to ignore
Rust can ignore warnings, for example, let's say that you didn't care that clippy didn't like you having unused variables in your code.

You can add this to the top of your file to tell the Rust compiler to shut up:

```rust
#[allow(dead_code)]
```

## Pattern Matching

#### As a "case" statement

```rust
    let x = 1;

    match x {
        1 => println!("one"),
        2 => println!("two"),
        3 => println!("three"),
        _ => println!("anything"),
    }
```

This would print "one" because x is 1

```rust
    let x = 1;

    match x {
        1 | 2 => println!("one or two"),
        3 => println!("three"),
        _ => println!("anything"),
    }
```

This would print "one or two" because 1 is 1 or 2

#### Matching tuples with ease

```rust
fn foo(x: (&str, isize, bool)) {
    match x {
        (_, 42, _) => println!("it's 42"),
        (_, _, false) => println!("it's not true"),
        _ => println!("it's something else"),
    }
}
```

You can match pretty much any data structure in rust and handle it, above is a tuple of a string, integer and boolean being matched, the `_` will make the match statement disregard the other fields.

#### Matching ranges of data

Matching ranges of integers and characters is easy:

```rust
    let x = 'c';

    match x {
        'a'..='j' => println!("early ASCII letter"),
        'k'..='z' => println!("late ASCII letter"),
        _ => println!("something else"),
    }
```

This would print "early ASCII letter" because 'c' is in the range of a to j

## Cargo plug-ins
Cargo can be configured to have even more functionality

#### For distributing to debian based linux distros
https://crates.io/crates/cargo-deb

Cargo-deb is a tool that allows you to create `deb` files in one command. Just like this:

`cargo deb`

That's it, you now have .deb files ready to go in the `target` directory of your project.

#### Test libraries
https://crates.io/crates/cargo-tarpaulin

Cargo-tarpaulin is a test library that allows for test coverage and can generate HTML of where your tests missed. 

#### Automagically generating Readme files
https://crates.io/crates/cargo-readme

By just running

`cargo readme > README.md`

it generates a Readme based off the documentation in your code.

#### Auditing security vulnerabilities
https://crates.io/crates/cargo-audit

This library will allow you to run the command `cargo audit` and it'll detect any security vulnerabilities in the dependencies of your code.

---

This is only scratching the surface on what Rust is capable of and there are so many more "wow factors" that are practical and mind-blowing.

# 8. It has unique takes on old problems

## None, Nil, Null, NaN, Undefined
Rust doesn't really have a None type by itself. It has an `Option` enum which allows you to represent a none type without the side effects. 

Even the creator of the none type says it was his greatest mistake. https://www.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare/

For example, to get a value in an array, we can use the method `.get`and provide an argument for the index:
`array.get(0)` will get the first item. What if the array is 4 items long and we try to get the 100000th item in the array? Most languages return a none type and then if you try and use that none type, it'll create a runtime error, crashing your entire application. Rust combats this by allowing you to do something like this:

```rust
let item = array.get(10000);
if let Some(i) = item {
	// could get the 10000th item in the array, handle it
	println!("Got: {}", i);
} else {
	// Didn't exist:
	println!("Doesn't exist in the array, please choose a lower index!");
}
```

this may seem a bit weird, but if you were to read deeper, it would make sense. Rust is designed to encourage you to handle *every* possible thing that could fail. e.g. you remove an item in an array that doesn't exist or you try to download an image from a website but you have no internet connection or you try to log in to an API and your token isn't valid.

## Error handling
Error handling in interpreted languages is usually done at runtime, this means that unless you write tests for it or go through the entire process of running the program and testing everything manually, there could be a blatant error with your code that you could push out onto your users who will probably be annoyed and look elsewhere.

Many compiled languages look on your source code at compile time but sometimes they don't pick things up or perhaps have dodgy code that the compiler can simply not verify. Rust is designed to destroy all errors at all stages.

It's very similar to the None type above, but slightly different. You can read more about it in the various tutorials around the internet (mentioned in #5).

## Traits & Inheritance
Inheritance is bad, here's why:

https://codeburst.io/inheritance-is-evil-stop-using-it-6c4f1caf5117

https://softwareengineering.stackexchange.com/questions/134097/why-should-i-prefer-composition-over-inheritance

Some very prominent computer scientists even hate the object oriented paradigm altogether:
http://harmful.cat-v.org/software/OO_programming/

Rust uses a system called traits to combat the issue of inheritance while keeping some of the cool and useful things about OOP.

You can read more about it in other tutorials (mentioned in #5).

## Borrow checking
C++ and C make you manage your memory by hand.

Python, Ruby, Javascript all have something called a Garbage Collector which will come around and clean up unused variables and other junk.

Garbage collectors are slow, manual memory management is laborious and will make your code do weird stuff like use ridiculous amounts of memory or randomly crash your program.

Rust uses borrow checking which is an innovative method of memory management that is faster than a garbage collector and easier, safer and more fun than manual memory management.

You can read more about it in other tutorials (mentioned in #5).

# 9. It has a great community

The reddit community `r/rust` is a great community who is happy to help. The reddit is also a place where new and exciting features, libraries and programs are showcased.

There are many discord servers who have solved many of my problems with the language and love to discuss it.

And there are plenty of meet-ups all over the world.

Here's some cool stuff that the community made:

Here's a plushie of Ferris the Crab, the Rust mascot:

http://edunham.net/2016/04/11/plushie_rustacean_pattern.html

![](http://edunham.net/_images/ferris-on-pattern.jpg)

Here's a pumpkin of Ferris:

https://imgur.com/gallery/q2ZHo

![](https://i.imgur.com/mNfEWCA.jpeg)

# 10. It maintains a perfectly sized standard library

You can entirely remove and swap out parts of the standard library with very little effort. This makes it perfect if you want to run Rust on bare metal and is a technique used by many users who wish to have Rust be as small and efficient as possible. It's also used to build things like Operating Systems and Drivers.

The standard library is not too large, it doesn't have things like random numbers, you'll need a library for that, and it doesn't have too little. It still has file operations, sorting, indexing etc...

---

Well there you have it, why I love Rust and how you can get into it yourself.

Maybe you have a new found desire to learn the language, if so, good luck!
