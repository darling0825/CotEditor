
Contributing Guidelines
==========================

General Feedback
--------------------------

Create a new issue on our [Issues page](https://github.com/coteditor/CotEditor/issues). You can write your feedback either in English or in Japanese.

Bug reports __must__ include your environment. You can generate a bug report template automatically in CotEditor selecting "Help" > "Create Bug Report…" in the menu.



Pull-Request
--------------------------

- Make a topic branch, instead commit to the master or develop branch.


### General Code Improvements

Bug fixes and improvements are welcome. If you wanna add a new feature or the change is huge, it's better at first to ask the team whether your idea will be accepted.

By adding code, please follow our coding style guide below. 


### Localization

Fixing/updating existing localizations is always welcome. The project team may add `FIXME:` tag as a comment in the localized strings files, if there are updated strings to be localized.

By localization, use OS X standard terms. It might be helpful for you to study native Apple applications like TextEdit.app or the System Preferences to know how Apple localizes terms in their apps.

If your localization makes the Autolayout destroy, just tell us about it with a screenshot when you make a pull-request. We'll update the xib file to layout your localized terms correctly.

#### Submit a new localization

We recommend to copy .strings files in CotEditor/ja.lproj/ directory in order to use them as templates, because Japanese localization is always up-to-date and well organized.
Note that you don't need to localize the Unicode block names in the `Unicode.strings` file.


### Syntax Styles

#### Add a new bundled syntax style

Put just your new syntax stye into `/CotEditor/syntaxes/` directory. You don't need to modify `SyntaxMap.json` file. It's generated automatically on build.

The license for the bundled syntax styles should be "Same as CotEditor".

If the syntax language is relatively minor, we recommend you to distribute it as an additional syntax style by your own way, and just add a link to our [wiki page](https://github.com/coteditor/CotEditor/wiki/Additional-Syntax-Styles).


### Themes

We aren't accepting pull-requests adding bundled theme at the moment. You can distribute it as an additional theme by your own way, and add a link to our [wiki page](https://github.com/coteditor/CotEditor/wiki/Additional-Themes).


### Graphics Resources

We aren't accepting pull-requests for image resources. [1024jp](https://github.com/1024jp) is enjoying to create and brush-up the graphics ;). Please just point out on the Issues page if graphic resource has some kind of mistake to be fixed.


Coding Style Guide
--------------------------

Please follow the style of the existing codes in CotEditor.

- Leave reasonable comments.
- Never omit `self`.
- Make classes `final` by default.
- Insert a blank line after class/function statement line.
	```Swift
	/// say moof.
	func moof() {
		
		print("moof")
	}
	```
- Use `\`self\`` to unwrap weak self in block instead of strongSelf.
	```Swift
	// OK
    DispatchQueue.main.async { [weak self] in
        let `self` = self else { return }
        
        // ...
    }
    
    // NG
    DispatchQueue.main.async { [weak self] in
        let strongSelf = self else { return }
        
        // ...
    }
	```
- Don't declare `@IBOutlet` properties with `!`.
	```Swift
	// OK
    @IBOutlet private weak var button: NSButton?
    
    // NG
    @IBOutlet private weak var button: NSButton!
	```
- Write `guard` statement in oneline if just return a simple value.
	```Swift
	// prefer
    guard let foo = foo else { return nil }
    
    // instead of
    guard let foo = foo else {
        return nil
    }
	```
