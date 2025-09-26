<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BuggersNet C++ Academy</title>
    <style>
        body {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }

        .header {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            padding: 1rem 2rem;
            box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header-content {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: #4a5568;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .logo::before {
            content: "💻";
            font-size: 2rem;
        }

        .progress-bar {
            flex: 1;
            max-width: 300px;
            margin: 0 2rem;
            background: #e2e8f0;
            border-radius: 20px;
            height: 12px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #48bb78, #38a169);
            border-radius: 20px;
            transition: width 0.3s ease;
            width: 0%;
        }

        .stats {
            display: flex;
            gap: 1rem;
            align-items: center;
        }

        .stat {
            display: flex;
            align-items: center;
            gap: 0.3rem;
            font-weight: 600;
            color: #4a5568;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }

        .main-content {
            display: grid;
            grid-template-columns: 300px 1fr;
            gap: 2rem;
            margin-top: 1rem;
        }

        .sidebar {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 1.5rem;
            height: fit-content;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }

        .level-selector {
            margin-bottom: 1.5rem;
        }

        .level-selector h3 {
            margin: 0 0 1rem 0;
            color: #2d3748;
            font-size: 1.1rem;
        }

        .level-grid {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 0.5rem;
        }

        .level-btn {
            aspect-ratio: 1;
            border: none;
            border-radius: 12px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.2s ease;
            font-size: 0.9rem;
        }

        .level-btn.completed {
            background: #48bb78;
            color: white;
        }

        .level-btn.current {
            background: #4299e1;
            color: white;
            transform: scale(1.1);
        }

        .level-btn.locked {
            background: #e2e8f0;
            color: #a0aec0;
            cursor: not-allowed;
        }

        .level-btn:hover:not(.locked) {
            transform: scale(1.05);
        }

        .content-area {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 2rem;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }

        .lesson-header {
            text-align: center;
            margin-bottom: 2rem;
        }

        .lesson-title {
            font-size: 2rem;
            color: #2d3748;
            margin: 0 0 0.5rem 0;
        }

        .lesson-subtitle {
            color: #718096;
            font-size: 1.1rem;
        }

        .question-container {
            margin-bottom: 2rem;
        }

        .question {
            background: #f7fafc;
            border-radius: 15px;
            padding: 1.5rem;
            margin-bottom: 1rem;
            border-left: 4px solid #4299e1;
        }

        .question h4 {
            margin: 0 0 1rem 0;
            color: #2d3748;
            font-size: 1.2rem;
        }

        .code-block {
            background: #1a202c;
            color: #e2e8f0;
            padding: 1rem;
            border-radius: 8px;
            font-family: 'Courier New', monospace;
            margin: 1rem 0;
            overflow-x: auto;
        }

        .answer {
            background: #e6fffa;
            border-radius: 10px;
            padding: 1rem;
            margin-top: 0.5rem;
            border-left: 3px solid #38b2ac;
        }

        .quiz-section {
            background: #fff5f5;
            border-radius: 15px;
            padding: 1.5rem;
            margin-top: 2rem;
            border: 2px solid #fed7d7;
        }

        .quiz-question {
            margin-bottom: 1rem;
        }

        .quiz-options {
            display: grid;
            gap: 0.5rem;
            margin: 1rem 0;
        }

        .quiz-option {
            background: white;
            border: 2px solid #e2e8f0;
            border-radius: 10px;
            padding: 1rem;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .quiz-option:hover {
            border-color: #4299e1;
            background: #ebf8ff;
        }

        .quiz-option.selected {
            border-color: #4299e1;
            background: #ebf8ff;
        }

        .quiz-option.correct {
            border-color: #48bb78;
            background: #f0fff4;
        }

        .quiz-option.incorrect {
            border-color: #f56565;
            background: #fff5f5;
        }

        .btn {
            background: #4299e1;
            color: white;
            border: none;
            padding: 0.75rem 1.5rem;
            border-radius: 10px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s ease;
            font-size: 1rem;
        }

        .btn:hover {
            background: #3182ce;
            transform: translateY(-1px);
        }

        .btn:disabled {
            background: #a0aec0;
            cursor: not-allowed;
            transform: none;
        }

        .btn-success {
            background: #48bb78;
        }

        .btn-success:hover {
            background: #38a169;
        }

        .navigation {
            display: flex;
            justify-content: space-between;
            margin-top: 2rem;
            padding-top: 1rem;
            border-top: 1px solid #e2e8f0;
        }

        .level-complete {
            text-align: center;
            padding: 2rem;
            background: linear-gradient(135deg, #48bb78, #38a169);
            color: white;
            border-radius: 20px;
            margin: 2rem 0;
        }

        .level-complete h2 {
            margin: 0 0 1rem 0;
            font-size: 2rem;
        }

        .score-display {
            font-size: 1.5rem;
            font-weight: bold;
            margin: 1rem 0;
        }

        .footer {
            text-align: center;
            padding: 2rem;
            color: rgba(255, 255, 255, 0.8);
            margin-top: 2rem;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-top: 1rem;
        }

        .social-link {
            color: rgba(255, 255, 255, 0.8);
            text-decoration: none;
            padding: 0.5rem;
            border-radius: 8px;
            transition: all 0.2s ease;
        }

        .social-link:hover {
            background: rgba(255, 255, 255, 0.1);
            color: white;
        }

        @media (max-width: 768px) {
            .main-content {
                grid-template-columns: 1fr;
            }
            
            .header-content {
                flex-direction: column;
                gap: 1rem;
            }
            
            .progress-bar {
                max-width: 200px;
                margin: 0;
            }
        }
    </style>
</head>
<body>
    <div class="header">
        <div class="header-content">
            <div class="logo">BuggersNet C++ Academy</div>
            <div class="progress-bar">
                <div class="progress-fill" id="progressFill"></div>
            </div>
            <div class="stats">
                <div class="stat">
                    <span>🔥</span>
                    <span id="streak">0</span>
                </div>
                <div class="stat">
                    <span>💎</span>
                    <span id="gems">0</span>
                </div>
                <div class="stat">
                    <span>⭐</span>
                    <span id="score">0</span>
                </div>
            </div>
        </div>
    </div>

    <div class="container">
        <div class="main-content">
            <div class="sidebar">
                <div class="level-selector">
                    <h3>Choose Your Level</h3>
                    <div class="level-grid" id="levelGrid"></div>
                </div>
            </div>

            <div class="content-area">
                <div id="lessonContent">
                    <div class="lesson-header">
                        <h1 class="lesson-title">Welcome to C++ Academy!</h1>
                        <p class="lesson-subtitle">Master C++ from basics to advanced programming</p>
                    </div>
                    <div style="text-align: center; padding: 2rem;">
                        <p style="font-size: 1.2rem; color: #4a5568; margin-bottom: 2rem;">
                            Start your journey by selecting Level 1 from the sidebar. Each level contains 20 comprehensive lessons with interactive quizzes!
                        </p>
                        <button class="btn" onclick="startLevel(1)">Start Learning C++</button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <div class="footer">
        <p>&copy; 2024 BuggersNet - Teaching C++ Programming to Everyone</p>
        <div class="social-links">
            <a href="https://www.instagram.com/bugersnetofficial" target="_blank" rel="noopener noreferrer" class="social-link">
                📱 @bugersnetofficial
            </a>
            <a href="https://www.instagram.com/_nynoah_" target="_blank" rel="noopener noreferrer" class="social-link">
                👨‍💻 @_nynoah_
            </a>
        </div>
    </div>

    <script>
        // Course data structure
        const courseData = {
            1: {
                title: "C++ Basics - Getting Started",
                questions: [
                    {
                        question: "What is C++?",
                        content: "C++ is a general-purpose programming language created by Bjarne Stroustrup as an extension of the C programming language.",
                        code: `// Your first C++ program
#include <iostream>
using namespace std;

int main() {
    cout << "Hello, World!" << endl;
    return 0;
}`,
                        answer: "C++ is an object-oriented programming language that supports both procedural and object-oriented programming paradigms. It's widely used for system programming, game development, and applications requiring high performance.",
                        quiz: {
                            question: "What does '#include <iostream>' do in C++?",
                            options: [
                                "Includes input/output stream functionality",
                                "Creates a new variable",
                                "Defines a function",
                                "Ends the program"
                            ],
                            correct: 0
                        }
                    },
                    {
                        question: "How do you declare variables in C++?",
                        content: "Variables in C++ must be declared with a specific data type before they can be used.",
                        code: `// Variable declarations
int age = 25;
double price = 99.99;
char grade = 'A';
string name = "John";
bool isStudent = true;`,
                        answer: "Variables are declared by specifying the data type followed by the variable name. You can optionally initialize them with a value using the assignment operator (=).",
                        quiz: {
                            question: "Which is the correct way to declare an integer variable?",
                            options: [
                                "int number = 10;",
                                "integer number = 10;",
                                "num number = 10;",
                                "var number = 10;"
                            ],
                            correct: 0
                        }
                    },
                    {
                        question: "What are the basic data types in C++?",
                        content: "C++ provides several built-in data types to store different kinds of information.",
                        code: `// Basic data types
int whole_number = 42;        // Integer
double decimal = 3.14159;     // Double precision floating point
float small_decimal = 2.5f;   // Single precision floating point
char letter = 'A';            // Single character
bool flag = true;             // Boolean (true/false)
string text = "Hello";        // String of characters`,
                        answer: "The basic data types include: int (integers), double/float (decimal numbers), char (single characters), bool (true/false values), and string (text).",
                        quiz: {
                            question: "Which data type would you use to store a person's age?",
                            options: [
                                "int",
                                "char",
                                "bool",
                                "string"
                            ],
                            correct: 0
                        }
                    },
                    {
                        question: "How do you output text in C++?",
                        content: "The cout object is used to display output to the console in C++.",
                        code: `#include <iostream>
using namespace std;

int main() {
    cout << "Hello World!" << endl;
    cout << "My age is: " << 25 << endl;
    cout << "Price: $" << 99.99 << endl;
    return 0;
}`,
                        answer: "Use 'cout <<' followed by the text or variable you want to display. Use 'endl' to create a new line.",
                        quiz: {
                            question: "What does 'endl' do in C++?",
                            options: [
                                "Creates a new line",
                                "Ends the program",
                                "Declares a variable",
                                "Includes a library"
                            ],
                            correct: 0
                        }
                    },
                    {
                        question: "How do you get input from users?",
                        content: "The cin object is used to read input from the user in C++.",
                        code: `#include <iostream>
using namespace std;

int main() {
    string name;
    int age;
    
    cout << "Enter your name: ";
    cin >> name;
    
    cout << "Enter your age: ";
    cin >> age;
    
    cout << "Hello " << name << ", you are " << age << " years old!" << endl;
    return 0;
}`,
                        answer: "Use 'cin >>' followed by the variable where you want to store the input. The program will wait for the user to type something and press Enter.",
                        quiz: {
                            question: "Which operator is used with cin to read input?",
                            options: [
                                ">>",
                                "<<",
                                "==",
                                "++"
                            ],
                            correct: 0
                        }
                    }
                ]
            },
            2: {
                title: "Operators and Expressions",
                questions: [
                    {
                        question: "What are arithmetic operators?",
                        content: "Arithmetic operators perform mathematical calculations on numeric values.",
                        code: `int a = 10, b = 3;
cout << "Addition: " << a + b << endl;      // 13
cout << "Subtraction: " << a - b << endl;   // 7
cout << "Multiplication: " << a * b << endl; // 30
cout << "Division: " << a / b << endl;       // 3
cout << "Modulus: " << a % b << endl;        // 1`,
                        answer: "Arithmetic operators include: + (addition), - (subtraction), * (multiplication), / (division), and % (modulus for remainder).",
                        quiz: {
                            question: "What does the % operator do?",
                            options: [
                                "Returns the remainder of division",
                                "Calculates percentage",
                                "Multiplies by 100",
                                "Divides by 100"
                            ],
                            correct: 0
                        }
                    },
                    {
                        question: "What are comparison operators?",
                        content: "Comparison operators compare two values and return true or false.",
                        code: `int x = 5, y = 10;
cout << (x == y) << endl;  // 0 (false)
cout << (x != y) << endl;  // 1 (true)
cout << (x < y) << endl;   // 1 (true)
cout << (x > y) << endl;   // 0 (false)
cout << (x <= y) << endl;  // 1 (true)
cout << (x >= y) << endl;  // 0 (false)`,
                        answer: "Comparison operators include: == (equal), != (not equal), < (less than), > (greater than), <= (less than or equal), >= (greater than or equal).",
                        quiz: {
                            question: "Which operator checks if two values are equal?",
                            options: [
                                "==",
                                "=",
                                "!=",
                                "<>"
                            ],
                            correct: 0
                        }
                    }
                ]
            }
        };

        // Game state
        let currentLevel = 0; // Start at 0 so level 1 shows as available
        let currentQuestion = 0;
        let completedLevels = [];
        let userStats = {
            streak: 0,
            gems: 0,
            score: 0
        };

        // Initialize the application
        function initApp() {
            generateLevelGrid();
            updateStats();
            updateProgress();
        }

        // Generate level grid
        function generateLevelGrid() {
            const grid = document.getElementById('levelGrid');
            grid.innerHTML = '';
            
            for (let i = 1; i <= 100; i++) {
                const btn = document.createElement('button');
                btn.className = 'level-btn';
                btn.textContent = i;
                
                if (completedLevels.includes(i)) {
                
