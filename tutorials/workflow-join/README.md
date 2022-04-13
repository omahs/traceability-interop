# Joining Workflow Instances

<img src="./workflow-instance-join.png"/>

This is an eCommerce business workflow which demonstrates joining two individual workflows into a common graph, leveraging workflow instance IDs. A total of three organizations collaborate in this scenario. Two organizations (_Importer_ and _Freight Forwarder_) first make individual presentations to a third org (_Customs_). When the correlation is realized, the workflows instances are joined with `["instance_1", "instance_2"]`.

## Business Focused Workflow Steps
The product importer of record (_Importer_) issues a Proforma Invoice (1) which is presented to _Customs_ with instance ID `["instance_1"]` well ahead of shipping (2). 

_Customs_ verifies the Proforma Invoice (3) from the _Importer_.

The _Importer_ issues the final Commercial Invoice (7) which is presented to the _Freight Forwarder_ (8), also with instance ID `["instance_1"]`.

Upon shipping, the _Freight Forwarder_ issues a House BL (4) which is presented (5) with instance ID `["instance_2"]`.
Passing on the Commercial Invoice (9), the _Freight Forwarder_ includes both its own and the Importer’s instance IDs `["instance_1", "instance_2"]`. 

_Customs_ verifies the House BL from the _Freight Forwarder_ (6). 
Receiving the Commercial Invoice (10), _Customs_ can also join the two graphs, thus knowing that the original Proforma Invoice relates to the _Freight Forwarder_’s presentations. 

