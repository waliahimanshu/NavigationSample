Android Architecture Components Advanced Navigation Sample
==============================================


This reproduce the navigation bug we have in our app.

- switch to `reproduce-cookpad-bug` branch 
- Changes I did to reproduce 
  - bump the nav version
  - combined all the nav graphs to single file  see diff [f6602e2102df4022b20156ebbff00d59e4a52c2f](https://github.com/waliahimanshu/NavigationSample/commit/f6602e2102df4022b20156ebbff00d59e4a52c2f)

Where does the bug happen 

in the librarary 
`` 
 public fun setupWithNavController()
`` 
Go to Line 620

```
 view.menu.forEach { item ->
                        if (destination.matchDestination(item.itemId)) {
                            item.isChecked = true
                        }
                    }
```

When there is another fragment on top of home fragment of bottom bar menue (in our case this could be user or recipe view)
the `matchDestination` fails, hence  `item.isChecked = true` is never executed which selected the bottom bar 

- Run the app to see the bheaviour 
![nav_bug](https://user-images.githubusercontent.com/7093480/175279445-3e86a3c8-5e81-4dd3-9d31-b6ecec1872ba.gif)
