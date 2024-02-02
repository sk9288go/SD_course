
----
**Text to Image (Txt2img)** 텍스트 설명을 바탕으로 이미지를 생성하는 방식입니다.

> Stable Diffusion은 대량의 이미지 데이터를 학습하여 구축된 모델을 사용합니다. <br>
모델들은 '레시피'와 유사한 역할을 하며, 사용자가 제공하는 텍스트 설명에 따라 이미지를 생성합니다. 
----

  <img src="../../img/txt_img1.png" alt="Generative AI in Architecture">

Txt2img의 변수는 다음과 같습니다.

    1) Prompt (Positive Prompt / Negative Prompt)
    2) Sampling Methods
    3) Sampling Steps
    4) Size (가로, 세로)
    5) Batch
    6) CFG Scale
    7) Seed

---- 

### **1. Prompt** 

Positive Prompt와 Negative Prompt는 Txt2img 과정에서 중요한 역할을 합니다.

<p align="center">
  <img src="../../img/txt_img2.png" alt="Generative AI in Architecture">
</p>

#### **1-1. Positive Prompt** 

 > 사용자가 생성하고자 하는 이미지의 특징과 요소에 대한 상세한 텍스트 설명입니다.  
 예를 들어, "Create a serene image of a minimalist home nestled in a forest with large windows to allow natural light"와 같은 프롬프트를 입력하면, 이 설명에 부합하는 이미지가 생성됩니다. 

#### **1-2. Negative Prompt** 

 > 이미지 생성 과정에서 원치 않는 요소를 명시하는 부분입니다.  
 Negative Prompt는 생성된 이미지에서 특정 요소들을 최소화하는 데 도움을 주지만, 모든 내용이 반드시 완전히 반영되는 것은 아닙니다.

----
### **2. Sampling Method**

<p align="center">
  <img src="../../img/txt_img7.png" alt="Generative AI in Architecture" width = "600px">
</p>
    Prompt – A middle century art gallery with several digital art pieces
    Steps – 27
    Image Size – 512 x 512
    CFG Scale – 7
    Seed – 1573819953

#### **2-1. Sampling Method** 

각각의 Sampling Method는 샘플 추출 과정에 대해 다른 접근법을 제공합니다. 
>모델이 생성하려는 이미지로 벡터들이 이동하는 **방법을 결정하는 데** 중요합니다.
<br>'Euler a' 방법을 사용하는 것이 일반적이지만, 다른 샘플러를 시도하는 것도 가능합니다.

#### **2-2. 샘플러의 영향** 

>대부분의 샘플러는 이미지를 비슷하게 생성하지만, 일부 샘플러는 큰 영향을 미칠 수 있습니다. 
 어떤 샘플러는 적은 단계로 더 잘 작동할떄, 또 어떤 샘플러는 특정 범위의 샘플링 단계에서 더 높은 품질의 이미지를 생성할 수 있습니다.

----

### **3. Sampling Steps**
<p align="center">
  <img src="../../img/txt_img3.png" alt="Generative AI in Architecture" width = "600px">
</p>

#### **3-1 Sampling Steps**

이미지 생성 과정의 단계를 의미하며, **품질과 스타일**에 직접적인 영향을 미칩니다. <br>
>일반적으로 더 많은 Sampling Steps를 사용하면 더 높은 품질의 이미지를 생성할 수 있지만, 생성 시간이 더 길어집니다. <br><br>
반면, 너무 적은 Sampling Steps는 이미지의 **품질 저하**를 초래할 수 있습니다.
Sampling Steps는 이미지의 품질과 스타일, 그리고 생성 시간 사이의 균형을 맞추는 데 중요한 역할을 합니다. 따라서 상황에 맞게 조절하여 사용하는 것이 좋습니다.

----

### **4. Size**

#### **4-1 Size** 

Stable Diffusion과 같은 모델들은 특정한 이미지 사이즈, <br> 예를 들면 512~1024의 픽셀로 트레이닝됩니다. <br>
> 트레이닝 사이즈는 모델이 이미지를 생성할 때 가장 효율적으로 작동하는 크기를 나타냅니다.
즉, 학습 데이터에 기반하여 비슷한 사이즈의 이미지 일때 가장 안정적이고 정확한 결과를 제공합니다.

#### **4-2 크기 증가의 영향** 

만약 트레이닝 사이즈보다 큰 이미지를 생성하려고 시도한다면, 예상치 못한 결과가 발생할 수 있습니다.
> 예를 들어, 모델이 하나의 건물 대신 두 개의 건물을 만들거나, 사람의 형태가 이상하게 나타나는 경우 등이 있습니다.
<br>이러한 현상은 모델이 더 큰 이미지에 대해 최적화되지 않았기 때문에 발생합니다.

----
 
### **5. Batch** 

Batch 설정은 Stable Diffusion에서 한번에 생성할 이미지의 수와 단위를 결정하는 설정입니다. 

#### 5-1 배치 수
> 생성할 이미지의 총 개수를 정하는 설정입니다.

#### 5-2 배치 크기
> 한 번에 생성할 이미지의 수를 정하는 설정입니다.  
 한 번의 실행으로 몇 장의 이미지를 동시에 생성할지 결정합니다. (Vram) 사용이 늘어납니다.

----
 
### **6. CFG Scale** 

CFG Scale은 프롬프트에 얼마나 충실할 것인지 결정하는 가중치입니다.

<p align="center">
  <img src="../../img/txt_img5.png" alt="Generative AI in Architecture" width= "600px">
</p>
    출처 : https://www.bercon.org/b24f00d3-bf56-4f3c-977e-b9de6b59ecf4

#### 6-1 CFG Scale

 프롬프트에 따른 이미지의 생성 정도를 조절합니다. 
 
 > 높은 CFG Scale 값은 프롬프트에 더 충실한 이미지를 생성하지만, 동시에 프롬프트에만 편향될 가능성이 높아집니다.
 낮은 CFG Scale 값은 더 창의적인 결과물을 얻을 수 있지만, 프롬프트와는 동떨어진 내용이 나올 수 있습니다. 
 일반적으로 7~11 범위의 CFG Scale이 적당합니다. 

----

### **7. Seed** 
<p align="center">
  <img src="../../img/txt_img4.png" alt="Generative AI in Architecture" width= "600px">
</p>

#### 7-1 Seed

> -1을 입력하면 매번 다른 이미지가 생성되며, 특정 시드 값 입력시 비슷한 구도나 스타일의 이미지를 반복적으로 생성할 수 있습니다. 
하지만, 항상 정확히 동일한 결과를 보장하지는 않습니다.

#### 7-1 change with same seed

> 이미지의 크기 와 프롬프트를 변경하면 동일한 시드 값을 사용하더라도, 조금 다른 구도나 스타일의 이미지가 생성될 수 있습니다.
시드 값과 이미지 사이즈, 프롬프트 변경은 ControlNet을 사용하여 다양한 결과를 탐색하고 실험하는데 유용합니다. 

----