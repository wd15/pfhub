---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.14.2-dev
  kernelspec:
    display_name: Python 3 (ipykernel)
    language: python
    name: python3
---

```python papermill={"duration": 0.013269, "end_time": "2023-03-15T16:00:43.720640", "exception": false, "start_time": "2023-03-15T16:00:43.707371", "status": "completed"} tags=["parameters"]
benchmark_id = '3a.1'
line_plots = [
    dict(name='free_energy', layout=dict(log_y=True, x_label=r'<i>t</i>', y_label=r'&#8497;', range_y=[1.8e6, 2.4e6], title="Free Energy v Time")),
    dict(name='solid_fraction', layout=dict(log_y=True, x_label=r'<i>t</i>')),
    dict(name='tip_position', layout=dict(log_y=True, x_label=r'<i>t</i>')),
    dict(name='phase_field_1500', layout=dict(aspect_ratio=1.0))
]
contour_plots = []
```

```python papermill={"duration": 0.010319, "end_time": "2023-03-15T16:00:43.733675", "exception": false, "start_time": "2023-03-15T16:00:43.723356", "status": "completed"} tags=["injected-parameters"]
# Parameters
benchmark_id = "4g.1"
line_plots = [
    {
        "name": "all_data",
        "layout": {
            "x_label": "Fictive Time, <i>t</i><sub>aim</sub>&nbsp;[a.u.]",
            "y_label": "Free Energy, &#8497;&nbsp;[aJ]",
            "title": "",
            "log_x": True,
        },
    },
    {
        "name": "all_data",
        "columns": ["time", "elastic_free_energy"],
        "layout": {
            "x_label": "Fictive Time, <i>t</i><sub>sim</sub>&nbsp;[a.u.]",
            "y_label": "Elastic Free Energy, &#8497;&nbsp;[aJ]",
            "title": "",
            "log_x": True,
        },
    },
    {
        "name": "all_data",
        "columns": ["time", "a_10"],
        "layout": {
            "x_label": "Fictive Time, <i>t</i><sub>sim</sub>&nbsp;[a.u.]",
            "y_label": "Precipitate Length, <i>a</i><sub>10</sub>&nbsp;[nm]",
            "title": "",
            "log_x": True,
        },
    },
    {
        "name": "all_data",
        "columns": ["time", "a_01"],
        "layout": {
            "x_label": "Fictive Time, <i>t</i><sub>sim</sub>&nbsp;[a.u.]",
            "y_label": "Precipitate Length, <i>a</i><sub>01</sub>&nbsp;[nm]",
            "title": "",
            "log_x": True,
        },
    },
    {
        "name": "all_data",
        "columns": ["time", "a_d"],
        "layout": {
            "x_label": "Fictive Time, <i>t</i><sub>sim</sub>&nbsp;[aJ]",
            "y_label": "Precipitate Length, <i>a</i><sub>d</sub>&nbsp;[nm]",
            "title": "",
            "log_x": True,
        },
    },
    {
        "name": "all_data",
        "columns": ["time", "elastic_free_energy"],
        "layout": {
            "x_label": "Fictive Time, <i>t</i><sub>sim</sub>&nbsp;[a.u.]",
            "y_label": "Normalized Elastic Energy, <i>g</i><sub>el</sub><sup>avg</sub>&nbsp;[aJ/nm<sup>2</sup>]",
            "title": "",
            "log_x": True,
        },
    },
    {
        "name": "contour",
        "layout": {
            "title": "Precipitate Boundary at Equilibrium",
            "log_x": True,
            "x_label": "x, [nm]",
            "y_label": "y, [nm]",
            "aspect_ratio": 1.0,
        },
    },
]

```

```python papermill={"duration": 0.011874, "end_time": "2023-03-15T16:00:43.748161", "exception": false, "start_time": "2023-03-15T16:00:43.736287", "status": "completed"} tags=[]
from IPython.display import display_markdown

display_markdown(f'''
# Benchmark { benchmark_id } Results

All results for the [{ benchmark_id } benchmark specification](../../benchmarks/benchmark{ benchmark_id }.ipynb/).
''', raw=True)
```

