<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Prompt Recorder</title>
  <style>
    body { font-family: Arial, sans-serif; text-align: center; margin-top: 30px; }
    #logo {
      display: block;
      margin: 0 auto 40px;
      width: 480px;
      max-width: 100%;
      margin-bottom: 60px;
    }
    #prompt {
      font-size: 24px;
      margin: 0 auto 20px;
      max-width: 480px;
      text-align: left;
      word-break: break-word;
      overflow-wrap: break-word;
      line-height: 1.4;
    }
    #videoPreview {
      width: 480px;
      height: 360px;
      margin: 20px auto;
      border: 2px solid #ccc;
      display: block;
    }
    #downloadLink, #stopButton {
      margin-top: 20px;
      display: none;
    }
    button {
      padding: 10px 20px;
      font-size: 16px;
      margin-top: 20px;
    }
    #startButton {
      margin-bottom: 80px;
    }
  </style>
</head>
<body>
  <img src="images/logo.png" alt="Your Logo" id="logo" />

  <button id="startButton" onclick="startApp()">Start Prompt</button>
  <button id="resetButton" onclick="resetApp()">Reset for Testing</button>

  <div id="prompt">Get ready...</div>

  <video id="videoPreview" autoplay muted playsinline></video>
  <p id="status">Preparing to record...</p>
  <button id="stopButton">Stop Recording</button>
  <br />
  <a id="downloadLink" href="#" download="recording.webm">Download your recording</a>
  <p id="recordingCountdown"></p>

  <script>
