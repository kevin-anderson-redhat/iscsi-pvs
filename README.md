# iscsi-pvs
OpenShift iscsi physical volumes are created using the pv?.yaml files.
Note that each pv is using a unique initiator name.

There are currently 6 LUNs provided by the target (we only use 3) 
The NetApp in this case provides two iscsi portals to the volumes (two heads)

We have 3 infra nodes and use selectors to place an elasticsearch pod on each infra node.

Initial deployment of cluster logging associates an initiator with each infra node.

Question 1 - What happens if we try to vacate an infra node (assuming the other infra nodes have enough resources to host 2 elastic search pods and associated additioinal loads?  Will the node running 2 ES pods use two iscsi initiators?  What happend to the nodes /dev/sd?  

Question 2 - Will monitoring work using a similar scema? Define 2 more physical volumes for monitoring using 2 more of the 6 LUNs but use unique initiator names (named monitoring instead of logging).

##Additional
- Using two ports consumes two block devices on the node.  There is a device limit, what is it?
- Is best practice to use one initiator name?
            


