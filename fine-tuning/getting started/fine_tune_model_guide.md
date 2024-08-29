<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">


<h1>Beginner Guide to Finetune Model</h1>

<p>Hello everyone! Welcome to Virtual Protocol (VP). You are here today because you have been invited to be the contributors on our platform. Currently, the characters on Virtual Protocol have 3 cores: the <strong>Cognitive Core</strong>, <strong>Audio Core</strong>, and <strong>Visual Core</strong>. Today, we will be focusing only on the Cognitive Core, which is largely made up of LLM datasets and models.</p>

<p>You, being the contributor on VP, means you will be <strong>uploading datasets or LLM models</strong> onto our platform. This process itself can be intellectually stimulating in LLM terms because you will experience the full end-to-end process from collecting datasets, pre-processing datasets, and finally fine-tuning to a functional model.</p>

<p>Do note this guide is an instructional guide to get you started. I will not include much on how LLM works and why we use certain steps. There are a lot of conceptual learning materials that can be found <a href="https://github.com/mlabonne/llm-course">here</a>.</p>

<h2>Let’s get started!</h2>

<p>(Remember, this is an instructional guide. If you wish to learn more in-depth, feel free to ask in the Discord channel.)</p>

<h3>Llama Factory: WebUI for Finetuning</h3>
<ol>
    <li>Download the model from <a href="https://github.com/hiyouga/LLaMA-Factory">https://github.com/hiyouga/LLaMA-Factory</a>.</li>
    <li>Have a quick read, then choose the Colab service. Link: <a href="https://colab.research.google.com/drive/1eRTPn37ltBbYsISy9Aw2NuI2Aq5CQrD9?usp=sharing">Colab Notebook</a>.</li>
    <li>In Google Colab, connect to the free runtime T4.</li>
    <li>Run “<strong>Install Dependencies</strong>”.</li>
    <li>Skip “<strong>Log in with Hugging Face account</strong>” first. You will need your Huggingface token if you want to upload your model.</li>
    <li>Head to the section “<strong>Fine-tune model via LLaMA Board</strong>,” change the code from <code>create_ui().queue().launch(share=True)</code> → <code>create_ui().queue().launch(share=True, debug=True)</code>. Adding <code>debug=True</code> helps in future troubleshooting.</li>
    <li>Click Run and wait for it to complete.</li>
    <li>Click the public URL that looks like <code>https://xxxxxxxxxxxx.gradio.live/</code>.</li>
    <li>Now you should see a WebUI in a new tab.</li>
    <li>To ensure things work properly, we can start with basic settings.</li>
    <li>Go to <strong>Model name</strong>, select “<em>LLaMA2-7B</em>”.</li>
    <li>Go to <strong>Finetuning method</strong>, select “<em>lora</em>”.</li>
    <li>Go to <strong>Dataset</strong>, select “<em>alpaca_gpt4_en</em>”.</li>
    <li>The settings below are meant to increase the training speed in this trial run. Please keep default when you are doing the actual run.
        <ul>
            <li><strong>Learning rate:</strong> 2e-4</li>
            <li><strong>Epoch:</strong> 2.0</li>
            <li><strong>Max samples:</strong> 1000</li>
            <li><strong>Gradient accumulation:</strong> 4</li>
        </ul>
    </li>
    <li>Go to <strong>Output dir</strong>, type “<em>my-test-01</em>”.</li>
    <li>Click <strong>Start</strong>, and your training should begin. For this trial, it can take up to 1 hour to complete.</li>
    <li>To try out your model, click the <strong>Refresh adapters</strong> button, and select the directory “<em>my-test-01</em>”.</li>
    <li>Head to the <em>Chat</em> tab, click <strong>Load model</strong> and chat with your trained model.</li>
    <li>Now go back to Google Colab and STOP the cell that is running this Gradio.</li>
    <li>Go to the section <strong>Merge LoRA weights</strong>, replace the <em>model_name_or_path, adapter_name_or_path, template, export_dir</em>, and <em>export_hub_model_id</em> with your path.</li>
    <li>Your merged weight should be uploaded to your Huggingface account.</li>
    <li>Go to this Google Colab and we want to quantize our model. <a href="https://colab.research.google.com/drive/1P646NEg33BZy4BfLDNpTz0V0lwIU3CHu?usp=sharing">Link to Colab</a>.</li>
    <li>Replace <code>MODEL_ID</code> with your Huggingface model ID.</li>
    <li>Set <strong>QUANTIZATION_METHODS</strong> as <em>q4_k_m, q8_0</em>.</li>
    <li>Put your Huggingface username and token.</li>
    <li>Click Run at the Google Colab cell and wait for the quantization to complete.</li>
