# Incremental Automation

Resources for process automation supplemental to presentation at Ruby Conf Mini 2022, _Zen and the Art of Incremental Automation_

[Talk References](#references)
[Supplemental Resources](#supplemental-resources)
[Ruby tools for incremental automation](#ruby-tools-for-incremental-automation)
[Personal Machine Automation](#personal-machine-automation)

## References

These articles greatly influenced the idea for and the content within the talk--

* [Manual Work is a Bug - Thomas A. Limoncelli](https://queue.acm.org/detail.cfm?id=3197520)

* [The Case for Incremental Automation - Jessica Abelson](https://www.transposit.com/devops-blog/devops/the-case-for-incremental-automation)

* [Do-Nothing Scripting: the key to gradual automation - Dan Slimmon](https://blog.danslimmon.com/2019/07/15/do-nothing-scripting-the-key-to-gradual-automation)

* [Gradual Automation in Ruby - Tomasz Wróbel](https://blog.arkency.com/gradual-automation-in-ruby/)

## Supplemental Resources

[Vintage Illustrations from my talk](https://oldbookillustrations.com)

[Is it worth the time? (Because there's an XKCD for everything we do, right?)](https://xkcd.com/1205)

## Ruby tools for Incremental Automation

### Rake
[Homepage/Github](https://github.com/ruby/rake)

Rake stands for Ruby Make, a standalone Ruby utility that replaces the Unix utility 'Make'. Rubyists familiar with Rails will already be familiar with rake, whether they know it or not, as many of the `rails xyz` commands are rake tasks under the hood.

As far as ease of use, low learning curve and barrier to entry, Rake can't be beat. It's so simple, Jim Weirich (Rake's original author) essentially rebuilt it onstage in several of his conference talks, [this instance](https://youtu.be/0D3KfnbTdWw?t=1256) being my favorite.

### Runbook
[Homepage/Github](https://github.com/braintree/runbook)

One of the first projects I was introduced to that tries (and succeeds!) at making full-featured Do Nothing Scripting is Runbook by Braintree. See [this blog post](https://medium.com/@patrick.blesi/https-medium-com-braintree-product-technology-runbook-be6f072cfc0d) for a similarly full-featured introduction to its philosophy and capabilities.

### Thor

Thor is a command line tool library that makes building cli's with rich behaviors easy and straightforward. It's used in Rails, Vagrant, Bundler, and many a project CLI I've worked with in my time.

The concept I wanted to fit into the talk that didn't quite ever fit was that of a project CLI tool. I love this idea to combine all the scripts and automation and documentation and much more of a project into a single utility that either lives in the codebase or an adjacent repo.

For example, if I was working on a project for 'Evolve Finance' (ficticious company as far as I know), and had a script that rotated the keys in production, I might invoke it from the command line like this...

```bash
evf keys
```

and if it could be run in staging, production, or other environments separately, it could accept arguments like...

```bash
evf keys --production
```

With `--help` pages, flags, arguments, all the bells and whistles you might need! Thor is the ruby way (tm) to get there quick.

### Boson
[Homepage](https://tagaholic.me/boson/)
[Github](https://github.com/cldwalker/boson)

I'm less familiar with this one, but saw it mentioned enough that I thought to include it. From the README--

> Boson is a modular comman/task framework. Thanks to its rich set of plugins, it differentiates itself from rake and thor by being usable from irb and the command line, having automated views generated by hirb and allowing libraries to be written as plain ruby. Works with on all major rubies for ruby >= 1.9.2

## Personal machine automation

### Tools

This list is fairly (or completely?) MacOS centric. Sorry Linux users, cover your ears!

#### Alfred

[Homepage](https://www.alfredapp.com/)
[Packal](https://www.packal.org/)

As far as I'm concerned, *the* launcher and first line of power user interaction on the Mac. Powerful workflow tools (workflows are what Alfred calls their automation), clipboard manager, app launcher, text expansion, so so much. Alfred changed the way I interact with my computer forever and I can't think of using my machine without it. I bought a lifetime license when they were on version 4, and paid for version 5 anyway because I want it to keep existing.

Packal is the biggest repository for finding workflows currently. It says Alfred 2 but it has newer ones and the old ones still mostly work.

#### Keyboard Maestro

[Homepage](https://www.keyboardmaestro.com/main/)

Whatever Alfred doesn't get done, Keyboard Maestro will. It's the one stop shop for automation on the Mac. Half the time, Alfred is launching keyboard maestro macros for me. Shell scripts, api calls, keyboard control, window management, conditional execution, variables, functions.. so much possibility here.

#### Stream Deck

[Homepage](https://www.elgato.com/en/stream-deck)

Wha? Hardware? And it's for streamers? Sure it started out for streamers, but there's so much potential here to launch and control your machine through this nifty little piece of tech. Can't remember keyboard shortcuts? Stream Deck makes little labeled buttons, customizeable, right at your fingertips.

#### Hook

[Homepage](https://hookproductivity.com)

Hook is maybe the hardest thing to explain on this list. It's a way to link two pieces of information, whether that's a file, a url, whatever. If there's a way to deep link to it, Hook probably works with it.

#### Rectangle

[Homepage](https://rectangleapp.com/)

There are many applications that will manage your windows for you.. this one is the one I use.

#### Applescript

[Official Language Guide](https://developer.apple.com/library/archive/documentation/AppleScript/Conceptual/AppleScriptLangGuide/introduction/ASLR_intro.html)

Apple's original first class citizen for automating MacOS. It's a scripting language that knows how to talk to your apps. Well.. most of your apps. Some are better supported by their developers than others, but when they are 🤩

Its syntax was supposed to be easy for non-developers to use, but really it just made it convoluted for developers to use and remained just as obtuse to non-programmers anyway. It's a little old, doesn't always work with everything, but in general Applescript is still the most powerful way to harness the inner workings of apps and string them together.

#### Better Touch Tool

[Homepage](https://folivora.ai/)

Started originally to control the touchbar and make it more useable (why Apple built the thing and never did anything with it, the world will never know), it has since grown into handling so much more. Again if there are places that Keyboard Maestro or Alfred don't cover, Better Touch Tool might be able to fill in those gaps.

#### Launch Control

[Homepage](https://www.soma-zone.com/LaunchControl/)

Launch Control is a GUI for launchd. Did you know that cron is not really how you're supposed to go about doing time-based automation on your Mac? Who knew? I sure didn't, but I DID know that my cron jobs were....unreliable to say the least.

Launchd is possibly as obtuse to use as cron, but nowhere near as well documented. I stopped trying, I just use LaunchControl.

#### Bunch

[Homepage](https://bunchapp.co/)

Want a simple, text file based way to automate your mac? Known-about-the-internet-developer Brett Terpstra has got you covered. I don't use this one myself, but its one of those things where everyone who does use it loves it.

#### Shortcuts

[Official User Guide](https://support.apple.com/guide/shortcuts/welcome/ios)

The new Apple sanctioned way to automate your machine. Easier for non-programmers.....who am I kidding, easier for programmers too, Applescript is kind of a nightmare. Not as full-featured as I'd hope, sometimes still have to drop down into Applescript.

Cross platform though! (Mostly) write once, run on MacOS, iPadOS and iOS.
