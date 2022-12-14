<div class="fluid-row" id="header">
    <img src='./misc/logo_geokarten.png' height='90' width='auto' align='right'>
    <h1 class="title toc-ignore">Pampa</h1>
    <h4 class="author"><em>Developed by  GeoKarten - schirmbeck.j@gmail.com</em></h4>
</div>

# About
This folder contains the scripts to classify and post-process the Pampa Biome.
 
We recommend that you read the MapBiomas Appendix of the Algorithm Theoretical Basis Document (ATBD).

# How to use
First, you need to copy these scripts  to your Google Earth Engine (GEE) account. To run these scripts, their  needs adjust to our data assets.
The process has been divided in 5 steps, this steps consist in:
* Step 1 - Prepare samples dataset to train Random Forest classifier.
* Step 2 - Classification by region, the Pampa Biome has been divided in 7 regions
* Step 3 - Post classification process
* Step 4 - Mosaic the pos classification images to obtain the biome map
* Step 5 - export the biome map in different images, one image per year.
# List of scripts:
# Prepare samples dataset to train Random Forest classifier.
* ***Step001A_gera_amostras_estaveis_coll_6.js***: export stable area maps for al time series            
* ***Step001B_gera_amostras_estaveis_coll_6_periodos.js***: export stable to four time intervals  
* ***Step001C_merge_estaveis_5_labGeo.js***: use reference map to leiter stable area maps                
* ***Step001D_exporta_pontos_estaveis.js***: apply à random selection on stable map to build the training dataset                
* ***Step001E_exporta_amostras_treinamento_anual_col7.js***: export annual mosaic information tho the training dataset built in previous step.

# Step 2 - Classification by region, the Pampa Biome has been divided in 7 regions
Te following sprits runing the random forest classification to the 7 Pampa regions:

* ***Step002_processa_regiao_01.js***                        
* ***Step002_processa_regiao_02.js***                        
* ***Step002_processa_regiao_03.js***                        
* ***Step002_processa_regiao_04.js***                        
* ***Step002_processa_regiao_05.js***                        
* ***Step002_processa_regiao_06.js***                        
* ***Step002_processa_regiao_07.js***                        

# Step 3 - Post classification process

* ***Step003_Filtro_01_gap_regiao_col07.js***: filter tho replace pixels classified as Non Observed;
* ***Step003_Filtro_02_espacial_regiao_col07.js***: this filter uses a mask to change only those patches with pixels connected to five or less pixels of the same class;

The following scripts runs the temporal filter, the first one is the generic filter, the next runs the temporal filter tho te specific regions. The temporal  filter uses the information from the previous year and the year later to identify and correct a pixel misclassification;
* ***Step003_Filtro_03_temporal_regiao_col07.js***           
* ***Step003_Filtro_03_temporal_regiao_col07_regiao2.js***   
* ***Step003_Filtro_03_temporal_regiao_col07_regiao3.js***   
* ***Step003_Filtro_03_temporal_regiao_col07_regiao6e7.js***

* ***Step003_Filtro_04_frequencia_regiao_multiplo_col07.js***: this filter were applied to use the temporal information available for each pixel to correct cases of false positives;

* ***Step003_Filtro_05b_prepara_incidentes_moda_col07.js***: prepare data to run incident filter;

* ***Step003_Filtro_05c_incidentes_e_floresta_col7.js* ***: this filter were applied to correct the classification of pixels considered with an excessive amount of changes along the 37 years;
* ***Step003_Filtro_07_espacial_regiao_pos_incidentes_col07.js***
* ***Step003_Filtro_07_temporal_regiao_pos_incidentes_col07.js***

# Step 4 - Mosaic the pos classification images to obtain the biome map
* ***Step004_mosaico_simplificado.js***                      

# Step 5 - export the biome map in different images, one image per year.
* ***Step005_exporta_por_ano.js***
