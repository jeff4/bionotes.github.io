zis implicitly in **strict mode**.
		* This is true even when the `use strict` directive is not explicitly used.
		* This means one can't use octal integer literals within Class bodies.
		* This means one can't use the `with` statement within Class bodies.
		* Syntax errors are more likely to be reported if one declares a variable before using it.
	1. **Class** declarations like in 9-3 are *not hoisted*, **unlike in function declarations such as in 9-1**. 
		* Recall from section 8.1.1 that function definitions behave as if they had been moved to the top of the enclosing file or enclosing function.
		* Although *class declarations* are quite similar to function to *function declarations*, *Class Definitions* do **not** share this hoisting behavior. 
		* One *cannot* instantiate a class before you declare it.


#### 9.3.1 Static Methods p. 420
* One can define a static method within a Class body by prefixing the method declaration with a **static** keyword.
* Static methods are defined as *properties* of the constructor function rather than the properties of the Prototype object.
* For example, let's add the below static **parse** method to Example 9-3:

	```javascript
	static parse(s) {

		let matches = s.match(/^\((\d+)\.\.\.(\d+)\)$/);

		if (!matches) {
			throw new TypeError(`Cannot parse Range from "${s}".`)
		}
		return new Range( parseInt(matches[1]), parseInt(matches[2]) );
	}
	```
* The method defined by this code is `Range.parse()`, not... 




## register info
* to paste *```javascript* in the register **j**, type `"jp`.
* to yank next 3 words and store in register **a**, type `"ay3w`.
