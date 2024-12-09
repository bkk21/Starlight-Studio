# 🌌 별빛 창작소 (Starlight Studio)
### 📚 유치원생을 위한 생성형 AI 기반의 창의적인 나만의 동화책 만들기 웹 서비스
- 별빛 창작소는 아이들의 상상력을 키워주고, 가족과 함께 추억을 쌓는 특별한 공간인 동화 제작 플랫폼입니다.
- 유치원 및 교육 현장에서도 활용할 수 있는 창작 활동 플랫폼으로 활용할 수 있습니다.<br><br>

<div align="center">
<a href = "blue.kku.ac.kr:1203"><img width="512" src="https://github.com/user-attachments/assets/ddbf89c0-fe5d-4ba4-8f3d-e67fa9bd6704"> </a>

 [[Web 바로가기 링크]](https://blue.kku.ac.kr:1203)
</div>
<br>

# 🖥️ 주요 기능
- **동화 스토리 생성:** ChatGPT API를 활용해 입력한 제목, 주제, 캐릭터, 배경으로 스토리 생성
- **스토리 수정 및 재생성:** AI가 생성한 내용을 저장하거나 재생성
- **동화 삽화 생성:** 동화 내용에 기반한 맞춤형 이미지 생성
- **동화 미리보기 제공**
- **동화 공유 기능:** URL 형태로 간편히 공유
<br>

# 💬 Prompt Engineering (✨My Position)
- 텍스트와 이미지 생성 모두 Prompt Engineering만 진행되었습니다.
- 아래 프롬프트 전문은 가장 기본적인 생성에 대한 프롬프트만 소개되어 있습니다. 수정과 관련된 프롬프트는 파일을 참고해주시길 바랍니다.

**텍스트 생성 프롬프트 전문**
```python
sys_prompt = """###시스템 프롬프트:
넌 지금부터 동화 작가야. 아래는 동화를 생성할 때 지켜야 하는 규칙이야.
1. 동화는 10세 이하 어린이들을 위한 내용이므로, 술, 총, 폭력, 마약 등과 같이 어린이에게 부적절한 내용이 들어가지 않을 것.
2. 동화 제작과 관련이 없는 질문을 할 때에는 "[시스템] 저는 동화 창작 도우미입니다. 동화와 관련된 이야기를 작성해주세요!"를 출력할 것
3. 이전 내용이 없을 때에는 동화의 첫 문장을 생성해야 하며, 주인공에 대한 설명으로 시작할 것
4. 이전 내용이 있을 경우 이전 내용의 뒷 이야기를 생성할 것
5. 한 문장은 "안녕하세요."와 같으며,  동화는 한 문장만 생성할 것
6. 새로 생성하는 문장은 수정 문장과 다른 문장이어야 하며, 이전 내용이 포함되지 않을 것
7. 이전 내용과 중복되지 않도록 다음 동화 내용을 생성할 것
8. 내용에서 캐릭터가 말하는 대사는 큰따옴표로 표시할 것
9. 단어는 10세 이하 어린이가 이해할 수 있는 쉬운 단어를 사용할 것
10. 문장은 '~했어요'와 같은 문장으로 만들 것
    """
    
#input 지정
prompt = f"###페이지 번호: {num}\n\n###주제: {topic}\n\n##캐릭터: {character}\n\n##배경: {background}\n\n###이전내용: {context}\n\n"
prompt += "###사용자 입력: 페이지 번호에 해당하는 내용을 만드는 건데, 주제, 캐릭터, 배경, 이전 내용을 참고해서 동화 다음 내용을 한 줄 생성해줘." 
```

**이미지 생성 프롬프트 전문**
```python
sys_prompt = """###시스템 프롬프트:
아래는 그림을 그릴 때 지켜야 하는 규칙이야.
1. 그림에는 술, 총, 폭력, 마약 등과 같이 어린이에게 부적절한 그림이 들어가지 않을 것
2. 사용자 입력에 맞는 그림을 그릴 것
3. 주제, 캐릭터, 배경, 사용자 입력을 참고해서 그릴 것
4. 그림은 동화책 삽화처럼 부드럽고 따뜻한 색조를 사용하며, 파스텔톤의 색상을 강조할 것
5. 그림에는 말풍선과 글자가 없어야 할 것
6. 그림의 분위기는 밝고 희망적이며 따뜻한 감정을 주도록 구성할 것
7. 캐릭터의 표정, 의상, 소품 등을 주제와 배경에 맞춰 자연스럽게 연출할 것
8. 배경과 캐릭터가 조화를 이루도록 전체적인 구도를 구성할 것
9. 그림의 스타일은 [부드러운 선과 확실한 색감, 캐릭터의 큰 눈과 친근한 표정]과 같은 특징을 반영할 것
10. 배경은 세부적인 디테일(예: 나무 잎사귀의 빛 반사, 고요한 강물의 반짝임)을 추가해 생동감 있게 표현할 것
11. 주제, 캐릭터, 배경, 사용자 입력이 서로 연결되고 조화를 이루도록 설정할 것
12. 사용자 입력에 따라 이야기가 전달되도록 그림의 구도를 구성할 것
"""        
#input 지정
prompt_text = f"###시스템 프롬프트: {sys_prompt}\n\n###주제: {topic}\n\n###캐릭터: {character}\n\n###배경: {background}\n\n###사용자 입력: {prompt_input}\n\n"
```
<br>

# 👀 Result
| <img width="1724" alt="1" src="https://github.com/user-attachments/assets/fe5203de-082e-4af8-a398-583cb240bd2a">  | <img width="1724" alt="2" src="https://github.com/user-attachments/assets/1a95e97d-401c-4a7b-9fa3-07ae75b38067"> |
|:---:|:---:|
| <img width="1724" alt="3" src="https://github.com/user-attachments/assets/848ebbef-66b6-4cf7-a109-5595c0ba304b"> | <img width="1724" alt="4" src="https://github.com/user-attachments/assets/f7a24b06-0896-4ad8-87de-207a6a6b843c"> |
| <img width="1724" alt="5" src="https://github.com/user-attachments/assets/4d2046a9-e2f1-4177-883d-4a3dc3f325da"> | <img width="1724" alt="6" src="https://github.com/user-attachments/assets/09ac5b7e-36fe-48bd-9fda-cadc54930188"> |
| <img width="1724" alt="7" src="https://github.com/user-attachments/assets/ff946bce-5a3a-4e2a-bf13-13f131fbf294"> | <img width="1724" alt="8" src="https://github.com/user-attachments/assets/0b656684-9eeb-4688-8101-168767a41b71"> |
| <img width="1724" alt="9" src="https://github.com/user-attachments/assets/71bacc4b-d1f6-43c1-8085-c6dd98e70ab7"> | <img width="1724" alt="10" src="https://github.com/user-attachments/assets/918fb3a8-6e6a-4521-9d0a-c6c79bb0331a"> |

> [!Note]
> 별빛 창작소 웹 사이트는 `세종글꽃체`를 사용합니다.

<br>

# 🛠️ Stacks
<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=python,ubuntu,anaconda,vscode,github&theme=light&perline=8" />
  </a>
</p>

<br>

# 😆 Contributors & Position
|   역할   |  이름  | GitHub 프로필                   |
| :------: | :----: | :------------------------------ |
| Front-End | 김도환 | https://github.com/ehghks021203 |
| Back-End  | 엄태현 | https://github.com/the0807      |
|  Gen-AI  | 정보경 | https://github.com/bkk21        |
|  Gen-AI  | 송주훈 | https://github.com/zoo171       |

<br>

# 📌 Related Links
| 프로젝트 | Github 링크                                               |
| :------: | :-------------------------------------------------------- |
| Front-End | https://github.com/ehghks021203/Starlight-Studio-FrontEnd |
| Back-End  | https://github.com/the0807/Starlight-Studio-BackEnd       |
|  Gen-AI  | https://github.com/bkk21/Starlight-Studio                 |

<br>
