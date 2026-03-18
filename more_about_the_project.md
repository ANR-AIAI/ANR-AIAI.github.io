---                      
layout: post             
title: More about the project 
---                      

# General objective

We aim to improve the integration of ice sheets into Earth System Models through the use of neural network emulators at the interfaces between the Antarctic ice sheet and the global atmosphere, and between Antarctic ice sheets and the global ocean. These will bring increased resolution and account for polar processes absent or poorly represented in Earth System Models. We will use this enhanced coupling framework to improve future projections of the Antarctic ice sheet contribution to global mean sea level rise by reducing uncertainties of both ocean-induced and atmosphere-induced variations in ice mass.

# Background and hypotheses

The sign of the Antarctic contribution to sea level rise over the 21st century has changed since the first IPCC (Intergovernmental Panel on Climate Change) assessment reports in which the ice sheet dynamics were assumed to be steady (Shepherd and Nowicki 2017). In the 2000s, satellite observations revealed that ice dynamics were changing faster than previously thought, prompting substantial improvements of ice sheet models in the following decades. For the first time, the 6th IPCC assessment report currently includes a likely range for the Antarctic contribution to sea level rise based on an ensemble of ice sheet simulations constrained by climate projections under various socio-economic pathways (Fox-Kemper et al. 2021).

The Antarctic contribution nonetheless remains the largest source of uncertainty in sea level projections, from nearly no contribution to sea level rise, to several tens of centimetres over the 21st century. The magnitude and sign of this contribution results from the compensation of two opposing effects: increased surface mass balance (SMB, i.e. the net balance between accumulation and ablation processes at the ice sheet surface) and increased ocean-induced dynamical ice mass loss, both of which are highly uncertain (Seroussi et al. 2020, Edwards et al. 2021). A large part of the uncertainty associated with these opposite effects comes from the absence of coupling between ice sheet and ocean/atmosphere models, which has motivated the recent development of such coupled models (e.g., Smith et al. 2021).

While these developments are a major step forward, a remaining challenge is the need for long integrations and large ensembles of simulations. These impose a coarse resolution of the ocean and atmosphere components even though small-scale processes are important in driving ice sheet evolution. For example, high basal melt rates on a thin fringe near the ice shelf grounding lines are the main cause of ocean-induced dynamical mass loss, and SMB and surface melt undergo large variations over the narrow topographic slope at the edge of ice sheets. Ice sheet models also need high resolution (typically 1km) near grounding lines and at their edge in order to correctly resolve the dynamics (Pattyn et al. 2012) and therefore often use unstructured or refined meshes, which makes them well suited to receive high-resolution ocean/atmosphere conditions.

Higher-resolution atmosphere and ocean models dedicated to polar environments can accurately represent the observed variability (Jourdain et al. 2017, Agosta et al. 2019), but their computational cost is prohibitive for climate applications. Deep learning methods, such as neural networks (NNs) that solve a complex non-linear regression problem between a set of input and output variables (Thuerey et al. 2021), can be trained to emulate the behaviour of polar-oriented high-resolution models at a much lower computing cost. While deep learning methods are now widely used in ocean and atmosphere sciences, they have not been used to refine the description of ocean–ice-sheet or atmosphere–ice-sheet interfaces so far. 

Our project is principally based on the following two hypotheses:

1. Neural networks trained on a large ensemble of high-resolution and polar-oriented simulations will improve the coupling between ice sheet models and coarse resolution ocean–atmosphere models.
2. Neural network emulators of SMB and ice-shelf melt can help reduce the uncertainty of the two opposing effects driving the Antarctic contribution to sea level, and hence help refine projections.

The products that will be developed are two trained neural networks that can be used at the atmosphere–ice-sheet and ocean–ice-sheet interfaces, and a new version of a global climate model in which the coupling interfaces will be enhanced by these neural networks. The expected results include revisited projections of the Antarctic surface mass balance as well as surface and ice-shelf basal melt rates. These will be compared with the results from the 6th phase of the Climate Model Intercomparison Project (CMIP6, Eyring et al. 2016) and the Ice Sheet Model Intercomparison Project for CMIP6 (ISMIP6, Nowicki et al. 2020), including its extension to 2300 (ISMIP6-2300). The final expected outcome is a demonstration that our methodology can be used for projections of Antarctic ice mass loss up to the year 2100.

# Approach and methodology

To fulfil our general objective and test our hypotheses, we will focus on the Antarctic ice sheet, through hindcasts of recent decades and scenario-based projections of the 21st century. We will further develop NN methods to derive high-resolution surface and basal ice-shelf melt as well as SMB from coarse-resolution climate models. We will use the neural networks to enrich the ice sheet coupling to a climate model. The strength of our proposal is that our consortium controls the entire modelling chain, from global climate model to regional components at higher resolution, and ice-sheet modelling. This is important both to design simulations that are fit-for-purpose for NN training and evaluation, and to embed the NNs within climate–ice-sheet models. The project is organised in five work packages (WPs) described further below. We first describe the tools used throughout the project.

