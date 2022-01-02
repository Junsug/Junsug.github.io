---
title: Plotly template 적용
category: Data analysis
tag : visualization
toc : true
toc_sticky : true
toc_label : 목차
author_profile : false
---

Plotly 템플릿 바꿔보자

## 기본 Scatter 그래프

```python
fig = px.scatter(gapminder_1997, x="gdpPercap", y="lifeExp", size = 'pop', color = 'continent',
                 hover_name = 'country', log_x=True, size_max = 50)
fig.update_layout(legend=dict(orientation='h', yanchor='bottom',y=1, xanchor='right',x=1))
fig.show()
```
{% include posts/plotly/2/2-1.html %}

## template 종류를 알아보자

```python
import plotly.io as pio
pio.templates
```
> Templates configuration <br>
  Default template: 'plotly' <br>
  Available templates:
  ['ggplot2', 'seaborn', 'simple_white', 'plotly',
   'plotly_white', 'plotly_dark', 'presentation', 'xgridoff',
   'ygridoff', 'gridon', 'none']

하나씩 살펴보자
```python
for template in ["plotly", "plotly_white", "plotly_dark", "ggplot2", "seaborn", "simple_white", "none"]:
    fig = px.scatter(gapminder_1997, x="gdpPercap", y="lifeExp", size = 'pop', color = 'continent',
                     hover_name = 'country', log_x=True, size_max = 50,
                     template=template, title="'%s' theme" % template)
    fig.update_layout(legend=dict(orientation='h', yanchor='bottom',y=1, xanchor='right',x=1))
    fig.show()
```
{% include posts/plotly/2/plotly.html %}
{% include posts/plotly/2/plotly_white.html %}
{% include posts/plotly/2/plotly_dark.html %}
{% include posts/plotly/2/ggplot2.html %}
{% include posts/plotly/2/seaborn.html %}
{% include posts/plotly/2/simple_white.html %}
{% include posts/plotly/2/none.html %}

## default값 변경
나는 simple_white가 제일 마음에 든다
```python
pio.templates.default = "simple_white"
```
```python
fig = px.scatter(gapminder_1997, x="gdpPercap", y="lifeExp", size = 'pop', color = 'continent',
                 hover_name = 'country', log_x=True, size_max = 50)
fig.update_layout(legend=dict(orientation='h', yanchor='bottom',y=1.01, xanchor='right',x=1))
fig.update_xaxes(showgrid=True, mirror=True) 
fig.update_yaxes(showgrid=True, mirror=True)
fig.show()
```
{% include posts/plotly/2/2-2.html %}

끝.