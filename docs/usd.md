# USD
Universal Scene Description의 약자입니다.
여러분이 아마도 TD 업무를 하면서 미래에는 이 포멧을 자주 다루게 될것 같습니다.
픽사의 3D 파이프라인 코어입니다. 아래 장점들을 가지고 있습니다.

- 일반 언어형태로 사용할 수 있습니다.
- 3D 데이터를 패키징 할 수 있습니다.
- 3D 데이터를 Assembling(조합) 할 수 있습니다.
- 3D 데이터를 편집할 수 있습니다.
- 여러 툴을 이용해서 콘텐츠를 만들 수 있습니다.(아직 USD가 활발하게 모든 툴에 탑제 되려면 조금더 시간이 필요하긴 합니다.)
- 여러 아티스트가 하나의 에셋을 작업할 수 있습니다.
- 데이터 로딩시 소요되는 시간을 최소화할 수 있습니다.
- 사용자가 커스텀하게 원하는 데이터를 추가할 수 있습니다.(굉장히 강력한 기능입니다.)

홈페이지 : https://graphics.pixar.com/usd/docs/index.html

## 파일의 종류
- .usd
- .usda : 아스키 파일
- .usdc : 바이너리 파일

## PyOpenGL 설치
usdview는 PyOpenGL을 사용합니다. 설치해주세요.

```
# pip install PyOpenGL
```

## 컴파일
```
$ cd ~/app
$ git clone https://github.com/PixarAnimationStudios/USD USD_src
$ cd USD_src
$ python USD/build_scripts/build_usd.py ~/app/USD
```

터미널에서 2개의 값을 임시로 설정합니다.

```
$ export PYTHONPATH="${PYTHONPATH}:$HOME/app/USD/lib/python"
$ export PATH="${PATH}:$HOME/app/USD/bin"
```

```
$ usdview extras/usd/tutorials/convertingLayerFormats/Sphere.usda
```

![usdview](https://user-images.githubusercontent.com/1149996/49622382-ba7b6280-fa0c-11e8-9898-e1031142de91.png)

화면처럼 Usdview가 잘 뜨면 위 환경변수를 자신의 .bashrc에 잘 추가해두세요.
우리는 많은 기능을 활성화해서 컴파일하지 않았습니다. 더 많은 기능을 이용하고 싶다면 사용하는 라이브러리를 추가 설정하여 다시 컴파일하면 됩니다.


## 명령어
- sdfdump
- sdffilter
- stringify
- testusdview
- usdcat
- usdchecker
- usddiff
- usdedit
- usdstitch
- usdstitchclip
- usdview
- usdzip

## 파일구조
usd파일은 아래와 같은 형태를 가지고 있습니다.

```
#usda 1.0

class "_class_Planet"
{
    bool has_life=False
}

def Xform "SolarSystem"
{
    def "Earth" (
        references = @./planet.usda@</Planet>
    )
    {
        bool has_life = True
        string color = "blue"
    }

    def "Mars" (
        references = @./plant.usda@</Plant>
    )
    {
        string color = "red"
    }

    def "Saturn" (
        references = @./plant.usda@</Plant>
        variants = {
            string rings = "with_rings"
        }
    )
    {
        string color = "beige"
    }
}
```

```
#usda 1.0

def Cube "Box"
{
    float3 xformOp:scale = (5, 5, 5)
    uniform token[] xformOpOrder = ["xformOp:scale"]
}
```


## Reference
- https://github.com/PixarAnimationStudios/USD
- https://github.com/vfxpro99/usd-build-club
- https://github.com/vfxpro99/usd-build-club/tree/master/prerequisites-linux
- https://github.com/meshula/mkvfx
- https://graphics.pixar.com/usd/overview.html
