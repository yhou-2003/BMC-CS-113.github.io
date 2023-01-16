CS113
=============================

Introduction to Computer Science - CS113 (Bryn Mawr College Spring 2023)

### Running locally:
Run `bundle exec jekyll serve`

### Adding staff to course website

1. Create a new entry to [_data/staff.yml](https://github.com/BMC-CS-113/website/blob/main/_data/staff.yaml) where you will add your information
2. Add a headshot to [assets/img/staff](https://github.com/BMC-CS-113/website/tree/main/assets/img/staff).
3. Building the website locally to test that your changes work
4. Commit the new files to a new branch and create a pull request and tag @azpoliak in the pull request.


### Copying over the CS webserver
`scp -r _site/* apoliak@symbolics.cs.brynmawr.edu:/var/www/html/cs113/website`

### Credits
This course website is based on the template from crowdsourcing-class.github.io
