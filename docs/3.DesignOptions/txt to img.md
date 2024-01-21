

Text를 활용하여 Image를 생성하는 'Text to Image(Txt2img)'에 대한 소개를 하고자 합니다.
우선 Stable Diffusion에서는 Check Point(Ckpt)라고 해서 수만장의 건축이미지를 학습시킨 모델이 있으며, 해당 모델에 학습된 이미지를 토대로 이미지를 생성(Txt2img)하거나 변환(Img2img)할수도 있습니다.

<p align="center">
  <img src="../../img/txt_img1.png" alt="Generative AI in Architecture">
  <img src="../../img/txt_img0.png" alt="Generative AI in Architecture">
</p>

우선, Txt2img를 하기 위해서 다루어야하는 요소(Factor)들은 아래와 같으며, 차례대로 설명드리도록 하겠습니다.
 
1) Prompt (Positive Prompt / Negative Prompt)
2) Sampling Methods
3) Sampling Steps
4) Size (가로, 세로)
5) Batch
6) CFG Scale
7) Seed
---- 

1. Prompt (Positive Prompt / Negative Prompt)

<p align="center">
  <img src="../../img/txt_img2.png" alt="Generative AI in Architecture">
</p>
Prompt (Positive Prompt): 사용자가 만들고자 하는 이미지에 대한 설명을 텍스트로 입력하는 부분입니다. 예를 들어, 'Create a serene image of a minimalist home nestled in a forest with large windows to allow natural light'와 같은 프롬프트를 입력하면, 해당 설명에 부합하는 이미지가 생성됩니다.
Negative Prompt: 이미지 생성 과정에서 제외하고 싶은 요소를 명시하는 부분입니다. Negative Prompt는 이미지 생성에 영향을 미쳐 원치 않는 요소를 최소화하는 데 도움을 줍니다. 하지만, 모든 Negative Prompt가 반드시 완전히 반영되는 것은 아니며, 주로 제외될 확률을 높이는 역할을 합니다.
Prompt의 중요성: Prompt는 생성될 이미지의 스타일, 분위기, 구성 요소 등을 결정하는 핵심 요소입니다. Positive Prompt와 Negative Prompt의 조합을 통해 사용자는 원하는 이미지를 더 정확하게 지시할 수 있습니다.

2. Sampling Methods
<p align="center">
  <img src="../../img/txt_img7.png" alt="Generative AI in Architecture">
</p>
Prompt – A middle century art gallery with several digital art pieces
Steps – 27
Image Size – 512 x 512
CFG Scale – 7
Seed – 1573819953

Sampling Methods의 기능: 각각의 Sampling Method는 샘플 추출 과정에 대해 다른 접근법을 제공합니다. 이는 모델이 생성하려는 이미지로 실제로 이동하는 방법을 결정하는 데 중요합니다.
다양한 실험 가능: 다양한 Sampling Methods를 시도함으로써, 원하는 결과와 성능에 맞는 방법을 찾을 수 있습니다. 각 방법은 이미지 생성 과정에 다르게 영향을 미칩니다.
기본 설정 사용: 기본적으로 설정된 'Euler a' 방법을 사용하는 것이 일반적이지만, 다른 샘플러를 시도하는 것도 가능합니다.
샘플러의 영향: 대부분의 샘플러는 이미지를 비슷하게 생성하지만, 일부 샘플러는 이미지에 큰 영향을 미칠 수 있습니다. 어떤 샘플러는 적은 단계로 더 잘 작동하며, 또 다른 샘플러는 특정 범위의 샘플링 단계에서 더 높은 품질의 이미지를 생성할 수 있습니다.

3. Sampling Steps
<p align="center">
  <img src="../../img/txt_img3.png" alt="Generative AI in Architecture">
</p>
ampling Steps의 역할: 이미지 생성 과정의 단계를 결정합니다. 이는 생성되는 이미지의 품질과 스타일에 직접적인 영향을 미칩니다.
품질과 시간의 균형: 일반적으로 더 많은 Sampling Steps를 사용하면 더 높은 품질의 이미지를 생성할 수 있지만, 생성 시간이 더 길어집니다. 반면, 너무 적은 Sampling Steps는 생성된 이미지의 품질 저하를 초래할 수 있습니다.
적절한 설정의 중요성: Sampling Steps는 생성되는 이미지의 품질과 스타일, 그리고 생성 시간 사이의 균형을 맞추는 데 중요한 역할을 합니다. 따라서 상황에 맞게 조절하여 사용하는 것이 좋습니다.

