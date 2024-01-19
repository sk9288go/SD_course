### 주변 환경 적용/ControlNet

이번 게시물에서는 지난번 말씀드렸던대로 Stable Diffusion의 특수기능 중 하나인 ControlNet에 대해 설명드리고자 합니다.

'ControlNet is a neural network structure to control diffusion models by adding extra conditions'
(Source : https://github.com/lllyasviel/ControlNet)

 
위 설명과 같이 ControlNet은 '조건을 추가하여 확산 모델을 제어하는 신경망 구조'이고,
이것이 의미하는 바는 추가된 조건(예를 들어 스케치)에 맞춰 이미지가 생성되는 것입니다.
따라서 스케치 사진을 넣거나 모델링 이미지를 넣음으로써 그에 맞춰진 이미지를 생성할수도 있습니다
ControlNet을 사용하는데 알아두어야 할 요소(Factor)는 아래와 같습니다.

1) Image
2) Enable, Low VRAM
3) Weight
4) Guidance (Start, End)
5) Annotator resolution
6) Canvas Size (Width, Height)
7) Preview annotator result
----
ControlNet에 입력해야하는 Image 위치는 아래 이미지와 같으며, JPEG 혹은 PNG 파일을 권장드립니다.

Weight는 ControlNet에 입력한 이미지의 영향을 얼마나 줄 것인지에 대한 수치입니다.

0에서 2까지 입력할 수 있으며, 입력된 가중치에 따른 이미지 생성 결과 차이는 아래 이미지와 같습니다.
1.5가 넘어가는 경우 이미지가 많이 훼손되는 것을 볼 수 있고,
0.75~1.25 정도가 바람직해보이며,
0~0.5가 되더라도 생성되는 건축물의 구도는 일정함을 볼 수 있습니다
----
4. Guidance (Start, End)

Guidance는 ControlNet이 적용되는 구간을 입력하는 것으로,
0에서 1까지 범위를 Start, End로 나누어 입력할 수 있습니다.
그리고 그에 대한 결과 이미지는 아래와 같습니다.

Guidance Start가 0이고 Guidance End가 1일 경우 이미지가 생성되는 처음 단계부터 마지막 단계까지 ControlNet이 적용되며,

이 경우 ControlNet에 입력된 스케치를 최대한 따라가는 것을 볼 수 있습니다.
반면, 0~0이거나 1~1일 경우 스케치의 구도만 반영될 뿐 별개의 이미지가 생성되고 있습니다.
그 외에 0.5~1, 0.75~1의 경우에는 별개의 이미지가 생성되던 중에 스케치가 개입되어 깨지는 현상이 보입니다.
따라서 가장 권장드리는 수치는 0~0.5(스케치로부터의 자유도 상승) 혹은 0~1(최대한 스케치와 일치)가 되겠습니다.


----
5. Annotator resolution
Annotator resolution은 ControlNet의 Sketch를 더욱 섬세하게 인식하는 정도로,

아래와 같은 인식정도를 볼 수 있습니다.

ControlNet은 높은 GPU와 메모리를 필요로 하며, Annotator resolution이 컴퓨터 성능에 비해 높아질 경우 오류가 날 수 있습니다.

따라서 오류가 날 경우에는 Annotator resolution를 줄이시면 문제가 해결됩니다.

----

6. Canvas Size (Width, Height)
Canvas Size는 생성되는 이미지의 크기가 아니고 ControlNet에 입력되는 스케치의 사이즈를 입력하는 것입니다.

하지만 Canvas Size에 입력된 수치가 높다고 해서 이미지 생성 결과가 더 정확해지는 정도는 미비하므로

장변이 512를 안 넘는 것을 권장드립니다.
----
7. Preview annotator result



Preview annotator result는 ControlNet에 입력된 스케치가 어떻게 인식되는지 미리볼 수 있는 기능으로,

아래 GIF와 같이 Preview 및 Hide를 통해 켜고 끌 수 있습니다
----


**AI를 활용한 환경 통합 방법 논의:**
AI를 이용해 특정 환경에 디자인을 어떻게 통합하는지에 대한 전반적인 방법론을 설명합니다.
ControlNet 도구를 활용하여 공간의 기하학적 및 의미적 특성을 고려하면서 장면 내에 객체나 디자인을 배치하는 방법을 소개합니다.

**ControlNet의 다양한 모델 및 기능 소개:**    

1. **Canny (Edge Detection):** 이미지 가장자리를 감지, 객체의 윤곽을 명확하게 하는 데 사용.
2.  **M-LSD Lines (Line Segment Detection):** 선분 감지를 통해 건축적 구조나 형태를 파악하여 스케치 라인을 생성하여 이미지 생성.
3. **HED Boundary (Holistic Edge Detection):** 이미지의 전체적인 가장자리를 감지하여 복잡한 장면에서도 soft한 스케치라인으로 객체를 구분하여 이미지 생성.
4. **Scribbles:** 사용자가 직접 스케치한 스크리블을 기반으로 디자인 요소를 장면에 통합합니다.
5. **Fake Scribble (From Image):** 이미지에서 추출된 가짜 스크리블을 사용하여 디자인 요소를 보다 사실적으로 장면에 배치합니다.
6. **Human Pose:** 인간의 포즈를 인식하여 장면에 인간적 요소를 통합합니다.
7. **Semantic Segmentation:** 장면의 다양한 요소를 의미적으로 구분하여 보다 정확한 컨텍스트 통합을 가능하게 합니다.
8. **Depth Map:** 장면의 깊이 정보를 이용하여 3D 공간상에서의 객체 배치를 보다 사실적으로 구현합니다.
9. **Normal Map:** 표면의 방향성 정보를 활용하여 텍스처와 조명의 상호작용을 더욱 정밀하게 표현합니다.

**ControlNet을 활용한 실제 적용 사례 시연:**    
- 건축 환경에서 ControlNet의 여러 모델을 활용하는 방법과 이들의 장단점에 대해 구체적인 사례를 통해 설명합니다.
- 다양한 환경에 디자인을 통합하는 실습을 통해 학생들이 ControlNet의 다양한 기능을 직접 경험하고 익힐 수 있도록 합니다.

----