const prompts = [
  {
    text: "How do you anticipate graduate studies being more challenging than undergraduate studies? What skills have you developed that have prepared you to deal with these challenges?",
    audio: "audio/prompt1.mp3"
  },
  {
    text: "You anticipate needing to have a “crucial conversation” about a group project for which one member is not actively engaged, during which a disagreement is likely. How do you prepare for this conversation? How do you keep the conversation on track and productive, especially when there is a moderate level of disagreement?",
    audio: "audio/prompt2.mp3"
  },
  {
    text: "Consider an experience that has impacted where you are in your life today. Why was it so impactful and how does it influence the way you will approach the graduate program in speech language pathology?",
    audio: "audio/prompt3.mp3"
  },
  {
    text: "Imagine that you are a student clinician working under the supervision of a licensed Speech-Language Pathologist. You are spending a week at a local Head Start program to provide language screenings. The students' classroom teachers ask you to recommend some materials they can send home to families about reading to their children. You ask your clinical supervisor for guidance when putting together the materials. Your supervisor tells you that the student's parents do not need information about reading together because 'many of these families don't bother reading books to their children anyway.' Explain what you would say and/or do, and how your response might be informed by your background?",
    audio: "audio/prompt4.mp3"
  },
  {
    text: "In the SLP Program, you’ll be part of a community; a classroom community, a university community, and the community where you live. How do you see yourself contributing to community?",
    audio: "audio/prompt5.mp3"
  },
  {
    text: "Both short- and long-term goals are necessary to achieve growth. Tell us about one of your long-term goals and explain some of the intermediate steps that you think will be necessary to get there.",
    audio: "audio/prompt6.mp3"
  },
  {
    text: "Describe something you learned outside of the field of communication disorders and how you think it can inform your future practice as a speech-language pathologist.",
    audio: "audio/prompt7.mp3"
  },
  {
    text: "SLP professionals need to use resources to be successful. Our graduate program uses a cohort model to help you understand how others can be resources to your development. When working in community with your classmates, describe ways you will use your strengths to support the cohort. Additionally, describe ways you anticipate needing to rely on your cohort for support.",
    audio: "audio/prompt8.mp3"
  }
];


    const MAX_RECORDINGS = 3;
    const RECORDING_DURATION = 60000;
    const COUNTDOWN_SECONDS = 15;

    let recordingCount = 0;
    let mediaRecorder, mediaStream, recordingTimeout, countdownInterval;
    let chunks = [];

    const promptDisplay = document.getElementById('prompt');
    const videoPreview = document.getElementById('videoPreview');
    const statusDisplay = document.getElementById('status');
    const downloadLink = document.getElementById('downloadLink');
    const stopButton = document.getElementById('stopButton');

    function disableStartButton() {
      const startButton = document.getElementById('startButton');
      startButton.disabled = true;
      startButton.style.opacity = 0.5;
      startButton.style.cursor = 'not-allowed';
      statusDisplay.textContent = "Recording limit reached.";
    }

    function startApp() {
      if (recordingCount >= MAX_RECORDINGS) {
        alert("You’ve reached the maximum number of recordings.");
        disableStartButton();
        return;
      }

      const selectedPrompt = prompts[Math.floor(Math.random() * prompts.length)];
      promptDisplay.textContent = selectedPrompt.text;

      const audio = new Audio(selectedPrompt.audio);
      audio.play();

      audio.onended = () => startCountdown(COUNTDOWN_SECONDS);
    }

    function resetApp() {
      recordingCount = 0;
      document.getElementById('startButton').disabled = false;
      document.getElementById('startButton').style.opacity = 1;
      document.getElementById('startButton').style.cursor = 'pointer';

      downloadLink.style.display = 'none';
      stopButton.style.display = 'none';
      promptDisplay.textContent = "Get ready...";
      statusDisplay.textContent = "Preparing to record...";
    }

    function startCountdown(seconds) {
      if (seconds > 0) {
        statusDisplay.textContent = `Recording starts in ${seconds}...`;
        setTimeout(() => startCountdown(seconds - 1), 1000);
      } else {
        startRecording();
      }
    }

    function startRecording() {
      navigator.mediaDevices.getUserMedia({ video: true, audio: true }).then(stream => {
        mediaStream = stream;
        videoPreview.srcObject = stream;

        const isSafari = /^((?!chrome|android).)*safari/i.test(navigator.userAgent);
        const possibleTypes = isSafari
          ? ['video/quicktime']
          : [
              'video/webm;codecs=vp9,opus',
              'video/webm;codecs=vp8,opus',
              'video/mp4;codecs=avc1',
              'video/quicktime'
            ];

        let selectedType = possibleTypes.find(type => MediaRecorder.isTypeSupported(type));
        const options = selectedType ? { mimeType: selectedType } : undefined;

        try {
          mediaRecorder = new MediaRecorder(stream, options);
        } catch (e) {
          console.error("Failed to initialize MediaRecorder:", e);
          statusDisplay.textContent = "Recording not supported in this browser.";
          return;
        }

        chunks = [];
        mediaRecorder.ondataavailable = e => chunks.push(e.data);
        mediaRecorder.onstop = () => {
          const blob = new Blob(chunks, { type: selectedType || 'video/webm' });
          const url = URL.createObjectURL(blob);
          downloadLink.href = url;

          if (selectedType && selectedType.includes('mp4')) {
            downloadLink.download = 'recording.mp4';
          } else if (selectedType && selectedType.includes('quicktime')) {
            downloadLink.download = 'recording.mov';
          } else {
            downloadLink.download = 'recording.webm';
          }

          downloadLink.style.display = 'inline';
          stopButton.style.display = 'none';
          stream.getTracks().forEach(track => track.stop());
          statusDisplay.textContent = "Recording finished!";
          document.getElementById('recordingCountdown').textContent = "";
        };

        mediaRecorder.start();
        statusDisplay.textContent = "Recording started...";
        recordingCount++;

        if (recordingCount >= MAX_RECORDINGS) disableStartButton();
        stopButton.style.display = 'inline';

        let secondsLeft = RECORDING_DURATION / 1000;
        const countdownDisplay = document.getElementById('recordingCountdown');
        countdownDisplay.textContent = `Recording ends in ${secondsLeft} seconds`;

        if (countdownInterval) clearInterval(countdownInterval);
        countdownInterval = setInterval(() => {
          secondsLeft--;
          countdownDisplay.textContent = `Recording ends in ${secondsLeft} seconds`;
        }, 1000);

        recordingTimeout = setTimeout(() => {
          stopRecording();
          clearInterval(countdownInterval);
        }, RECORDING_DURATION);
      }).catch(error => {
        statusDisplay.textContent = "Camera or mic access was denied.";
        console.error(error);
      });
    }

    function stopRecording() {
      if (mediaRecorder && mediaRecorder.state === "recording") {
        mediaRecorder.stop();
        clearTimeout(recordingTimeout);
        const countdownDisplay = document.getElementById('recordingCountdown');
        countdownDisplay.textContent = "";
        if (countdownInterval) {
          clearInterval(countdownInterval);
          countdownInterval = null;
        }
      }
    }

    stopButton.addEventListener('click', stopRecording);
  </script>
</body>
</html>
