---
layout: post
title:  Histogram back projection을 이용한 피부 인식의 한계
date:   2020-01-06 15:46:00 +0900
---
테스트 이미지에서 얼굴 영역을 선택하고 선택된 영역내의 점들의 색상분포를 Hue - Saturation 히스토그램으로 변환한다([Hsv Histogram](../../../2019/12/29/hsv-histogram.html)). 이를 역투영(Back Projection) 함으로써 사진 내 피부색의 점들을 인식한다.
이상적으로는 히스토그램 내 데이터가 하나의 분포를 이루며 충분히 밀집되고 이를 역투영 시켰을 때 피부에 대한 점들만이 도드라 지는 것이다.

![Image Alt Ideal](/assets/img/ideal.png)


### 한계
동일인물에 대해서도 사진의 피부톤은 조명환경에 따라 달라진다.
히스트그램에서 구분된 클러스터가 생길 수 있으며, 이때 하나의 구분된 클러스터를 이루는 피부색 범위은 다른 구분된 클러스터의 색을 피부로 인식해 내지 못한다.
아래와 같이 피부톤 영역이 각각 나눠지는 두 이미지 둘 중 하나를 테스트 이미지로 사용하여 모델을 구축하였을 때 다른 이미지의 피부점들은 찾아낼 수 없게 되는 것이다.

![Image Alt Segmentation](/assets/img/segmentation.png)

또, 조명으로 인해 피부톤이 흰색에 가까워지는 경우 Hue가 색상구분을 위한 인자로 작동이 되지 않는다. 아래 이미지에 대한 히스토그램을 보면 밀집된 튼튼한 클러스터를 만드는데 실패한 것을 볼 수있다. 뚜렷한 범위를 만들어 낼 수 없는 모델을 이용하여 역투영하는 경우 False positive가 커진다. 모델 생성단계에서 문제 데이터가 유입되지 않도록 걸러낼 수 있지만, 중요한 점은 정제된 히스토그램으로는 문제 이미지에서 피부점들을 인식해 낼 수 없다는 것이다.

![Image Alt Too bright](/assets/img/toobright.png)


### 더 생각해볼 꼭지들
다양한 조명환경에 대해 독립적인 모델 히스토그램을 만들기 위해 충분히 다양한 피부톤의 이미지를 입력으로 사용하되, 피부톤이 흰색에 가까운 이미지는 제외한다. 이는 모델 히스토그램의 피부톤 범위를 더 크게 만들 것이며 인식단계에서의 false positive를 증가시킨다. 가령 베이지색 벽, 분홍색 옷들이 피부점으로 인식될 수 있다. loose하게 인식된 피부점들과 그 영역에 대해 얼굴로 판단할 수 있는 방법이 있어야 할것이다.
