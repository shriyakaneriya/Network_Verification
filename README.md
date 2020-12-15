# Network_Verification

Header Space Library.  

The access instruction for this library are as follows:

    1) Go to hsa-python directory.
    2) Run setup.sh
    3) Add the directory to PYTHONPATH. 
        [generate network on MAC because widlcard-*.so is compatible to Mac through config parser]  
        Note: This will not work for iOS users. This is because the PYTHONPATH cannot be changed permanently. 
        As a solution, do not close the terminal while you finish the work. 
        iOS COMMANDS:
            PYTHONPATH="/location/of/hsa_python:$PYTHONPATH"
            export PYTHONPATH
            
        Also, for mac, you will have to re-run setup.sh after updating PYTHONPATH.
        Also, everything is in Python 2.xx
        
    4) Go to config parser and run: python cisco_router_parser.py
        
        Input: The config parser takes in the following files from Cisco IOS as input. They can be obtained as for any topology created with :
        - arp_table : sh arp
        - rtr_config : sh ip ce
        - rtr_mac_table : sh mac-address-tabl
        - rtr_route : sh run
        - rtr_spanning_tree : sh spanning-tree
        Change your input in the file. 
        
    5) The .tf file that is generated is to be transferred to /hassel-c/tfs/
    6) When adding a new network, cp src/apps/stanford.c src/apps/<network>.c.
    7) Go to hassel-c. Compile the Makefile using make.
       Note: run Make on Linux machines, because Mac doesnt support PTHREAD in GNU. Thus the library would not compile for me on Mac.
       
    8) Run ./gen <network> [reads transfer functions from tfs/<network>/* and creates the data file data/<network>.dat => confirm this]
    9) Run ./<network> <source_port> <dest_port> or ./<network> <source_port> [<dest_port1>, <dest_port1>, ..] etc.




loop around reachablity code from port-map to check the possibility. 



We can run netplumber on MacOS (again because of .so file.) 
Make sure you change the utils folder. 
