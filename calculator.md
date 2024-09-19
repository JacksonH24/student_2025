---
layout: page
title: Calculator
permalink: /calculator/
---

## Simple Larger Calculator

<div id="calculator">
    <input type="text" id="result" disabled />
    <br>
    <button onclick="clearResult()">C</button>
    <button onclick="appendNumber('7')">7</button>
    <button onclick="appendNumber('8')">8</button>
    <button onclick="appendNumber('9')">9</button>
    <button onclick="appendOperator('+')">+</button>
    <br>
    <button onclick="appendNumber('4')">4</button>
    <button onclick="appendNumber('5')">5</button>
    <button onclick="appendNumber('6')">6</button>
    <button onclick="appendOperator('-')">-</button>
    <br>
    <button onclick="appendNumber('1')">1</button>
    <button onclick="appendNumber('2')">2</button>
    <button onclick="appendNumber('3')">3</button>
    <button onclick="appendOperator('*')">*</button>
    <br>
    <button onclick="appendNumber('0')">0</button>
    <button onclick="appendOperator('/')">/</button>
    <button onclick="calculateResult()">=</button>
    <button onclick="appendOperator('%')">%</button>
</div>

<style>
    #calculator {
        text-align: center;
    }

    #result {
        width: 220px;
        height: 40px;
        font-size: 24px;
        margin-bottom: 10px;
        text-align: right;
    }

    button {
        width: 60px;
        height: 60px;
        font-size: 20px;
        margin: 5px;
    }
</style>

<script>
    function appendNumber(number) {
        document.getElementById('result').value += number;
    }

    function appendOperator(operator) {
        document.getElementById('result').value += operator;
    }

    function clearResult() {
        document.getElementById('result').value = '';
    }

    function calculateResult() {
        try {
            let result = eval(document.getElementById('result').value);
            document.getElementById('result').value = result;
        } catch (e) {
            document.getElementById('result').value = 'Error';
        }
    }
</script>
