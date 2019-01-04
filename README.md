# RStudioConf2019
My presentation at RStudio::conf(2019), Austin, Tx - "The lazy and easily 
distracted report writer" on 18th January 2018.

# Aims
The example provided shows how you can use parameters with rmarkdown and knitr 
to produce reports for multiple outcomes.  

## Specifying parameters for knitr / rmarkdown
We're using a parameter passed into the 
report via the YAML header. This parameter can be set at time of rendering the 
report (using the `knit with parameters` option in the RStudio IDE, 
via "Inputs" specification in RStudio Connect or by specifying the parameters
and values within a list passed to the `params` argument of `rmarkdown:render`.

## Quantitative vs non-quantitative view
If the user sets the `quantAudience` parameter to `FALSE` then the code is hidden
in the rendered HTML, and certain text sections are hidden. To hide text we 
keep the relevant text in child documents and only bring these into the report
if the `quantAudience` parameter is set to `TRUE`. The code is entirely contained
in the parent document, but is executed depending on the setting of the parameter.

## Working with more than one outcome endpoint
The trick is to rename the outcome variables (and potentially associated 
variables with the same name e.g. HAMDTL17_BASE, HAMDTL17_CHG) to something 
generic i.e. `outcome` that will allow us to write code once and use it 
for each of the endpoint variables. We can then use the endpoint parameter 
`params$endpoint` to specify labels and names wherever these are needed. We
could also compute based on the value of `params$endpoint` if we need to do
specific things for each endpoint e.g. if one outcome is binary, rather than
continuous.