4. Size
트레이닝 사이즈의 영향: Stable Diffusion은 일반적으로 512x512 사이즈로 트레이닝됩니다. 이러한 트레이닝 사이즈는 모델이 최적화된 이미지 크기를 의미하며, 이 범위 내에서 가장 안정적인 결과를 기대할 수 있습니다.
크기 증가에 따른 변화: 이미지 크기를 트레이닝된 사이즈보다 크게 조정할 경우, 예상치 못한 결과가 발생할 수 있습니다. 예를 들어, 건물이 두 개 생성되는 현상, 사람이 두 명 나타나는 현상 등이 이에 해당합니다. 이는 모델의 'attention cloud'가 큰 이미지에서 분산되어 예상과 다른 방식으로 작동하기 때문입니다.
주의사항: 너무 큰 크기로 설정할 경우, 모델의 atte
 
5. Batch 
Batch 설정은 Stable Diffusion에서 한번에 생성할 이미지의 수와 그 생성의 단위를 결정하는 설정입니다. 

배치 수: 생성할 이미지의 총 개수를 정하는 설정입니다. 사용자가 원하는 이미지의 총량을 설정할 수 있습니다.
배치 크기: 한 번에 생성할 이미지의 수를 정하는 설정입니다. 이는 한 번의 실행으로 몇 장의 이미지를 동시에 생성할지 결정합니다.
배치 크기의 중요성: 배치 크기를 높게 설정하면 시스템에 과부하가 걸릴 수 있습니다. 따라서 안정성을 고려하여 일반적으로 배치 크기를 '1'로 설정하는 것이 권장됩니다.
 
6. CFG Scale 

CFG Scale은 Stable Diffusion의 중요한 설정 중 하나로, 프롬프트에 얼마나 충실할 것인지 결정하는 가중치입니다. 요약하면 다음과 같습니다:
  <p align="center">
  <img src="../../img/txt_img5.png" alt="Generative AI in Architecture" width= "800px">
</p>

CFG Scale의 역할: 프롬프트에 따른 이미지의 생성 정도를 조절합니다. 높은 CFG Scale 값은 프롬프트에 더 충실한 이미지를 생성하지만, 동시에 프롬프트에만 편향될 가능성이 높아집니다.
적정 값 설정: 일반적으로 7~11 범위의 CFG Scale이 적당합니다. 이 범위는 지시에 충분히 따르면서도 일정 수준의 창의성을 유지할 수 있습니다.
낮은 값의 효과: CFG Scale 값을 낮게 설정하면 더 창의적인 결과물을 얻을 수 있습니다.
실험적 사용: CFG Scale 값을 Sampling Steps와 함께 다양하게 조절해보면서 최적의 결과를 찾는 것이 좋습니다.

CFG Scale 역시 Sampling Steps와 같이 바꿔가며 사용하시면 됩니다.
https://www.bercon.org/b24f00d3-bf56-4f3c-977e-b9de6b59ecf4

7. Seed

  <p align="center">
  <img src="../../img/txt_img4.png" alt="Generative AI in Architecture">
</p>

시드 값 변경: -1을 입력하면 매번 다른 이미지가 생성되며, 특정 시드 값 입력시 비슷한 구도나 스타일의 이미지를 반복적으로 생성할 수 있습니다. 하지만, 항상 정확히 동일한 결과를 보장하지는 않습니다.
이미지 사이즈 변경: 이미지의 크기를 변경하면 동일한 시드 값을 사용하더라도, 조금 다른 구도나 스타일의 이미지가 생성될 수 있습니다.
프롬프트 변경: 프롬프트에 소소한 변경을 적용하면, 같은 시드 값을 사용해도 다른 스타일이나 구도의 이미지가 생성될 가능성이 있습니다.
시드 값과 이미지 사이즈, 프롬프트 변경은 ControlNet을 사용하여 다양한 결과를 탐색하고 실험하는데 유용합니다. 이러한 기능들은 사용자가 원하는 방향으로 이미지를 조정하고 다양성을 탐구할 수 있게 도와줍니다.