# Network_Verification

## Header Space Library.  

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
    10) You can loop around reachablity code from port-map to check reachability between different combination of nodes. 
    11) Optional/Example: We can check reachability through the exmaples folder in hassel-c. Go to /hassel-c/examples/stanford.
    12) Optional/Example: Run python run_loop_detection_su_bb.py.
        This will run loop detection on the stanford tf file. 


## Netplumber.  

Follow-up access instructions for this library are as follows

    1) Go to hassel-c directory.
    2) Go to netplumbing
        We can run netplumber on MacOS (again because of .so file.) as seen above in the headerspace library. Note that I have changed the utils folder with my own binaries, so if you directly skip to this step, it will work if you are on Mac environment. 
    3) We can use the test_net_plumber.py file to test new networks.
        The file allows for adding/deleting nodes and links to a network. Netplumber will check loops and blackholes in the resulting network upon addition of links. We cannot check the network for slicing because there will always be a slice when you begin constructing a network.   
    4) We can run the file through python test_net_plumber.py
    5) We can also run topologies through testing.py file. 
   
## Acknowledgements:
This is my attempt at working with the Header Space Library, published at https://bitbucket.org/peymank/hassel-public/src by Peyman Kazemian. 
 