</ol>

<p><strong>Congratulations!</strong> Now you are done with the full workflow from finetuning to GGUF. Now, you can repeat the steps above, but with your own dataset.</p>

<aside>
    😖 Get stuck? Ask away in our <a href="https://discord.gg/virtualsio">#contributors-chats</a> channel!
</aside>

<h2>How to collect your own dataset?</h2>

<p>Choose a character that is available on Virtual Protocol, or assigned by the admin. I do not have the step-by-step guide on how to collect datasets due to the variety of datasets available out there. You can discuss with fellow contributors in our Discord channel. However, these are the data sources that I would recommend to start with:</p>

<ul>
    <li>Wikipedia, fandom, Wikia, articles</li>
    <li>Interviews, podcasts, audiobooks</li>
    <li>Movie dialogue, lyrics</li>
</ul>

<aside>
    💡 Learn how to scrape web data <a href="https://www.notion.so/Beginner-s-Guide-to-Web-Scraping-with-Python-fe44ff340e1e4451956e7b2b10d35ee3?pvs=21">here</a>.
</aside>

<p>Please refer to this link on how to format your dataset: <a href="https://github.com/hiyouga/LLaMA-Factory/tree/main/data">https://github.com/hiyouga/LLaMA-Factory/tree/main/data</a> into Alpaca format.</p>

<p>This is a sample of <em>dataset_info.json</em>:</p>
<pre><code>{
  "dataset_name": {
    "file_name": "my_collected_dataset.json",
    "subset": "None",
    "folder": "None",
    "ranking": "false",
    "formatting": "alpaca",
    "columns (optional)": {
      "prompt": "instruction",
      "query": "input",
      "response": "output",
      "system": "system"
    }
  }
}
</code></pre>

<p>This is how your dataset structure will look like. <a href="https://github.com/hiyouga/LLaMA-Factory/blob/main/data/alpaca_data_en_52k.json">Source</a></p>
<img src="https://prod-files-secure.s3.us-west-2.amazonaws.com/12f7bb5a-d953-4ff0-8718-ebe6b3499c01/d0d6595e-15d6-468d-8c95-4f63183a84e5/Untitled.png" alt="Dataset Structure">

<h3>I have finished merging my LoRA with the base model and quantized it to GGUF, what’s next?</h3>

<p>Congratulations on coming this far! So now you need to learn how to navigate Virtual Protocol. This guide is valid as of 20th March 2024. New UI/UX might be added to Virtual Protocol, and we will try to keep the guide updated.</p>

<ol>
    <li>Visit our whitepaper to learn how to contribute: <a href="https://whitepaper.virtuals.io/how-to-guides/submit-a-contribution">https://whitepaper.virtuals.io/how-to-guides/submit-a-contribution</a>.</li>
    <li>Join our Discord server to chat with fellow contributors: <a href="https://discord.gg/virtualsio">https://discord.gg/virtualsio</a>.</li>
    <li>Watch our YouTube tutorial series for a step-by-step guide: <a href="https://www.youtube.com/virtualsio">https://www.youtube.com/virtualsio</a>.</li>
    <li>Have your merged LoRA with GGUF ready to be uploaded on <a href="https://portal.virtuals.io">Virtual Protocol portal</a>.</li>
    <li>Fill in the required metadata for your submission. The admin will check and approve the submission. Do note that this will take up to 3 working days.</li>
    <li>After your submission is approved, you will receive a confirmation email, and your character will be updated with the latest cognitive core.</li>
</ol>

<p><strong>Woohoo!</strong> You have successfully contributed to Virtual Protocol. Your character now will have a unique cognitive core, with the finest dataset and parameters made by you!</p>

<p>Have fun, and thank you for contributing to Virtual Protocol. This is just the beginning, and we’re so excited to see what you create!</p>

</body>
</html>
