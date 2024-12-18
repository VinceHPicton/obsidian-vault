A OO programming technique where a class receives its dependencies (other objects, functions, or primitives it relies on) from an external source rather than creating them itself.

**Example with objects**

**Without DI**
class CoffeeMaker {
    private coffeeMachine = new CoffeeMachine(); // Creates its own dependency.
    brew() {
        this.coffeeMachine.makeCoffee();
    }
}

**With DI**
class CoffeeMaker {
    constructor(private coffeeMachine: CoffeeMachine) {} // Receives dependency.

    brew() {
        this.coffeeMachine.makeCoffee();
    }
}

const coffeeMachine = new CoffeeMachine();
const coffeeMaker = new CoffeeMaker(coffeeMachine); // Inject dependency.

Note that here, the code calling the CoffeeMaker is where the dependency object is created, NOT in the class itself. This is the essence of DI.

**With a DI framework**
@Injectable()
class CoffeeMachine {
    makeCoffee() {
        console.log('Brewing coffee...');
    }
}

@Injectable()
class CoffeeMaker {
    constructor(private coffeeMachine: CoffeeMachine) {}

    brew() {
        this.coffeeMachine.makeCoffee();
    }
}

*Called when a call is made to the endpoint*

Here the object is never explicitly instantiated and passed, the DI framework does that behind the scenes with its magic.

**Example of passing functions or primitive data**
// A simple logger function (non-object dependency)
function logger(message: string) {
    console.log(`[LOG]: ${message}`);
}

// CoffeeMachine class that takes in dependencies via its constructor
class CoffeeMaker {
    private temperature: number; // Primitive value
    private log: (message: string) => void; // Function

    constructor(temperature: number, log: (message: string) => void) {
        this.temperature = temperature;
        this.log = log;
    }

    brew() {
        this.log(`Brewing coffee at ${this.temperature}°C...`);
        console.log('Coffee is ready!');
    }
}

// Manually injecting dependencies
const temperature = 85; // Primitive dependency
const logFunction = logger; // Function dependency

// Instantiate CoffeeMaker with injected dependencies
const coffeeMaker = new CoffeeMaker(temperature, logFunction);

// Use the CoffeeMaker
coffeeMaker.brew();
