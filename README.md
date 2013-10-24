R-travis
========

Two tiny scripts that faciliate testing R packages with Travis CI.
To test each commit and pull request against stable *and* development versions
of R:

- add the following
[`.travis.yml`](https://github.com/krlmlr/R-travis/blob/master/misc/.travis.yml)
file to the root of your R package on GitHub
- don't forget to add `.travis.yml` to `.Rbuildignore`

```
# it is not really python, but there is no R support on Travis CI yet
language: python

env: RTRAVISPATH=~root/R-travis

# install dependencies
install:
  - sudo git clone https://github.com/krlmlr/R-travis.git $RTRAVISPATH
  - sudo $RTRAVISPATH/install

# run tests
script:
  - $RTRAVISPATH/script stable
  - $RTRAVISPATH/script devel
```
