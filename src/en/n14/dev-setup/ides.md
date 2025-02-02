# IDEs

## Intro
An IDE is an Integrated Development Environment and is used for coding. In SS14 this allows you to edit code and then build and run your newly edited code with ease all in one program. There's a variety of free options but popular ones include Visual Studio Community, [Visual Studio Code (VSC)](https://code.visualstudio.com/) and JetBrains Rider. We encourage all new contributors to use VSC as it has a [Robust YAML plugin](https://marketplace.visualstudio.com/items?itemName=slava0135.robust-yaml) to make editing YAML much easier on top of its [YAML language support here](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml).

More experienced coders or people dabbling in C# may consider JetBrains Rider as it's free for open source use and can be more powerful and intuitive in the right hands.

## VSC Setup
1. Head to the Visual Studio Code Website here and run through the installation process. Keep all default options ticked. https://code.visualstudio.com/
2. When you first launch it'll ask you to select a theme, do that. On the left there is a checklist of actions to do to complete your getting started. 
3. The next after theme is "Rich support for all your languages", in here you can install the `C# Dev Kit` to make reading code easier. In this "extensions: marketplace" window you can delete the preloaded search and search for `yaml` and `robust yaml` to install those too.
4. After this is installed, close all the tabs and close down VSC. Then open it back up again.
5. Next if you've already cloned the repository via your Git client then we will do the "open folder" option. Then navigate to where you cloned the repository to and select that folder, for me that's `D:\Github\Nuclear14`. You'll get a popup about trusting the authors, tick the box then click "Yes, I trust the authors".
6. At this point the project will load all the files down the left, and in the bottom right you'll get a suggestion to get more extensions such as `Better Comments by Aaron Bond` and `vscode-fluent` which will help with adding comments to your code and the latter for seeing and creating localisation strings for yaml.
7. Congrats, you're pretty much setup. Along the far left bar you have a file explorer, search and replace function, source control which can be used instead of or in addition to a Git client if you choose, and the run and debug function. On this tab you can select the client dropdown, change it to yaml linter, then in the run dropdown along the top, run without debugging, this will test your yaml work.
