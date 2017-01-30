# Change the Name and Email of Commits:

```
git filter-branch --env-filter '
OLD_EMAIL="your-old-email@example.com"
CORRECT_NAME="Your Correct Name"
CORRECT_EMAIL="your-correct-email@example.com"
if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$CORRECT_NAME"
    export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$CORRECT_NAME"
    export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags

or:

git filter-branch -f --env-filter '[ "$GIT_AUTHOR_NAME"="<old name>" ] && GIT_AUTHOR_NAME="<new name>" && GIT_COMMITTER_NAME="<new name>" GIT_AUTHOR_EMAIL="<new email>" && GIT_COMMITTER_EMAIL="<new email>"'


commit that with
git push -f
```
