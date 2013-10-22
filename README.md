R-travis
========

Two tiny scripts that faciliate testing R packages with Travis CI.
Add the following `.travis.yml` file to the root of your R package on GitHub
to test each commit and pull request against stable *and* development versions
of R:

```
# it is not really python, but there is no R support on Travis CI yet
language: python

# install dependencies
install:
  - sudo git clone https://github.com/krlmlr/R-travis.git ~/R-travis
  - sudo ~/R-travis/install

# run tests
script:
  - "for mode in stable devel; do ~/R-travis/script $mode; done"
```
