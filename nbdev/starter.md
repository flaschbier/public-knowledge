# nbdev

The blog that started this endeavour: 
[nbdev: use Jupyter Notebooks for everything](https://www.fast.ai/2019/12/02/nbdev/)

```sh
pip install nbdev
# plus loads of things to do per repo
```

- (buggy) tutorial: https://nbdev.fast.ai/tutorial/
- video for the same: [nbdev tutorial | Jeremy Howard](https://www.youtube.com/watch?v=Hrs7iEYmRmg)
- Jupyter extensions: [Collapsible Headings](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/collapsible_headings/readme.html)
- nbdev [repo](https://github.com/fastai/nbdev/tree/master/nbs)

## Findings

- Never try assigning a theme to GitHub pages when activating
- Switch bt Jupyter and shell is a mess
- Saving _may be_ required to make the shell tools aware of souce code changes
- GitHub CI allows for (at least small) file system consumption
- All cells not marked are treated as tests
- GitHub CI allows for Requests 
- Rulez: https://help.github.com/en/github/site-policy/github-additional-product-terms#a-actions-usage
- Consumption: https://github.com/settings/billing (when logged on)

## Trial NBs

- repo: https://github.com/flaschbier/nbdev_try2
- docs: https://flaschbier.github.io/nbdev_try2/core/

## Side Notes

- coping with a bad commit text with [`git reset HEAD^`](https://stackoverflow.com/questions/15772134/can-i-delete-a-git-commit-but-keep-the-changes)

