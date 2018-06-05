{%- if page.category != "" -%}

{%- assign temppage = "" -%}
{%- assign prevpage = "" -%}
{%- assign nextpage = "?" -%}

{%- assign thispage = page.path -%}

{%- assign xrawcats = "" -%}
{%- for page in site.pages -%}
  {%- assign xtcats = page.category | join:'|' | append:'|' -%}
  {%- assign xrawcats = xrawcats | append:xtcats -%}
{%- endfor -%}

{%- assign xrawcats = xrawcats | split:'|' | sort -%}

{%- assign xcats = "" -%}

{%- for cat in xrawcats -%}
  {%- if cat != "" -%}

    {%- if xcats == "" -%}
      {%- assign xcats = cat | split:'|' -%}
    {%- endif -%}

    {%- unless xcats contains cat -%}
    {%- assign xcats = xcats | join:'|' | append:'|' | append:cat | split:'|' -%}
    {%- endunless -%}
  {%- endif- %}
{%- endfor -%}



{% for ct in xcats %}
  {%- assign xsorted = site.pages | sort: 'title' -%}
  {%- for page in xsorted -%}
    {%- if page.category contains ct %}
      {%- if nextpage=="" -%}
        {%- assign nextpage = page.path -%}
      {%- endif -%}
      {%- if thispage == page.path -%}
        {%- assign prevpage = temppage -%}
        {%- assign nextpage = "" -%}
      {%- endif -%}
      {%- assign temppage = page.path  -%}
    {%- endif -%}
  {%- endfor %}
{% endfor -%}



{% if prevpage != "" %}
  <p><a href="{{ prevpage | replace: '.md','' }}">previous</a></p>
{% endif %}
{% if nextpage != ""  and nextpage != "?"%}
  <p><a href="{{ nextpage | replace: '.md','' }}">next</a></p>
{% endif %}

{%- endif -%}

