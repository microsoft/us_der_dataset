# Nationwide Distributed Energy Resource Modeling

Nationwide DER dataset for the contiguous US grid. We extend the synthetic model of the US power grid developed by Breakthrough Energy Sciences (BES) to include DERs aggregated up to each transmission node. We use publicly available data to model DER penetration across the US, with a primary focus on solar and storage. We include data on [utility-scale solar](data/utility_solar.csv), [small-scale distributed solar](data/distributed_solar.csv), and [battery storage](data/battery_storage.csv), all located in the distribution grid. With DERs integrated into the BES model, large scale impacts can be studied. To accompany the dataset and support continued research we have assembled a [Research Project Database](project_database.md), which leverages the integrated DER dataset and US grid model towards understanding pathways to deep decarbonization. Details of the integrated DER dataset and Research Project Database can be found in our paper: [Towards closing the data gap: A project-driven distributed energy resource dataset for the U.S. Grid](https://dl.acm.org/doi/10.1145/3599733.3600250).

To members of the research community: we look forward to collaborating with you to:
1. Use the dataset towards answering questions around decarbonization pathways such as those in the [Research Project Database](project_database.md) and sharing the findings widely
2. Enhancing the dataset with complimentary data sets (such as EVs, home batteries, charging networks, electrified heating networks, etc.)
3. Modeling efforts to include distribution system models in the U.S. grid model



<!--As the maintainer of this project, please make a few updates:
- Updating SUPPORT.MD with content about this project's support experience 
- Understanding the security reporting process in SECURITY.MD
--->



## Dataset description
The dataset includes the following files in the data folder
* Files without prefix: dataset of DER resources retrieved from existing publicly available data sources. The data was processed as described in [our paper](https://dl.acm.org/doi/10.1145/3599733.3600250), with geospatial information added.
* Prefix _integration_: dataset of DER resources with specified bus_id to integrate with the BES model. This dataset is a subset of the files above (i.e. without prefix), retaining only the resources that have the requisite information to map to a substation and bus in the BES model. Additionally, this dataset only retains a subset of the data fields which are necessary for modeling in the BES grid.
* [Lookup table](zip_to_latlong_lookup.csv) to convert zipcodes to latitude-longitude coordinates

The dataset additionally includes the following:
* [Research Project Database](project_database.md) which poses a series of questions to analyze pathways to deep decarbonization, using the integrated DER dataset and US grid model
* [Data schema](DATASCHEMA.md) description of the fields in each resource file, with additional links to more information from the original data repository

### Data Schema
Detailed data schema for each resource are presented [here](DATASCHEMA.md). The required information to integrate the DER resources into the BES grid model and simulation engine is as follows:
Data field name | Description | Data type, units, options
--- | --- | ---
id | Resource ID matching the DER datasets | String/Numeric
capacity_MW | Installed DC capacity for the resource | Numeric, MW
bus_id | ID of the specific bus to which the resource is connected | Numeric
branch_id | ID of the transmission branch to which the resource capacity is allocated | Numeric
sub_id | ID of the substation to which the resource is connected | Numeric
interconnect | Resource is connected to one of three U.S. grid interconnections | String: {Eastern, ERCOT, Texas}
state | U.S. State abbreviation | String, two letter abbreviation
ID_EIA | Identification number for EIA Form 860 (if applicable) | Numeric
hybrid_flag | Boolean flag indicating whether the resource is colocated with another resource type (ex. solar and storage hybrid resources) | Boolean: {True, False}

## Integration with the Breakthrough Energy Sciences model
### Adding DER resources to the BES model
Each resource can be added individually using the change tables, so the hourly operations for each resource can be viewed in the simulation results. Documentation for the change table operations can be found [in the BES documentation](https://breakthrough-energy.github.io/docs/powersimdata/index.html#creating-a-scenario). Multiple resources can be located at a single bus in the transmission grid model, with load and generation modeled separately. Note that new resources are represented using the same models and constraints as existing resources -- ex. DER solar resources will be modeled in the same way as transmission-level solar resources. The model can be extended to add additional capabilities, but is not easily done via the UI. 


### Breakthrough Energy Sciences model installation
Documentation for the BES model can be found as follows:
* [How profiles are generated](https://breakthrough-energy.github.io/docs/prereise/index.html#demand)
* [How constraints are modeled and operating decisions made](https://breakthrough-energy.github.io/docs/reisejl/index.html#formulation)

Guides for installation and setup can be found below:
* Main installation guide: https://breakthrough-energy.github.io/docs/user/installation_guide.html 
* Install some preliminary things (such as julia) as per: https://breakthrough-energy.github.io/docs/reisejl/installation.html
* This is helpful in setting up the virtual environment, and getting the jupyter notebook in VSCode to point to the virtual env: https://stackoverflow.com/questions/58119823/jupyter-notebooks-in-visual-studio-code-does-not-use-the-active-virtual-environm

Suggestions for package versions:
* Python 3.8 (so that PyJulia can work)
* Julia 1.5.3
* This is for version 0.5.1 of the requirements.txt file

Additional suggestions for installation and testing:
* The Dockerfile might also be a good reference for reproducing the environment
* If scenario state is going from prepared (all the files are in place to launch the simulation) to failed, likely that there is an error within the “engine” (referring to REISE.jl).
  - Try running scenario.check_progress() which should get any stdout produced by REISE.jl
  - Try running call.py directly (check with breakthrough team for support), which would rule out any issues invoking REISE.jl from PowerSimData
* Note: If you want to use a Gurobi license to run the simulation engine and are using a virtual machine (VM), the license for a single machine will be tied to the VM. If you reboot the VM, you will need to request a license transfer. Gurobi also has different licenses for Docker apps.


## Contact
Questions about the dataset and research project database can be directed to [Rabab Haider](https://www.rababhaider.me/) or [Weiwei Yang](https://www.microsoft.com/en-us/research/people/weiwya/).

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
