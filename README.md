# 🧠 Explorando IA Generativa com Python e Stable Diffusion XL

Estou migrando minhas prática para o ecossistema de **IA generativa com Python**.  
Este repositório documenta meu primeiro experimento prático com **modelos de difusão**, usando o **Stable Diffusion XL** via biblioteca `diffusers` do Hugging Face, executado no **Google Colab**.

---

### ✨ O que eu fiz:

Gerei uma imagem com o prompt:
> *"Astronaut in a jungle, cold color palette, muted colors, detailed, 8k"*

Usei o modelo **Stable Diffusion XL**, que é mais leve e funciona bem no Colab grátis.

---

### 🛠️ Tecnologias usadas:

- Python
- Google Colab
- Hugging Face (`diffusers`, `transformers`)
- Stable Diffusion XL

---

### 🖼️ Resultado:

Aqui está a imagem que eu gerei e salvei:

![Imagem gerada com IA](sd-xl.png)

> ✅ A imagem foi gerada com sucesso no Colab!
---

### 🧑‍💻 Como eu fiz (passo a passo):

1. Instalei as bibliotecas necessárias:
   ```python
   !pip install -U diffusers transformers accelerate safetensors

---
2. Carreguei o modelo e configurei para economizar memória:
    ```python
   pipe = StableDiffusionXLPipeline.from_pretrained(
    "stabilityai/stable-diffusion-xl-base-1.0",
    torch_dtype=torch.float16,
    use_safetensors=True,
    variant="fp16",
    low_cpu_mem_usage=True,
    )
---
3. Gerei a imagem com o prompt desejado:
    ```python
    image = pipe(
    prompt,
    height=1024,
    width=1024,
    guidance_scale=7.5,
    num_inference_steps=30,
    generator=torch.Generator("cuda" if torch.cuda.is_available() else "cpu").manual_seed(9)
    ).images[0]
    image.save("sd-xl.png")


