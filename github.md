# Github

## Clean a repos {remote,local} tags and releases

```bash
#!/usr/bin/env bash

echo "--- Removing remote tags"
git tag -l | xargs -n 1 git push --delete origin                                                                  
echo "--- Removing local tags"
git tag | xargs git tag -d  
echo "--- Deleting releases"
num_releases=$(gh release list | wc -l)
if [[ $num_releases -eq 0 ]]; then
    echo "--- No releases to delete, exiting."
else
    echo "--- Removing $num_releases releases"
    releases=$(gh release list | awk '{print $2}')
    for release in $releases; do
      echo "--- Removing $release"
      gh release delete -y "$release"
    done
fi
```

## markdown extensions

Displayed with distinctive colors and icons to indicate the importance of the content

### note

> [!NOTE]  
> Highlights information that users should take into account, even when skimming.

```md
> [!NOTE]  
> 
```

### tip

> [!TIP]
> Optional information to help a user be more successful.

```md
> [!TIP]  
> 
```

### important

> [!IMPORTANT]  
> Crucial information necessary for users to succeed.

```md
> [!IMPORTANT]  
> 
```

### warning

> [!WARNING]  
> Critical content demanding immediate user attention due to potential risks.

```md
> [!WARNING]  
> 
```

### caution

> [!CAUTION]
> Negative potential consequences of an action.

```md
> [!CAUTION]  
> 
```
