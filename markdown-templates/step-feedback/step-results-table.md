{%- set all_passed = (results_table | selectattr("passed") | length) == (results_table | length) %}

{%- if all_passed %}

## Step {{ step_number }} - Passed ✅

{%- else %}

## Step {{ step_number }} - Fail ❌

{%- endif %}

{%- if all_passed %}
<img src="https://octodex.github.com/images/inflatocat.png" align="right" height="150px" alt="Inflatocat image indicating the step passed" />
{%- else %}

<img src="https://octodex.github.com/images/spidertocat.png" align="right" height="100px" alt="Spidertocat image indicating the step failed" />
Alguna verificación ha fallado. Verifica los resultados e inténtalo de nuevo.

Es la hora de encontrar el error! 🤔
{%- endif %}

| Status | Description |
| ------ | ----------- |

{%- for row in results_table %}
| {% if row.passed -%}✅ - Pass{%- else -%}❌ - Fail{%- endif %} | {{ row.description }} |
{%- endfor %}

{%- if tips and tips.length %}

### Consejos

{%- for tip in tips %}

- {{ tip }}
  {%- endfor %}

{%- endif %}
