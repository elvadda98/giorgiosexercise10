<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vocabulary Exercise: General English</title>
    <style>
        :root {
            --primary-color: #00897B; /* Teal */
            --secondary-color: #80CBC4; /* Light Teal */
            --background-color: #F4F6F6;
            --container-bg: #FFFFFF;
            --correct-color: #4CAF50;
            --incorrect-color: #F44336;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: var(--background-color);
            color: #333;
            line-height: 1.6;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            background-color: var(--container-bg);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }

        h1 {
            color: var(--primary-color);
            text-align: center;
            margin-bottom: 25px;
            font-size: 2em;
        }

        /* --- Navigation --- */
        .nav-buttons {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 30px;
        }

        .nav-buttons button {
            padding: 10px 20px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1em;
            font-weight: 600;
            transition: all 0.3s ease;
            background: #E0F2F1;
            color: var(--primary-color);
        }

        .nav-buttons button.active,
        .nav-buttons button:hover {
            background: var(--primary-color);
            color: white;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
        }

        .section {
            padding: 20px 0;
            border-top: 1px solid #EEE;
            display: none;
        }

        .section.active {
            display: block;
        }

        /* --- Scoreboard --- */
        #score-display {
            position: absolute;
            top: 20px;
            right: 20px;
            font-size: 1.1em;
            font-weight: 600;
            color: var(--primary-color);
            background: var(--secondary-color);
            padding: 8px 15px;
            border-radius: 5px;
        }

        /* --- Vocabulary List --- */
        .vocab-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px;
            margin-bottom: 10px;
            border-bottom: 1px dashed var(--secondary-color);
        }

        .vocab-item:last-child {
            border-bottom: none;
        }

        .vocab-word-details {
            flex-grow: 1;
        }

        .word {
            font-weight: 700;
            color: var(--primary-color);
            font-size: 1.2em;
        }

        .context {
            font-style: italic;
            color: #777;
            font-size: 0.9em;
            margin-left: 10px;
        }

        .explanation, .example {
            margin-top: 5px;
            font-size: 0.95em;
        }

        .speak-button {
            background: var(--secondary-color);
            color: var(--primary-color);
            border: none;
            padding: 8px 12px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            transition: background 0.2s;
        }

        .speak-button:hover {
            background: var(--primary-color);
            color: white;
        }

        /* --- Word Bank Styling --- */
        .word-bank {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            padding: 15px;
            margin-bottom: 20px;
            border-radius: 10px;
            background: linear-gradient(135deg, #E8F5E9 0%, #B9F6CA 100%);
            border: 1px solid var(--correct-color);
            justify-content: center;
            font-weight: 600;
            color: #1B5E20;
        }

        .word-bank span {
            padding: 5px 12px;
            background-color: white;
            border-radius: 20px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        /* --- Fill in the Gaps (Writing) --- */
        .gap-sentence {
            padding: 10px 0;
            border-bottom: 1px dotted #CCC;
            margin-bottom: 15px;
        }

        .gap-sentence input[type="text"] {
            padding: 8px;
            border: 1px solid var(--secondary-color);
            border-radius: 5px;
            font-size: 1em;
            width: 150px;
            text-align: center;
            margin: 0 5px;
            transition: border-color 0.3s;
        }

        .gap-sentence input:focus {
            border-color: var(--primary-color);
            outline: none;
        }

        .feedback {
            margin-left: 15px;
            font-weight: 600;
        }

        .writing-controls {
            display: flex;
            gap: 15px;
            margin-top: 20px;
            justify-content: center;
        }

        .writing-controls button {
            padding: 10px 25px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 700;
            transition: background 0.3s;
        }

        #check-writing {
            background: var(--primary-color);
            color: white;
        }

        #check-writing:hover {
            background: #00695C;
        }

        #reset-writing {
            background: #EEE;
            color: #333;
        }

        #reset-writing:hover {
            background: #DDD;
        }

        /* --- Match Definitions --- */
        .match-container {
            display: flex;
            justify-content: space-around;
            gap: 20px;
        }

        .match-column {
            flex-basis: 48%;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .match-item {
            padding: 12px;
            border: 2px solid var(--secondary-color);
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            user-select: none;
            min-height: 40px;
            display: flex;
            align-items: center;
            background-color: var(--container-bg);
        }

        .match-word {
            font-weight: 700;
            color: var(--primary-color);
        }

        .match-definition {
            font-style: italic;
        }

        .match-selected {
            border-color: var(--primary-color) !important;
            background-color: #E0F7FA;
            box-shadow: 0 0 10px rgba(0, 137, 123, 0.3);
        }

        .match-correct {
            background-color: var(--correct-color) !important;
            color: white;
            border-color: var(--correct-color) !important;
            cursor: default;
            box-shadow: none;
        }

        .match-incorrect {
            animation: shake 0.5s;
            border-color: var(--incorrect-color) !important;
            background-color: #FFEBEE;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            20%, 60% { transform: translateX(-5px); }
            40%, 80% { transform: translateX(5px); }
        }

        /* --- Fill in the Gaps (Pronunciation) --- */
        .pron-sentence {
            display: flex;
            align-items: center;
            padding: 10px 0;
            border-bottom: 1px dotted #CCC;
            margin-bottom: 15px;
        }

        .pron-sentence p {
            flex-grow: 1;
            margin: 0;
            display: flex;
            align-items: center;
        }

        .pron-blank {
            display: inline-block;
            width: 150px;
            height: 25px;
            line-height: 25px;
            text-align: center;
            border-bottom: 2px dashed #999;
            margin: 0 5px;
            font-weight: 600;
            color: var(--primary-color);
        }

        .pron-correct {
            border-bottom: 2px solid var(--correct-color);
            color: var(--correct-color);
        }

        .mic-button {
            background: none;
            border: none;
            cursor: pointer;
            font-size: 1.5em;
            padding: 5px;
            transition: transform 0.2s;
        }

        .mic-button:hover {
            transform: scale(1.1);
        }
        
        .mic-listening {
            color: var(--incorrect-color);
            animation: pulse 1s infinite;
        }

        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.5; }
            100% { opacity: 1; }
        }

        .pron-feedback {
            margin-left: 15px;
            font-size: 0.9em;
            font-style: italic;
        }

    </style>
