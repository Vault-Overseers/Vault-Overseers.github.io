# IDEs

## Intro
An IDE is an Integrated Development Environment and is used for coding. In SS14 this allows you to edit code and then build and run your newly edited code with ease all in one program. There's a variety of free options but popular ones include Visual Studio Community, [Visual Studio Code (VSC)](https://code.visualstudio.com/) and JetBrains Rider. We encourage all new contributors to use VSC as it has a [Robust YAML plugin](https://marketplace.visualstudio.com/items?itemName=slava0135.robust-yaml) to make editing YAML much easier on top of its [YAML language support here](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml) or if you prefer, JetBrains Rider which does not have the plubin but is a very common choice.

A lot of people don't actually edit YAML in an IDE and instead use software like Notepad++ with the yaml language selected, but for beginners I'd suggest the plugin via an IDE above to hold your hand while you start out.

## VSC Setup
1. Head to the Visual Studio Code Website here and run through the installation process. Keep all default options ticked. https://code.visualstudio.com/
2. When you first launch it'll ask you to select a theme, do that. On the left there is a checklist of actions to do to complete your getting started. 
3. The next after theme is "Rich support for all your languages", in here you can install the `C# Dev Kit` to make reading code easier. In this "extensions: marketplace" window you can delete the preloaded search and search for `yaml` and `robust yaml` to install those too.
4. After this is installed, close all the tabs and close down VSC. Then open it back up again.
5. Next if you've already cloned the repository via your Git client then we will do the "open folder" option. Then navigate to where you cloned the repository to and select that folder, for me that's `D:\Github\Nuclear14`. You'll get a popup about trusting the authors, tick the box then click "Yes, I trust the authors".
6. At this point the project will load all the files down the left, and in the bottom right you'll get a suggestion to get more extensions such as `Better Comments by Aaron Bond` and `vscode-fluent` which will help with adding comments to your code and the latter for seeing and creating localisation strings for yaml.
7. Congrats, you're pretty much setup. Along the far left bar you have a file explorer, search and replace function, source control which can be used instead of or in addition to a Git client if you choose, and the run and debug function. On this tab you can select the client dropdown, change it to yaml linter, then in the run dropdown along the top, run without debugging, this will test your yaml work.

## JetBrains Rider Setup
1. Head to the JetBrains website here and hit download. https://www.jetbrains.com/rider/
2. Run through the installation process, making sure at the options page to add the program to PATH as well as selecting all the different file types it should associate with like .sln and .cs
3. Launch Rider, you'll be greeted with a prompt to add a license. Select the option that you don't have a license key and or that you'll be using the program for non-commercial use. This will let you use the program for open source development like ours.
4. After this you can launch rider, open solution and select your cloned space station 14 repository of choice. In future when you launch you can just launch straight into this.
5. In the top right hand corner you'll see a hammer icon which is to "build" the solution. Hit the dropdown beside it and select "Tools" or "Release" if that doesn't work. This makes the program more error averse so it won't crash as much.
6. Next to this is a folder with a green play button on it. This is how you'll launch the game for testing purposes. Right now it might say Content.Client or Content.Server, we will now make a compound startup so you don't need to run these two individually. To do this, hit that dropdown > edit configurations > Compound > add new run configuration > name it like Server + Client > add, Content.Client then Content.Server > hit apply and now you have a compound startup.
7. Go back out of these menus then make sure your new compound startup is selected from that dropdown. Next to the dropdown isw a replay or play looking button. Hit that or the shortcut is Ctrl + F5. This will run your configuration, launching client and server and building too.
8. If you have any errors in your setup or code, your client or server console that appears next will crash, just before it does you'll see a red error. Copy that quickly so you can interrogate what broke.
9. If you've done your first PR or changes or done something and the game is broken, check step 8 OR, in that configuration selector, select Content.YAMLLinter, this will run the yaml linter and usually give you an error specified to a file, line and column to correct. It's typically formatting or a broken prototype.
