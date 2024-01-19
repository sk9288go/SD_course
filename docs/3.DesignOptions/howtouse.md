# 디자인 옵션 탐색


<table style="margin-left: 15%;">

        <tr>
            <th>기능</th>
            <th>추가 설치 여부</th>
            <th>인풋 데이터</th>
        </tr>
        <tr>
            <td>txt2img</td>
            <td>추가 설치 X</td>
            <td>텍스트 프롬프트</td>
        </tr>
        <tr>
            <td>img2img</td>
            <td>추가 설치 X</td>
            <td>이미지 + prompt</td>
        </tr>
        <tr>
            <td>inpaint</td>
            <td>추가 설치 X</td>
            <td>이미지 + prompt + 마스킹</td>
        </tr>
        <tr>
            <td>txt2img(control-net) 스케치</td>
            <td>추가 설치 O</td>
            <td>스케치 + prompt</td>
        </tr>
        <tr>
            <td>txt2img(control-net) 깊이 맵</td>
            <td>추가 설치 O</td>
            <td>모델링 이미지(depth 맵) + prompt</td>
        </tr> </table>

Stable diffusion은 기본적으로 txt2img, img2img, inpaint등의 기능을 포함하고 있으며, 각 기능은 특정 인풋을 요구합니다.

1. **txt2img** (텍스트로 이미지 생성)<br>
    txt2img는 사용자가 입력한 프롬프트에 따라 관련 이미지를 생성해주는 핵심 기능입니다. 이 기능을 활용하려면 
    텍스트 프롬프트 (이미지로 변환하고자 하는 텍스트) 이 필요합니다. 

2. **img2img** (이미지로 이미지 생성)<br>
    img2img 기능은 원본 이미지에 스타일 이미지, 텍스트를 적용하여 새로운 이미지를 생성합니다. 이 기능을 활용하려면 원본 이미지 (스타일을 적용하고자 하는 이미지),텍스트 프롬프트 (선택 사항): 스타일 변환의 방향을 지정하는 텍스트가 필요합니다.

3. **inpaint/outpaint** (이미지 복원 및 변경)<br>
    inpaint 기능은 이미지의 변경이 필요한 구역을 지정하여 AI가 해당 구역의 이미지를 생성합니다. 이 기능을 활용하려면 원본 이미지 (수정하고자 하는 이미지), 마스크 변경하거나 복원할 영역을 표시한 마스크 이미지를 설정해야 합니다.

---- 

해당 WebUi에는 추가로 control-net extension 모델을 설치하여 스케치, 이미지 depth와 연결하여 지정한 이미지에 맞춘 이미지 생성이 가능합니다. 해당 모델들은 https://huggingface.co/lllyasviel/ControlNet/tree/main/models 에서 설치 가능하며 이에 대한 설명은 추후 게시글을 통해 다루도록하겠습니다. 