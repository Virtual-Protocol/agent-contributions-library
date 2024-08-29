<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

<h1>Audio Core Contribution Guide</h1>

<p>Welcome to the Virtual Protocol Audio Core project! This repository is dedicated to the development and fine-tuning of TTS (Text-to-Speech) voice models. Please follow this guide to contribute effectively.</p>

<h2>Table of Contents</h2>
<ul>
    <li><a href="#prerequisites">Prerequisites</a></li>
    <li><a href="#getting-started">Getting Started</a></li>
    <li><a href="#data-collection">Data Collection</a></li>
    <li><a href="#data-processing">Data Processing</a></li>
    <li><a href="#finetuning-with-gpt-sovits">Finetuning with GPT-SoVITS</a></li>
    <li><a href="#contribution">Contribution</a></li>
    <li><a href="#common-issues">Common Issues</a></li>
    <li><a href="#support">Support</a></li>
</ul>

<h2 id="prerequisites">Prerequisites</h2>
<p>Before you begin, ensure you have met the following requirements:</p>
<ul>
    <li>A Windows, MacOS, or Linux machine with the latest updates.</li>
    <li>Python 3.x installed on your machine.</li>
    <li>Basic knowledge of Git and GitHub.</li>
    <li>A Discord account for communication and support.</li>
</ul>

<h2 id="getting-started">Getting Started</h2>
<p>Clone the repository to your local machine:</p>
<pre><code>git clone https://github.com/your-repository/audio-core.git
cd audio-core
</code></pre>

<p>Install the necessary dependencies:</p>
<pre><code>pip install -r requirements.txt
</code></pre>

<h2 id="data-collection">Data Collection</h2>
<ol>
    <li>
        <strong>Select Video from YouTube:</strong>
        <ul>
            <li>Avoid videos with heavy background noise.</li>
            <li>Prefer interviews or podcasts with clear audio.</li>
        </ul>
    </li>
    <li>
        <strong>Download Video:</strong>
        <ul>
            <li>Use any YouTube downloader, such as <a href="https://en.savefrom.net/1-youtube-video-downloader-586Wb/">SaveFrom</a>.</li>
        </ul>
    </li>
</ol>

<h2 id="data-processing">Data Processing</h2>
<ol>
    <li>
        <strong>Denoise Audio:</strong>
        <ul>
            <li>Download and install <a href="https://ultimatevocalremover.com/">UVR5</a>.</li>
            <li>Use the MDX-Net model for denoising.</li>
        </ul>
    </li>
    <li>
        <strong>Speaker Diarization:</strong>
        <ul>
            <li>Use <a href="https://huggingface.co/spaces/jessica07/Playground-Deepgram">Deepgram</a> for speaker diarization.</li>
        </ul>
    </li>
</ol>

<h2 id="finetuning-with-gpt-sovits">Finetuning with GPT-SoVITS</h2>

<h3>Local Installation (Windows)</h3>
<ol>
    <li>Download the zipped package from the <a href="https://github.com/RVC-Boss/GPT-SoVITS">repository</a>.</li>
    <li>Run <code>go-webui.bat</code> to start the tool.</li>
</ol>

<h3>Google Colab Setup</h3>
<ol>
    <li>Open the <a href="https://colab.research.google.com/github/RVC-Boss/GPT-SoVITS/blob/main/colab_webui.ipynb">Colab Notebook</a>.</li>
    <li>Run all cells to start the service.</li>
</ol>

<h3>Working with GPT-SoVITS</h3>
<ol>
    <li>Upload your cleaned and sliced audio data.</li>
    <li>Use the tool's interface to start the training and inference process.</li>
</ol>

<h2 id="contribution">Contribution</h2>
<ol>
    <li>
        <strong>Structure Your Submission:</strong>
        <ul>
            <li>Follow the guide <a href="https://whitepaper.virtuals.io/technical-documentation/modular-consensus-framework/contribution/voice-core/contribute-to-voice-core#improvement-on-the-tts-model">here</a>.</li>
        </ul>
    </li>
    <li>
        <strong>Submit Your Contribution:</strong>
        <ul>
            <li>Follow the step-by-step <a href="https://whitepaper.virtuals.io/how-to-guides/submit-a-contribution#submitting-your-contribution">guide</a> to upload your files.</li>
        </ul>
    </li>
    <li>
        <strong>Notify the Community:</strong>
        <ul>
            <li>Announce your contribution in the <code>#contributor-chat</code> on <a href="https://discord.gg/virtualsio">Discord</a>.</li>
        </ul>
    </li>
</ol>

<h2 id="common-issues">Common Issues</h2>
<ul>
    <li><strong>Out of Memory Errors:</strong> Reduce batch size during training to prevent memory errors.</li>
    <li><strong>Installation Issues:</strong> Ensure all dependencies are installed correctly. Check for Python version compatibility.</li>
    <li><strong>Audio Quality Problems:</strong> Revisit the data processing steps to ensure high-quality input.</li>
</ul>

<h2 id="support">Support</h2>
<p>If you encounter any issues, feel free to ask in the <code>#contributor-chat</code> on <a href="https://discord.gg/virtualsio">Discord</a>.</p>

</body>
</html>
