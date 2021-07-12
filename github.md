# Github

# Clean a repos {remote,local} tags and releases

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
