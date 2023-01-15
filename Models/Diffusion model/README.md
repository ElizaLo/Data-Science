# Diffusion model

In machine learning, **diffusion models**, also known as **diffusion probabilistic models**, are a class of latent variable models. They are [Markov chains](https://en.wikipedia.org/wiki/Markov_chain) trained using [variational inference](https://en.wikipedia.org/wiki/Variational_Bayesian_methods). The goal of diffusion models is to learn the latent structure of a dataset by modeling the way in which data points diffuse through the [latent space](https://en.wikipedia.org/wiki/Latent_space). In computer vision, this means that a neural network is trained to [denoise](https://en.wikipedia.org/wiki/Denoise) images blurred with Gaussian noise by learning to reverse the diffusion process.

**Diffusion models were introduced in 2015** with a motivation from [non-equilibrium thermodynamics](https://en.wikipedia.org/wiki/Non-equilibrium_thermodynamics).

Diffusion models can be applied to a variety of tasks, including [image denoising](https://en.wikipedia.org/wiki/Image_denoising), [inpainting](https://en.wikipedia.org/wiki/Inpainting), [super-resolution](https://en.wikipedia.org/wiki/Super-resolution), and [image generation](https://en.wikipedia.org/wiki/Text-to-image_model). For example, an image generation model would start with a random noise image and then, after having been trained reversing the diffusion process on natural images, the model would be able to generate new natural images. Announced on 13 April 2022, OpenAI's text-to-image model [DALL-E 2](https://en.wikipedia.org/wiki/DALL-E_2) is a recent example. It uses diffusion models for both the model's prior (which produces an image embedding given a text caption) and the decoder that generates the final image.

## Courses

- [Hugging Face Diffusion Models Course](https://github.com/huggingface/diffusion-models-class)

## 📄 Articles

- [Diffusion model](https://en.wikipedia.org/wiki/Diffusion_model) on Wikipedia
