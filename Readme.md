## 1 1)>>> import pandas as pd 2)>>> import folium 3)>>> import webbrowser ##1. 데이터 시각화를 하기 위해 필요한 folium,pandas,webbrowser 라이브러리를 import한다.

## 2.>>> state_geo = ("c:/TL_SCCO_SIG_WGS84.json")

### 2. 로컬디스크 c에 있는 json파일을 state_geo라는 이름으로 지정한다.

## .3>>> state_unemployment = ("c:/Total_People_2019.csv")

### 3. 로컬디스크 c에 있는 보정한 csv파일을 state_unemployment라는 이름으로 지정한다.

## 4.>>> state_data = pd.read_csv(state_unemployment, encoding = 'euc-kr') ##4. ("c:/Total_People_2019.csv")를 읽어주는데 encoding = 'euc-kr'를 꼭해야한다. encoding = 'euc-kr'를 하지 않았을때 오류가 발생한다. 읽은 csv를 state_data로 지정한다.

## 5.>>> m = folium.Map(location=[36, 127], tiles="OpenStreetMap", zoom_start=7)

### 5. location은 대한민국을 표시할 위도,경도를 나타낸다. tiles는 OpenStreetMap이라는 개방형 라이선스에서 사용할 수 있는 곳이다. zoom_start는 수업시간에 배운걸 썼습니다.

## .6>>> 1)m.choropleth( geo_data=state_geo, name='choropleth', data=state_data, columns=['Code', 'Population'], key_on='feature.properties.SIG_CD', fill_color='YlGn', fill_opacity=0.7, line_opacity=0.5, legend_name='Population Rate (%)' ) 2)Warning (from warnings module): File "C:\Users\user\AppData\Local\Programs\Python\Python38-32\lib\site-packages\folium\folium.py", line 411 warnings.warn( FutureWarning: The choropleth method has been deprecated. Instead use the new Choropleth class, which has the same arguments. See the example notebook 'GeoJSON_and_choropleth' for how to do this.

### 3)>>> m.choropleth( geo_data=state_geo, name='choropleth', data=state_data, columns=['Code', 'Population'], key_on='feature.properties.SIG_CD', fill_color='YlGn', fill_opacity=0.7, line_opacity=0.5, legend_name='Population Rate (%)' ) ##6. 코드를 실행하면 Warning이 나옵니다. 왜 Warning이 나오는지는 아직도 잘모르겠습니다. 그런데 신기하게 한번더 코드를 실행하면 됩니다. choropleth는 시군 등의 단위지역으로 구성된 지역을 통계량의 크기로 나타내는 부호이다. geo_data는 json파일은 state_geo로 지정 이름은 그냥 choropleth로 했습니다. data는 csv파일은 state_data columns는 csv파일에 1행에 있는 것을 지정 해주어야 에러가 뜨지 않았습니다. key_on는 json파일과 csv파일을 매칭할때 데이터를 지정하는 곳입니다. fill_color는 지도를 잘 나타내기 위한 YlGn로 했습니다. fill_opacity, line_opacity는 투명도를 나타내서 가장 적단한 수로 했습니다. legend_name 는 웹페이지가 나타날때 인구수당 짙음을 나타내는 정도를 보여주는 제목입니다.

## .7 1)>>> folium.LayerControl().add_to(m) 2)>>> m.save("c:/크롤링과제") 3)>>> webbrowser.open_new("c:/크롤링과제") ##7 로컬디스크c에 "크롤링과제"로 저장합니다. 웹브라우저를 실행하여 결과물을 웹페이지로 확인합니다.
