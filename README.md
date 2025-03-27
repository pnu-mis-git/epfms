<h1>ENV LINK</h1>
<h4>https://drive.google.com/file/d/1PZNGRAzyFLpeE3yFwehC5p4p0dEvQ34n/view?usp=drive_link</h4>

<h1>SOFTWARES NEEDED</h1>
<h4>1. VSCode</h4>
<h4>2. TablePlus</h4>
<h4>3. Putty</h4>
<h4>4. Herd</h4>
<h4>5. Postman (optional)</h4>

<h1>IMPORTANT NOTES:</h1>
<h3>Our database is already hosted in laravel forge. To connect, follow the steps below.</h3>
<h4>1. Open terminal to tunnel the database hosted in the server, run "ssh -i {location of ssh key used in table plus} -L 3308:127.0.0.1:3306 forge@192.168.175.59 -N"</h4>

<h1>STEPS TO REPLICATE REPOSITORY</h1>
<h4>1. Clone the repository on your local machine's herd projects path.</h4>
<h4>2. Install https in herd for your local project.</h4>
<h4>3. Copy .env on main project.</h4>
<h4>4. Run <span style="color:red;">composer install</span> in terminal to install dependencies</h4>
<h4>5. Always run <span style="color:red;">npm run dev</span> in terminal</h4>

<h1>SOLID PRINCIPLE LINKS</h1>
<h4>1. https://www.youtube.com/watch?v=AEy7-bwsQOg</h4>
<h4>1. https://www.youtube.com/watch?v=hZVda5ezoA4</h4>

<h1>🚀 SOLID Principles in Software Development</h1>

<h2>📌 Introduction</h2>
<p>The SOLID principles are five fundamental design principles that help developers create <strong>scalable, maintainable, and flexible</strong> software. Introduced by <strong>Robert C. Martin</strong>, these principles improve object-oriented programming (OOP) by enhancing code structure and reducing dependencies.</p>

<hr>

<h2>📖 The SOLID Principles</h2>

<h3>1️⃣ Single Responsibility Principle (SRP)</h3>
<blockquote>"A class should have only one reason to change."</blockquote>
<p>Each class should handle <strong>only one feature or concern</strong>.</p>

<h4>❌ Bad Implementation</h4>
<pre>
<code>
class Report {
    public function generateReport() {
        // Logic to generate a report
    }

    public function saveToFile() {
        // Logic to save the report to a file
    }
}
</code>
</pre>

<h4>✅ Following SRP</h4>
<pre>
<code>
class ReportGenerator {
    public function generate() {
        // Logic to generate a report
    }
}

class ReportSaver {
    public function saveToFile(ReportGenerator $report) {
        // Logic to save the report
    }
}
</code>
</pre>

<hr>

<h3>2️⃣ Open/Closed Principle (OCP)</h3>
<blockquote>"Software entities should be open for extension but closed for modification."</blockquote>
<p>Code should be <strong>extendable</strong> without modifying existing logic.</p>

<h4>❌ Bad Implementation</h4>
<pre>
<code>
class PaymentProcessor {
    public function pay($type) {
        if ($type == 'paypal') {
            // Pay using PayPal
        } elseif ($type == 'stripe') {
            // Pay using Stripe
        }
    }
}
</code>
</pre>

<h4>✅ Following OCP</h4>
<pre>
<code>
interface PaymentMethod {
    public function pay();
}

class PayPal implements PaymentMethod {
    public function pay() {
        // Pay using PayPal
    }
}

class Stripe implements PaymentMethod {
    public function pay() {
        // Pay using Stripe
    }
}

class PaymentProcessor {
    public function pay(PaymentMethod $paymentMethod) {
        $paymentMethod->pay();
    }
}
</code>
</pre>

<hr>

<h3>3️⃣ Liskov Substitution Principle (LSP)</h3>
<blockquote>"Derived classes must be substitutable for their base classes without breaking functionality."</blockquote>
<p>A subclass should be usable <strong>in place of</strong> its parent class without altering correctness.</p>

<h4>❌ Bad Implementation</h4>
<pre>
<code>
class Bird {
    public function fly() {
        // Logic for flying
    }
}

class Penguin extends Bird {
    public function fly() {
        throw new Exception("Penguins can't fly!");
    }
}
</code>
</pre>

<h4>✅ Following LSP</h4>
<pre>
<code>
interface Flyable {
    public function fly();
}

class Sparrow implements Flyable {
    public function fly() {
        // Sparrow flying logic
    }
}

class Penguin {
    public function swim() {
        // Penguin swimming logic
    }
}
</code>
</pre>

<hr>

<h3>4️⃣ Interface Segregation Principle (ISP)</h3>
<blockquote>"Clients should not be forced to depend on interfaces they do not use."</blockquote>
<p>A class should <strong>only implement methods it actually needs</strong>.</p>

<h4>❌ Bad Implementation</h4>
<pre>
<code>
interface Worker {
    public function work();
    public function eat();
}

class Robot implements Worker {
    public function work() {
        // Robot working
    }

    public function eat() {
        throw new Exception("Robots don't eat!");
    }
}
</code>
</pre>

<h4>✅ Following ISP</h4>
<pre>
<code>
interface Workable {
    public function work();
}

interface Eatable {
    public function eat();
}

class Human implements Workable, Eatable {
    public function work() {
        // Human working
    }

    public function eat() {
        // Human eating
    }
}

class Robot implements Workable {
    public function work() {
        // Robot working
    }
}
</code>
</pre>

<hr>

<h3>5️⃣ Dependency Inversion Principle (DIP)</h3>
<blockquote>"High-level modules should not depend on low-level modules. Both should depend on abstractions."</blockquote>

<h4>❌ Bad Implementation</h4>
<pre>
<code>
class MySQLDatabase {
    public function connect() {
        // Connection logic
    }
}

class UserRepository {
    private $db;

    public function __construct(MySQLDatabase $db) {
        $this->db = $db;
    }
}
</code>
</pre>

<h4>✅ Following DIP</h4>
<pre>
<code>
interface DatabaseConnection {
    public function connect();
}

class MySQLDatabase implements DatabaseConnection {
    public function connect() {
        // Connection logic
    }
}

class UserRepository {
    private DatabaseConnection $db;

    public function __construct(DatabaseConnection $db) {
        $this->db = $db;
    }
}
</code>
</pre>