### Neural networks (NN)

Simple NNs, at the grid scale level, provide encouraging preliminary results for ice-shelf basal melt patterns and variability (see 2nd proof of concept), but we plan to use convolutional NNs (CNN) throughout this project, in particular U-Net (Ronneberger et al. 2015; see also 1st proof of concept), to account for spatial structures in the input data. We will assess their skills with evolving ice sheet geometry, which was not done in our proofs of concept. We will also explore the use of physical constraints during the training stage (Thuerey at al. 2021). The NN will be trained and evaluated based on high-resolution simulations from polar-oriented models that are described hereafter (Fig. 1).

<div>
<img src="{{site.url}}img/more_fig1.png" width="60%" height="60%"/>
</div>

### Polar regional models used to train and evaluate NNs

The NN at the atmosphere–ice-sheet interface will emulate the behaviour of the MAR regional atmospheric model (Gallée and Schayes 1994, Agosta et al. 2019) at 35 km resolution. MAR is particularly suited for polar regions as it includes a multi-layer snow model, as well as cloud and turbulence parameterisations adapted to the very stable polar surface boundary layer. When driven by atmospheric reanalyses, MAR accurately captures the Antarctic surface mass balance and surface melt under present-day conditions in comparison to weather station and satellite data (Agosta et al. 2019, Donat-Magnin et al. 2020, Kittel et al. 2021). The surface mass balance produced by MAR is often used jointly with remote sensing data to estimate the past Antarctic contribution to sea level rise (e.g., Shepherd et al. 2018).

The NN at the ocean–ice-sheet interface will emulate the behaviour of a circum-Antarctic configuration of the NEMO (Nucleus for European Modelling of the Ocean, Madec et al. 2022) ocean–sea-ice model, including ice-shelf cavities (Mathiot et al. 2017). The corresponding ocean simulations must possess sufficient resolution of the ocean circulation features within ice-shelf cavities that are known to be key for the ice-sheet stability. To satisfy this, we choose the so-called NEMO-CircAnt-0.25° configuration, covering the Southern Ocean south of 55°S and the Antarctic marginal seas, including the under-ice-shelf seas. This model configuration is being developed for the CRiceS project. A resolution of 0.25° keeps numerical costs reasonable while permitting adequate representation of the main circulation in approximately 36 ice shelf cavities, including Pine Island, Thwaites and Totten, which are hot spots for the ice sheet stability (Burgard et al. 2022). When driven by atmospheric reanalyses, similar regional configurations accurately capture coastal ocean properties and ice-shelf basal melt rates (Jourdain et al. 2017; Haussmann et al. 2019).

While both MAR and NEMO-CircAnt-0.25° do have biases, we consider that they offer a huge improvement compared to the IPSL-CM6-LR simulations, in terms of resolution and processes.

### Climate and ice sheet models

Hindcasts and projections will be based on the IPSL-CM6-LR climate model, which includes, among others, the LMDZ atmospheric model at 157 km resolution and the NEMO ocean–sea-ice model at 1° resolution (Boucher et al. 2020). In the CMIP6 context, this climate model has been used to produce 32 ensemble members of the historical period (1850-2014), and multiple ensemble members to 2100 for a large range of emission scenarios, and to 2300 for a smaller subset of simulations. Our project will start by using the IPSL-CM6.0 model version, which has the advantage of having a large amount of available CMIP6 simulations, i.e. a large database for NN training and evaluation. We will nonetheless make our tools sufficiently flexible to adapt them to new versions of IPSL-CM when they become available.

The ice sheet model used will be Elmer/Ice (Gagliardini et al. 2013), with an Antarctic unstructured mesh of up to 1km resolution, and the shallow shelf approximation of the Stokes equations. Elmer/Ice has been coupled to idealised (Favier et al. 2019) and global (TiPACCs project) NEMO configurations and is being coupled to LMDZ through the ESM2025 project. The coupling is done every year through file exchange. Scripts applying the trained NN will be added at the model interfaces to derive high-resolution SMB and melt from the coarse ocean/atmosphere properties as summarised in Fig. 2.

<div>
<img src="{{site.url}}img/more_fig2.png" width="60%" height="60%"/>
</div>

### Project organization

The project covers 2023-2027 and is organized in four WPs:
* WP0 – Project Coordination 
* WP1 – Neural networks to derive ice-sheet surface conditions
* WP2 – Neural networks to derive ice-shelf basal conditions
* WP3 – Projections and uncertainty
