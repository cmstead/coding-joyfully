<!--bl
(filemeta
    (title "Change Identification Feedback"))
/bl-->

In order to get the best change identification feedback possible, it is important to think of our tests as living software documentation. The way our tests stay alive is that we run them often and use the output to ensure our software continues to work as expected.  This means test names, descriptions and error messaging be as clear and domain-related as possible.

In the time I have worked as a software developer, I have written tests which had terrible descriptions and wonderful descriptions.  The way I differentiated the two is how much context I could regain later when I was working for figure out what broke and why.

It is fairly common to see tests which look like the following:

```javascript
describe('helper utility', function () {

    it('converts a string to a buffer', function () {
        const expectedResult = [ '77', '121', '32', '83', '116', '114', '105', '110', '103' ];

        const result = conversionHelper.convertValue('My String');
        const resultArray = result.reduce(function(result, charValue) {
                return result.concat([charValue.toString()]);
            }, []);
        
        assert.isTrue(result instanceof Buffer);
        assert.equal(JSON.stringify(result), JSON.stringify(result))
    });

});
```

This example leaves a lot of communication out in the cold.  It's not clear, without reading the every line of the test case, what call does the conversion.  Moreover, we can't clearly discern the module we want to work with by the top level description of the test. There are also deeper issues arount context and noisy code, but we will revisit those concerns in the next section.

Without going into how, I claim we can do better.  By making just a few changes, we can actually build a lot of context around change identification which will help us narrow down the culprit for any test breakages. 

```javascript
describe('conversionHelper', function () {
    describe('string to hex converter - convertValue', function () {
        it('converts a string value to a buffer', function () {
            const expectedResult = [ '77', '121', '32', '83', '116', '114', '105', '110', '103' ];

            const result = conversionHelper.convertValue('My String');
            const resultArray = result.reduce(function(result, charValue) {
                    return result.concat([charValue.toString()]);
                }, []);
            
            assert.isTrue(result instanceof Buffer,
                'ConvertValue did not return a buffer!');
            assert.equal(JSON.stringify(result), JSON.stringify(result),
                'Converted buffer did not match expected output!')
        });
    });
});
```