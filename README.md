## VS Code Verilog 컴파일 설정
### iVerilog 다운로드
### Icarus Verilog for Windows

#### 1. Icarus Verilog 설치
```
https://bleyer.org/icarus/
```
<img width="1898" height="841" alt="image" src="https://github.com/user-attachments/assets/0d3415d7-5ef5-4ff8-a901-b808b9d4ee98" />
<br>
다운로드 -> iverilog-v12-20220611-x64_setup [18.2MB] 
<br>
<img width="582" height="482" alt="image" src="https://github.com/user-attachments/assets/6f63f256-728f-49d6-8033-59580fb817a0" />
<br>
<img width="466" height="386" alt="image" src="https://github.com/user-attachments/assets/283e8cb7-2f54-40bc-a99c-4860d6e1c2ef" />
<br>
<img width="466" height="386" alt="image" src="https://github.com/user-attachments/assets/9cea11ad-8d64-4558-b917-f20126fc5b05" />
둘 다 체크
<br>
<img width="466" height="386" alt="image" src="https://github.com/user-attachments/assets/959ad32d-5202-41b4-89fe-10d95761327e" />
두번째 무조건 체크
<br>
<img width="466" height="386" alt="image" src="https://github.com/user-attachments/assets/0c799177-8415-4b9d-adc4-89af9910c703" />
<br>

VScode 폴더 하나 생성해서 
<img width="1159" height="728" alt="image" src="https://github.com/user-attachments/assets/1f4c4e5e-1a81-4679-8698-1d42b4f78a9a" />
<br>
<img width="1907" height="687" alt="image" src="https://github.com/user-attachments/assets/7710f33c-aef5-4683-bb5b-060ad01c4c84" />
<br>

#### 1.1 Icarus Verilog 설치 확인

(window +R) cmd 열기 
설치 확인하기
```
iverilog -V
```
<img width="743" height="948" alt="image" src="https://github.com/user-attachments/assets/c7cb4d57-0009-40d5-a8d7-1a7fe9fc3cef" />
<img width="760" height="303" alt="image" src="https://github.com/user-attachments/assets/9c1f814f-48d8-4edc-88c3-88a2e2153fb0" />
<br>
위와 같이 버전 뜨면 프로그램은 설치 준비 완

#### 2. VS code에서 설정하기

이전에 김남우 교수님이 해준 자동 정리 & 스니펫 설정 유지하고
+ 빠른 문법 오류 확인 설정 추가 예정

tasks.json 파일에 코드 수정 (그냥 삭제하고) 아래 코드 그냥 그대로 복붙 ㄱㄱ
```
"version": "2.0.0",
    "tasks": [
        {
            "label": "build",
            "type": "shell",
            "command": "msbuild",
            "args": [
                "/property:GenerateFullPaths=true",
                "/t:build",
                "/consoleloggerparameters:NoSummary"
            ],
            "group": "build",
            "presentation": {
                "reveal": "silent"
            },
            "problemMatcher": "$msCompile"
        },
        {
            "label": "Format Verilog",
            "type": "shell",
            "command": "C:/Users/52/AppData/Local/Microsoft/WindowsApps/python.exe",
            "args": [
                "C:/verilog_formatter/verilog_formatter_cli.py",
                "${file}"
            ],
            "presentation": {
                "reveal": "always",
                "panel": "shared"
            },
            "problemMatcher": []
        },
        {
            "label": "Verilog Compile Check",
            "type": "shell",
            "command": "iverilog",
            "args": [
                "-t",
                "null",
                "${file}"
            ],
            "group": "none",
            "presentation": {
                "reveal": "always"
            },
            "problemMatcher": []
        }
    ]
}
```
저장 후


