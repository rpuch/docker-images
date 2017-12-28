#
# An image which is published as rpuch/jdk8-chromedriver to the standard
# Docker Hub.
# Used to run Selenium tests with Google Chrome browser.
#
# Build: docker build -t rpuch/jdk8-chromedriver .

# An important note: in a Docker container, we are under root user by default.
# Google Chrome refuses to launch under root unless you specify --no-sandbox
# This can be done like this in Java:
#
# driver = new ChromeDriver(new ChromeOptions().addArguments("--no-sandbox"));
#

FROM payneteasy/jdk-8

# Installing Google Chrome browser from Google repository.
# Current version is installed.
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
RUN sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
RUN apt-get update
RUN apt-get install google-chrome-stable xvfb -y

# Installing chromedriver from Google site.
# A specific version is installed.
# TODO: we probably either need to install here the most recent version
# (like it's made for Chrome), or install a specific version of Chrome
# instead of the most recent one.
RUN wget https://chromedriver.storage.googleapis.com/2.34/chromedriver_linux64.zip \
    && unzip chromedriver_linux64.zip -d /usr/bin/ \
    && chmod a+x /usr/bin/chromedriver