</head>
<body>

    <div id="score-display">Score: 0 / 33</div>

    <div class="container">
        <h1>English Vocabulary Practice</h1>

        <div class="nav-buttons">
            <button onclick="showSection('vocab-list', this)" class="active">📚 Vocabulary List</button>
            <button onclick="showSection('writing-gaps', this)">✍️ Fill in the Gaps</button>
            <button onclick="showSection('match-defs', this)">🧠 Match Definitions</button>
            <button onclick="showSection('pronunciation-gaps', this)">🗣️ Pronunciation</button>
        </div>

        <div id="vocab-list" class="section active">
            <h2>Vocabulary List & Examples</h2>
            <div id="vocab-items-container">
                </div>
        </div>

        <div id="writing-gaps" class="section">
            <h2>✍️ Fill in the Gaps (Writing)</h2>
            <p>Use the words in the bank to complete the sentences. Type the word exactly as it appears.</p>
            <div id="writing-word-bank" class="word-bank">
                </div>
            <div id="writing-sentences-container">
                </div>
            <div class="writing-controls">
                <button id="check-writing" onclick="checkWritingGaps()">Check Answers</button>
                <button id="reset-writing" onclick="resetWritingGaps()">Reset</button>
            </div>
        </div>

        <div id="match-defs" class="section">
            <h2>🧠 Match Definitions</h2>
            <p>Click a word on the left, then click its correct definition on the right.</p>
            <div class="match-container" id="match-container">
                <div class="match-column" id="match-words-container">
                    </div>
                <div class="match-column" id="match-definitions-container">
                    </div>
            </div>
        </div>

        <div id="pronunciation-gaps" class="section">
            <h2>🗣️ Fill in the Gaps (Pronunciation)</h2>
            <p>Press the microphone button, say the missing word to fill the blank.</p>
            <div id="pron-word-bank" class="word-bank">
                </div>
            <div id="pron-sentences-container">
                </div>
        </div>

    </div>

    <script>
        // --- DATA ---
        const vocabData = [
            {
                word: "dishes",
                context: "plural of 'dish', meaning items of tableware or prepared food",
                explanation: "Plates, bowls, cups, and cooking utensils, especially those that need washing, or the prepared food itself.",
                example: "After the party, we had a mountain of dirty dishes to wash.",
                writingSentence: "Could you please clear the ___ from the table before dessert?",
                pronSentence: "I'm tired of eating the same five ___ every week; let's try something new.",
                definition: "Items of tableware used for serving or eating food, or prepared food courses.",
            },
            {
                word: "municipality",
                context: "city or town with its own local government",
                explanation: "A city or town that has corporate status and a local government.",
                example: "The new recycling program was implemented by the local municipality.",
                writingSentence: "Contact the local ___ to get a building permit for your new fence.",
                pronSentence: "Our tax money goes to funding services provided by the ___.",
                definition: "A city or town that has its own governing body and corporate status.",
            },
            {
                word: "waste",
                context: "material that is eliminated or discarded as no longer useful",
                explanation: "Unwanted or unusable material, substances, or by-products that are discarded.",
                example: "We need to reduce the amount of plastic waste we produce every day.",
                writingSentence: "She tries hard not to ___ food by planning her meals carefully.",
                pronSentence: "The factory was heavily fined for dumping toxic ___ into the river.",
                definition: "Unwanted or unusable materials that are discarded after a substance is used or produced.",
            },
            {
                word: "pollution",
                context: "harmful substances in the environment",
                explanation: "The presence in or introduction into the environment of a substance or thing that has harmful or poisonous effects.",
                example: "Air pollution in major cities is a serious health concern.",
                writingSentence: "Vehicle exhaust is a major source of air ___ in this region.",
                pronSentence: "They are campaigning to stop the river ___ caused by industrial runoff.",
                definition: "The presence of substances that cause harmful or poisonous effects in the environment.",
            },
            {
                word: "hard",
                context: "difficult to do or manage",
                explanation: "Requiring a great deal of effort or endurance; difficult.",
                example: "It was a hard exam, and I had to study for weeks to pass it.",
                writingSentence: "Climbing Mount Everest is an incredibly ___ task for anyone.",
                pronSentence: "Learning a new language is ___ but rewarding if you stick with it.",
                definition: "Requiring a great deal of effort, determination, or endurance; not easy.",
            },
            {
                word: "size",
                context: "dimensions or magnitude of something",
                explanation: "The overall extent or dimensions of something; how big or small it is.",
                example: "What size shoe do you wear? I need to know your exact size.",
                writingSentence: "She ordered a large pizza, but they accidentally delivered the medium ___.",
                pronSentence: "You should check the dimensions of the room before buying a sofa of that ___.",
                definition: "The magnitude or dimensions of an object; how large or small something is.",
            },
            {
                word: "not worth it",
                context: "not important or beneficial enough to justify the time or effort",
                explanation: "Something that is too expensive, time-consuming, or difficult for the benefit you will receive.",
                example: "Spending an hour in traffic for a five-minute meeting is simply not worth it.",
                writingSentence: "The repair costs are so high that fixing the old car is ___ anymore.",
                pronSentence: "After weighing the pros and cons, they decided the risk was ___.",
                definition: "Used to describe something that does not justify the time, effort, or cost required.",
            },
            {
                word: "meal",
                context: "an occasion when food is eaten",
                explanation: "An occasion when food is eaten, typically at a fixed time.",
                example: "Dinner is usually the biggest meal of the day for our family.",
                writingSentence: "We sat down together for a delicious Sunday ___ prepared by my grandmother.",
                pronSentence: "He skipped his last ___ because he was too busy working.",
                definition: "An occasion or a specific time when food is eaten, such as breakfast or dinner.",
            },
            {
                word: "keep an eye on",
                context: "to watch or monitor carefully",
                explanation: "To watch or observe someone or something carefully and continuously.",
                example: "Could you keep an eye on my luggage while I go to the restroom?",
                writingSentence: "The supervisor asked the security guard to ___ the entrance at all times.",
                pronSentence: "Please ___ the baby while I quickly jump on a work call.",
                definition: "To carefully monitor, watch, or supervise someone or something.",
            },
            {
                word: "earthquake",
                context: "a sudden violent shaking of the ground",
                explanation: "A sudden and violent shaking of the ground, sometimes causing great destruction, as a result of movements within the earth's crust.",
                example: "The region experienced a major earthquake last year, causing widespread damage.",
                writingSentence: "The tremor felt like a minor ___, but fortunately, no one was injured.",
                pronSentence: "Scientists use seismographs to measure the force of an ___.",
                definition: "A sudden, violent shaking of the ground resulting from movements in the Earth's crust.",
            },
            {
                word: "shutters",
                context: "movable cover for a window",
                explanation: "Movable covers, usually hinged, that are placed on the outside of a window to protect it or to control the amount of light entering.",
                example: "She closed the wooden shutters to block out the morning sun.",
                writingSentence: "In the summer, we keep the window ___ closed to keep the house cool.",
                pronSentence: "The old house had beautiful, dark-green ___ on every window.",
                definition: "Hinged covers placed on the exterior of a window, often made of wood or metal.",
            }
        ];

        let totalVocabulary = vocabData.length;
        let totalPossibleScore = totalVocabulary * 3;
        let currentScore = 0;
        let writingCorrectCount = 0;
        let matchingCorrectCount = 0;
        let pronCorrectCount = 0;

        let selectedWordMatch = null;
        let selectedDefinitionMatch = null;
        const matchingAnswers = {}; // wordId -> definitionId

        const pronResults = {}; // word -> true/false

        const recognitionFallback = ('webkitSpeechRecognition' in window || 'SpeechRecognition' in window);

        // --- UTILITY FUNCTIONS ---
        function shuffleArray(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
            return array;
        }

        function updateScore() {
            currentScore = writingCorrectCount + matchingCorrectCount + pronCorrectCount;
            document.getElementById('score-display').innerText = `Score: ${currentScore} / ${totalPossibleScore}`;
        }

        function showSection(id, button) {
            document.querySelectorAll('.section').forEach(section => {
                section.classList.remove('active');
            });
            document.getElementById(id).classList.add('active');

            document.querySelectorAll('.nav-buttons button').forEach(btn => {
                btn.classList.remove('active');
            });
            button.classList.add('active');
        }

        // --- 1. VOCABULARY LIST ---
        function generateVocabList() {
            const container = document.getElementById('vocab-items-container');
            container.innerHTML = '';
            vocabData.forEach(item => {
                const div = document.createElement('div');
                div.className = 'vocab-item';
                div.innerHTML = `
                    <div class="vocab-word-details">
                        <span class="word">${item.word}</span> <span class="context">(${item.context})</span>
                        <p class="explanation"><strong>Meaning:</strong> ${item.explanation}</p>
                        <p class="example"><strong>Example:</strong> <em>"${item.example}"</em></p>
                    </div>
                    <button class="speak-button" onclick="speak('${item.word}')">▶️ Hear</button>
                `;
                container.appendChild(div);
            });
        }

        function speak(text) {
            if ('speechSynthesis' in window) {
                const u = new SpeechSynthesisUtterance(text);
                u.lang = "en-US";
                speechSynthesis.speak(u);
            } else {
                alert("Speech synthesis not supported in your browser.");
            }
        }


        // --- 2. FILL IN THE GAPS (WRITING) ---
        function generateWritingGaps() {
            const container = document.getElementById('writing-sentences-container');
            const bank = document.getElementById('writing-word-bank');
            container.innerHTML = '';
            bank.innerHTML = '';

            // Generate Word Bank
            shuffleArray([...vocabData]).forEach(item => {
                const span = document.createElement('span');
                span.innerText = item.word;
                bank.appendChild(span);
            });

            // Generate Sentences (Shuffled)
            shuffleArray([...vocabData]).forEach((item, index) => {
                const sentence = item.writingSentence;
                const expectedWord = item.word;
                const sentenceHTML = sentence.replace('___', `<input type="text" data-expected="${expectedWord}" id="write-gap-${index}">`);

                const div = document.createElement('div');
                div.className = 'gap-sentence';
                div.innerHTML = `
                    <p>${sentenceHTML}<span id="write-feedback-${index}" class="feedback"></span></p>
                `;
                container.appendChild(div);
            });
        }

        function checkWritingGaps() {
            let correctCount = 0;
            document.querySelectorAll('#writing-sentences-container input').forEach((input, index) => {
                const expected = input.getAttribute('data-expected').toLowerCase().trim();
                const actual = input.value.toLowerCase().trim();
                const feedbackSpan = document.getElementById(`write-feedback-${index}`);

                if (input.disabled) {
                    if (actual === expected) correctCount++;
                    return; // Already checked and correct, don't re-evaluate
                }

                if (actual === expected) {
                    feedbackSpan.innerHTML = '✔️ Correct!';
                    feedbackSpan.style.color = varToHex('--correct-color');
                    input.style.borderColor = varToHex('--correct-color');
                    input.disabled = true;
                    correctCount++;
                } else {
                    feedbackSpan.innerHTML = '❌ Try again.';
                    feedbackSpan.style.color = varToHex('--incorrect-color');
                    input.style.borderColor = varToHex('--incorrect-color');
                }
            });

            writingCorrectCount = correctCount;
            updateScore();
        }

        function resetWritingGaps() {
            document.querySelectorAll('#writing-sentences-container input').forEach((input, index) => {
                input.value = '';
                input.style.borderColor = varToHex('--secondary-color');
                input.disabled = false;
                document.getElementById(`write-feedback-${index}`).innerHTML = '';
            });
            writingCorrectCount = 0;
            updateScore();
        }

        // --- 3. MATCH DEFINITIONS ---
        function generateMatchDefs() {
            const wordsContainer = document.getElementById('match-words-container');
            const defsContainer = document.getElementById('match-definitions-container');
            wordsContainer.innerHTML = '';
            defsContainer.innerHTML = '';
            selectedWordMatch = null;
            selectedDefinitionMatch = null;
            matchingCorrectCount = 0;
            updateScore();

            const words = shuffleArray(vocabData.map((item, index) => ({ id: `word-${index}`, text: item.word, answer: `def-${index}` })));
            const definitions = shuffleArray(vocabData.map((item, index) => ({ id: `def-${index}`, text: item.definition, answer: `word-${index}` })));

            words.forEach(item => {
                const div = document.createElement('div');
                div.className = 'match-item match-word';
                div.id = item.id;
                div.setAttribute('data-answer', item.answer);
                div.setAttribute('onclick', 'selectMatchItem(this, "word")');
                div.innerText = item.text;
                wordsContainer.appendChild(div);
            });

            definitions.forEach(item => {
                const div = document.createElement('div');
                div.className = 'match-item match-definition';
                div.id = item.id;
                div.setAttribute('data-answer', item.answer);
                div.setAttribute('onclick', 'selectMatchItem(this, "definition")');
                div.innerText = item.text;
                defsContainer.appendChild(div);
            });
        }

        function selectMatchItem(element, type) {
            if (element.classList.contains('match-correct')) return;

            // Clear previous selection of the same type
            document.querySelectorAll(`.match-${type}`).forEach(item => item.classList.remove('match-selected', 'match-incorrect'));

            element.classList.add('match-selected');

            if (type === 'word') {
                selectedWordMatch = element;
            } else {
                selectedDefinitionMatch = element;
            }

            if (selectedWordMatch && selectedDefinitionMatch) {
                checkMatch();
            }
        }

        function checkMatch() {
            const word = selectedWordMatch;
            const definition = selectedDefinitionMatch;

            if (word.getAttribute('data-answer') === definition.id) {
                // Correct Match
                word.classList.add('match-correct');
                definition.classList.add('match-correct');
                matchingCorrectCount++;
                updateScore();
            } else {
                // Incorrect Match
                word.classList.add('match-incorrect');
                definition.classList.add('match-incorrect');
                setTimeout(() => {
                    word.classList.remove('match-incorrect');
                    definition.classList.remove('match-incorrect');
                }, 800);
            }

            // Clear selections
            selectedWordMatch = null;
            selectedDefinitionMatch = null;
            setTimeout(() => {
                document.querySelectorAll('.match-item').forEach(item => item.classList.remove('match-selected'));
            }, 500);
        }

        // --- 4. FILL IN THE GAPS (PRONUNCIATION) ---
        function generatePronunciationGaps() {
            const container = document.getElementById('pron-sentences-container');
            const bank = document.getElementById('pron-word-bank');
            container.innerHTML = '';
            bank.innerHTML = '';
            pronCorrectCount = 0;
            updateScore();
            Object.keys(pronResults).forEach(key => pronResults[key] = false); // Reset results

            // Generate Word Bank
            shuffleArray([...vocabData]).forEach(item => {
                const span = document.createElement('span');
                span.innerText = item.word;
                bank.appendChild(span);
            });

            // Generate Sentences (Shuffled)
            shuffleArray([...vocabData]).forEach((item, index) => {
                const sentence = item.pronSentence;
                const expectedWord = item.word;
                const blankPlaceholder = `<span class="pron-blank" id="pron-gap-${index}">?</span>`;
                const sentenceHTML = sentence.replace('___', blankPlaceholder);

                const div = document.createElement('div');
                div.className = 'pron-sentence';
                div.innerHTML = `
                    <p>
                        ${sentenceHTML}
                    </p>
                    <button class="mic-button" data-expected="${expectedWord}" data-index="${index}" onclick="startSpeechRecognition(this)">🎙️</button>
                    <span id="pron-feedback-${index}" class="pron-feedback"></span>
                `;
                container.appendChild(div);
                pronResults[expectedWord] = false;
            });

            if (!recognitionFallback) {
                alert("Speech Recognition is not fully supported in this browser. This exercise may not work.");
            }
        }

        let recognition = null;
        let isListening = false;
        let currentMicButton = null;

        function startSpeechRecognition(button) {
            if (!recognitionFallback) {
                alert("Speech Recognition not supported in your browser.");
                return;
            }

            if (isListening) {
                // If already listening, stop the current session
                if (recognition) recognition.stop();
                return;
            }

            const expectedWord = button.getAttribute('data-expected');
            const index = button.getAttribute('data-index');
            const gapElement = document.getElementById(`pron-gap-${index}`);
            const feedbackElement = document.getElementById(`pron-feedback-${index}`);

            // If already correct, do nothing
            if (pronResults[expectedWord]) return;

            // Reset UI for new attempt
            gapElement.innerText = '?';
            gapElement.classList.remove('pron-correct');
            feedbackElement.innerText = '';
            
            // Highlight button
            currentMicButton = button;
            currentMicButton.classList.add('mic-listening');
            isListening = true;

            const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
            recognition = new SpeechRecognition();
            recognition.continuous = false;
            recognition.interimResults = false;
            recognition.lang = 'en-US';

            recognition.onresult = (event) => {
                const transcript = event.results[0][0].transcript.toLowerCase().trim();
                const cleanTranscript = transcript.replace(/\s/g, ''); // For multi-word answers, remove spaces for comparison
                const cleanExpected = expectedWord.toLowerCase().trim().replace(/\s/g, '');

                if (cleanTranscript === cleanExpected) {
                    if (!pronResults[expectedWord]) {
                        pronResults[expectedWord] = true;
                        pronCorrectCount++;
                        updateScore();
                    }
                    gapElement.innerText = expectedWord;
                    gapElement.classList.add('pron-correct');
                    feedbackElement.innerText = '✅ Success!';
                    feedbackElement.style.color = varToHex('--correct-color');
                } else {
                    feedbackElement.innerText = `❌ Heard: "${transcript}". Try again.`;
                    feedbackElement.style.color = varToHex('--incorrect-color');
                }
            };

            recognition.onerror = (event) => {
                console.error('Speech recognition error:', event.error);
                feedbackElement.innerText = `⚠️ Error: ${event.error}.`;
                feedbackElement.style.color = '#FF9800';
                stopListeningUI();
            };

            recognition.onend = () => {
                stopListeningUI();
            };

            recognition.start();
            feedbackElement.innerText = '...Listening...';
            feedbackElement.style.color = varToHex('--primary-color');
        }

        function stopListeningUI() {
            if (currentMicButton) {
                currentMicButton.classList.remove('mic-listening');
            }
            isListening = false;
            currentMicButton = null;
        }

        // Helper to get CSS variable color (for dynamic styling)
        function varToHex(variable) {
            return getComputedStyle(document.documentElement).getPropertyValue(variable).trim();
        }

        // --- INITIALIZATION ---
        document.addEventListener('DOMContentLoaded', () => {
            generateVocabList();
            generateWritingGaps();
            generateMatchDefs();
            generatePronunciationGaps();
            updateScore();
            showSection('vocab-list', document.querySelector('.nav-buttons button:first-child'));
        });
    </script>
</body>
</html>
