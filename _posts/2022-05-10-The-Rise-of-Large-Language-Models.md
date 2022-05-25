## The Rise of Large Language Models

The rapid development of new language models within the NLP branch of AI since 2019 has brought about much improved capabilities concerning scope and accuracy. The media hype surrounding OpenAI's GPT-X series of models hasn't gone unnoticed probably [1][2]. These improvements have been mainly brought about by switching to the now ubiquitous transformer architecture and scaling the models to humongous sizes. The last model from OpenAI GPT-3 comes with 750 billion parameters trained on 570 GB of data.

These parameters incur substantial compute costs in training. As a rough estimate one can take as compute resource an NVIDIA V100 GPU with 7 TFLOPs and the estimate for compute effort from the GTP-3 paper [3] (page 46) stating compute cost of 3.14E+23 Flops for the largest model. This means an equivalent of 1E7 hours of NVIDIA V100 GPU time. Estimating cost of GPU time with roughly 1 USD per hour the total compute cost for the largest model for one complete training comes in at 10 million USD.[4] Naturally there are additional costs for parameter variation and additional training, storage, commodity costs for hardware etc. not to speak of staff. These are staggering numbers.

Looking at the development of model size over time one can see an exponential increase over the last few years seeing an order of magnitude increase year over year.

![Size of language models over time](assets/nlp_models_sizes_over_time.png)

The next model of OpenAI GPT-4 is rumored to come in at 100 trillion parameters (100 x 10E12). It's a bit unscientific but informative to compare this with the number of neurons in the human brain, which features approximately 100 billion neurons (100 x 10E9), that's a thousand times less[7].

Now one can ask if all this is necessary. Currently the common logic is going further by scaling models supported by studies which clearly link size of model to it's capabilities and claim universal scaling laws for this behavior [8]. According to the referenced paper by Kaplan et al. the model loss is reduced by one unit if the model is scaled by one order of magnitude (a factor of 10). But to make this happen compute effort in training and dataset size have to be scaled also [8][9].

Besides cost there is obviously an accompanied enormous carbon footprint which has been discussed with AI training in general but has to be considered for scaling these models especially. The economic consequences of these trends leads to a monopolization of model providers. This can be felt already with the large models only available as commercial offerings through their creators [11] whereas prior smaller models are freely available through direct code download from research sites but more importantly specialised startups offering model repositories cleaned up and embedded in frameworkds ready for production [10].

If at the end of the day only super large AI companies like Google through OpenAI, Microsoft through Deepmind and Alibaba remain to commercialize this technology the consequences could be grave for the economy at large. The capabilities of the large models are already impressive and lead to a foreseeable future where every company is in need to use them to automate many standard tasks, from classification, summarization, generation of standard texts etc. Another problem lies in the fact that these few companies bring an unavoidable bias not only in the standard language they rely on but also in a subtler way through their cultures they are embedded in. Communities or whole nations relying on different languages and cultures will inevitably trail behind in using these technologies.

It remains to be seen if the trend persists and how the world will respond to it.

References
[1] GPT-2 <https://openai.com/blog/better-language-models/>

[2] GPT-3 <https://openai.com/blog/gpt-3-apps/>

[3] GPT-3 official paper on arxiv: <https://arxiv.org/abs/2005.14165>

[4] Estimate of compute cost: s. Abschnitt D in [3](page 46), compute cost per GPU e.g. Google Cloud approximately 1USD/hour for NVIDIA V100, spec V100 => 7 TFLOPs = 7 10^12 / s, 3.14 10^23 Flops => 3.14 10^23/7x10^12 / 3600 = 10^7 hours => 10 Mio USD, s. details  <https://github.com/ug3p141/nlp_models>

[6] to compare with published data: <https://arxiv.org/abs/2201.11990> (page 2)

[7] Number of neurons in brain: <https://www.pnas.org/doi/10.1073/pnas.1201895109>

[8] Scaling laws for language models: <https://arxiv.org/abs/2001.08361>

[9] Trying to find out how to scale model, dataset and compute: <https://www.deepmind.com/publications/an-empirical-analysis-of-compute-optimal-large-language-model-training>

[10] Free model repository: <https://huggingface.co/models>

[11] Pricing OpenAI <https://openai.com/api/pricing/>
