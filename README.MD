# Pneumonia-diagnosis-model-using-machine-learning

<br>

### - 작품설명 -

<br>

본 프로젝트는 Kaggle에서 제공하는 정상인의 폐 X-ray 이미지와 폐렴환자의 폐 X-ray 를 학습시켜 모델로 만들고 이를 판별하는 프로젝트입니다.<br>
이미지의 데이터 수는 상 환자 1583장과 폐렴 환자 4273장으로 구성되어 있습니다.<br>
출처 : www.kaggle.com/paultimothymooney/chest-xray-pneumonia

<br><br>
### - 사용 목적 -
의사의 진료 없이 모델을 통해서 진단이 이뤄지면 절대 안됩니다. 하지만 의료자원이 부족한 곳에선 전문의가 아니더라도 진료를 봐야 하는 경우가 생기기 때문에 진단 보조 기구로 해당 모델의 정확도가 더 높아지고 정교해 진다면 진단 보조 기구로 사용할 수 있을 것 입니다.


<br><br>
** 해당 모델은 의료용으로 개발한 것이 아님을 사전에 밝힘 **

<br><br>

  
### -목차-

1. 입출력 데이터의 처리 방법<br>
2. 모델의 학습 정확도<br>
3. 모델 정확도를 높이기 위한 노력<br>
4. 만든 모델의 차별점<br>

<hr>

<br><br>
우선 테스트 시작에 앞서 테스트에 사용하기 위해서 asdf라는 내용과 이름을 가지는 파일과 qwer이라는 이름을 가진 디렉토리를 하나씩 만들겠습니다.
<br><br>

## cat<br><br>
cat은 cat 명령 뒤에 파일 이름을 입력하면 그 파일의 내용을 출력하는 코드입니다.
보통 cat filename 이러한 형식으로 많이 사용됩니다.
<br><br>

테스트 결과 :

![slide1](https://github.com/LeeHyunHo270/ImageSave/blob/main/MiniShell/cat.jpg?raw=true)

<br><br>

## cd<br><br>
cd는 현재 작업중인 작업 디렉토리의 위치를 바꾸는 명령어입니다. 보통 cd [dir_name] 이나 cd 단독으로 사용됩니다.
<br><br>
테스트 결과:

![slide2](https://github.com/LeeHyunHo270/ImageSave/blob/main/MiniShell/cd.jpg?raw=true)

<br><br>

## cp<br><br>
cp는 파일을 복사하는 명령어입니다. 보통 cp [복사할 파일] [붙여 넣기할 파일]의 형태로 사용됩니다.
<br><br>
테스트 결과:

![slide3](https://github.com/LeeHyunHo270/ImageSave/blob/main/MiniShell/cp.jpg?raw=true)
<br><br>

## pwd<br><br>
pwd는 현재 작업이 진행되고 있는 파일의 디렉토리 경로를 출력하는 명령어입니다. 보통 pwd 단독으로 사용됩니다.
<br><br>
테스트 결과 :

![slide4](https://github.com/LeeHyunHo270/ImageSave/blob/main/MiniShell/pwd.jpg?raw=true)
<br><br>

## rm<br><br>
rm은 파일을 삭제하는 명령어입니다. 보통 rm [삭제할 파일]의 형태로 많이 사용됩니다.
<br><br>
테스트 결과:

![slide5](https://github.com/LeeHyunHo270/ImageSave/blob/main/MiniShell/rm.jpg?raw=true)
<br><br>


## rm<br><br>
ln은 지정한 파일의 링크 파일을 만드는 명령어입니다. 프로젝트에선 하드 링크를 구현했으며 ln [원본 파일] [링크 파일]과 같은 형태로 구현했습니다.
<br><br>
테스트 결과:

![slide6](https://github.com/LeeHyunHo270/ImageSave/blob/main/MiniShell/ln.jpg?raw=true)
<br><br>

## mkdir<br><br>
mkdir은 디렉터리를 생성하는 명령어입니다. 보통 mkdir [dir_name]의 형식으로 사용됩니다.
<br><br>
테스트 결과:

![slide7](https://github.com/LeeHyunHo270/ImageSave/blob/main/MiniShell/mkdir.jpg?raw=true)
<br><br>

## stat<br><br>
stat은 티렉토리나 파일의 다양한 정보를 확인할 수 있는 명령어입니다. stat [파일,디렉토리]와 같은 형태로 사용되며 ls와 다르게 요약되지 않은 정보를 출력합니다.
<br><br>
테스트 결과:

![slide8](https://github.com/LeeHyunHo270/ImageSave/blob/main/MiniShell/stat.jpg?raw=true)
<br><br>

## ls<br><br>
ls는 작업 중인 디렉터리에 있는 디렉터리와 파일 등을 확인해 출력하는 명령어입니다. 보통 ls, ls –al의 형식으로 사용됩니다,
<br><br>
테스트 결과:

![slide9](https://github.com/LeeHyunHo270/ImageSave/blob/main/MiniShell/ls.jpg?raw=true)
<br><br>

## chmod<br><br>
chmod는 파일의 권한을 변경해주는 명령어입니다. chmod [바꾸고자 하는 권한] [파일이름]의 형태로 많이 사용됩니다.
<br><br>
테스트 결과:

![slide10](https://github.com/LeeHyunHo270/ImageSave/blob/main/MiniShell/chmod.jpg?raw=true)

<br><br>
## exit<br><br>
exit은 쉘이나 스크립트에서 사용되는 종료 명령어입니다. 보통 exit 단일로 사용됩니다.
<br><br>
테스트 결과:

![slide11](https://github.com/LeeHyunHo270/ImageSave/blob/main/MiniShell/exit.jpg?raw=true)