```python papermill={"duration": 0.008966, "end_time": "2023-03-15T16:00:43.759860", "exception": false, "start_time": "2023-03-15T16:00:43.750894", "status": "completed"} tags=[]
# To generate the comparison notebooks use:
# 
# papermill template.ipynb benchmark{version}.ipynb -f bm{version}.yaml
#
```

```python papermill={"duration": 0.016008, "end_time": "2023-03-15T16:00:43.780135", "exception": false, "start_time": "2023-03-15T16:00:43.764127", "status": "completed"} tags=[]
from IPython.display import HTML

HTML('''<script>
code_show=true; 
function code_toggle() {
 if (code_show){
 $('div.input').hide();
 $('div.prompt').hide();
 } else {
 $('div.input').show();
$('div.prompt').show();
 }
 code_show = !code_show
} 
$( document ).ready(code_toggle);
</script>
<form action="javascript:code_toggle()"><input type="submit" value="Code Toggle"></form>''')
```

```python papermill={"duration": 0.695986, "end_time": "2023-03-15T16:00:44.478762", "exception": false, "start_time": "2023-03-15T16:00:43.782776", "status": "completed"} tags=[]
#from IPython.display import HTML, display
#from time import sleep

#display(HTML("""
#<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
#"""))

#sleep(0.1)

from IPython.display import HTML, display, display_markdown
from time import sleep

#import logging
#logging.basicConfig(format='%(asctime)s - %(message)s', level=logging.DEBUG)

display(HTML("""
<script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
"""))

sleep(0.1)


from pfhub.main import line_plot, levelset_plot, get_table_data_style, plot_order_of_accuracy, get_result_data, efficiency_plot
#import itables.interactive
from itables import init_notebook_mode

init_notebook_mode(all_interactive=False)
```

```python papermill={"duration": 12.118913, "end_time": "2023-03-15T16:00:56.600636", "exception": false, "start_time": "2023-03-15T16:00:44.481723", "status": "completed"} tags=[]
for x in line_plots:
    line_plot(
        data_name=x['name'],
        benchmark_id=benchmark_id,
        layout=x['layout'],
        columns=x.get('columns', ('x', 'y'))
    ).show()
```

```python papermill={"duration": 0.073612, "end_time": "2023-03-15T16:00:56.738583", "exception": false, "start_time": "2023-03-15T16:00:56.664971", "status": "completed"} tags=[]
for x in contour_plots:
    data = get_result_data([x['name']], [benchmark_id], x['columns'])

    levelset_plot(
        data,
        layout=x['layout'],
        mask_func=lambda df: (x['mask_z'][0] < df.z) & (df.z < x['mask_z'][1]),
        columns=x['columns']
    ).show()
```

```python papermill={"duration": 2.605523, "end_time": "2023-03-15T16:00:59.417327", "exception": false, "start_time": "2023-03-15T16:00:56.811804", "status": "completed"} tags=[]
efficiency_plot(benchmark_id).show()

display_markdown("<span class='plotly-footnote' >* Wall time divided by the total simulated time.</span>", raw=True)

```

```python papermill={"duration": 0.078242, "end_time": "2023-03-15T16:00:59.578687", "exception": false, "start_time": "2023-03-15T16:00:59.500445", "status": "completed"} tags=[]
display_markdown(f'''
# Table of Results

Table of { benchmark_id } benchmark result uploads.
''', raw=True)
```

```python papermill={"duration": 0.060515, "end_time": "2023-03-15T16:00:59.702434", "exception": false, "start_time": "2023-03-15T16:00:59.641919", "status": "completed"} tags=[]

```

```python papermill={"duration": 1.137161, "end_time": "2023-03-15T16:01:00.897734", "exception": false, "start_time": "2023-03-15T16:00:59.760573", "status": "completed"} tags=[]
## Currently switching off interactive tables as these are not converted to HTML properly.
## This might improve when jupyter-nbcovert is updated to a later version.

init_notebook_mode(all_interactive=False)
get_table_data_style(benchmark_id, pfhub_path='../..')
```

```python papermill={"duration": 0.054038, "end_time": "2023-03-15T16:01:01.009197", "exception": false, "start_time": "2023-03-15T16:01:00.955159", "status": "completed"} tags=[]

```