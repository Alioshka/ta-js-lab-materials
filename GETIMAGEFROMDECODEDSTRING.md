# take screenshot and attach to cucumber output .json file
see [TAKESCREENSHOT.md](./TAKESCREENSHOT.md)

# get image from cucumber output .json file

* after you added image to cucumber output .json file it appeared in json in encoded string:
```
...
"embeddings": [
    {
       "data": "iVBORw0KGgoAAAANSUhEUgAABAoAAALrCAIoppdS1N+ttBoDr33WQB+lEe3...",
       "mime_type": "image/png"
    }
 ],
...
```
* and you could simply decode it back to the file:
```
let data = require(path.resolve('./e2e/output/cucumber.json'));
let imgString = data[index].elements[index].steps[index].embeddings[index].data;
let bitmap = new Buffer(imgString, 'base64');
fs.writeFileSync(somefileName + '.png', bitmap);
```
* see working example [here](https://github.com/Alioshka/ta-js-lab-awesome-report-generator/blob/master/lib/generator.js)
<br /> to make it work see [ta-js-lab-angular-protractor-cucumber-ts-seed](https://github.com/Alioshka/ta-js-lab-angular-protractor-cucumber-ts-seed): **Generate tests reports**