Try to instrument the "built" files

./node_modules/.bin/istanbul instrument --output coverage ../distribution/


We can't currently run istanbul cover so we have to do the middle step manually!

QUnit test should run against instrumented files.

coverage.html does this

After Qunit has run, there should be a coverage JSON object - this is currently 
echo'd to the console in the coverage.html file - if we ran tests in Phantom / other browser, we'd need
to collect this and write to test/coverage.json

We can then run istanbul report --root test/ to generate reports.

Can also use the qunit.js file in root to run the node-qunit-phantomjs-istanbul plugin which sort of works
- still need to instrument & report "manually" though

node qunit.js
#Make sure that coverage.json from above experiment is not there!
./node_modules/.bin/istanbul report --dir cov2 --root test/
