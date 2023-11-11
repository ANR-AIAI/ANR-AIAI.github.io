---
layout: default
---

<div>
<img src="{{site.url}}img/baniere_3.jpg" width="100%" height="100%"/>
</div>

<br>

{::nomarkdown}
<TABLE WIDTH=100%>
  <TR VALIGN=TOP>
    <TD WIDTH=40% STYLE="border-top: none; border-bottom: none; border-left: none; border-right: none; padding: 0.1cm 0cm"><P><img src="{{site.baseurl}}/img/logo_AIAI_final_text.jpg" width="100%" height="100%" style="float: left;" /></P></TD>
    <TD WIDTH=60% STYLE="border-top: none; border-bottom: none; border-left: none; border-right: none; padding: 0.1cm 0cm">
      <P><b>Artificial Intelligence to improve the coupling between the Antarctic ice sheet and the ocean/atmosphere system (AIAI)</b><br> <br>Funded by the French National Agency for Research (ANR) over 2023-2027<br><img src="{{site.baseurl}}/img/ANR-logo-2021-sigle.jpg" width="10%" height="10%" style="float: none;" /> </P>
    </TD>
  </TR>
</TABLE>
{:/}

## Project objectives
This project aims to improve the integration of ice sheets into Earth System Models through the use of neural network emulators at the interfaces between the Antarctic ice sheet and the global atmosphere, and between Antarctic ice sheet and the global ocean. These will bring increased resolution and account for polar processes absent or poorly represented in Earth System Models. We will use this enhanced coupling framework to improve future projections of the Antarctic ice sheet contribution to global mean sea level rise by reducing uncertainties of both ocean-induced and atmosphere-induced variations in ice mass.

## News
{% for post in site.posts %}
   - {{ post.date | date_to_string }} » [{{ post.title }}]({{ site.baseurl }}{{ post.url }})
{% endfor %}
