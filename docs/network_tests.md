Bonding Tests
=============

network_tests.BondingTestClass.test_nic_bond_active_backup
----------------------------------------------------------
Bonding test between two VMs (one on each host). Must establish
that traffic fails over to the secondary interface.

   # Setup VMs
   # Setup Bond using active_backup mode (must include interface under test)
   # Start a ping between VMs
   # ifconfig down the first interface
   # ifconfig up the first interface, ifconfig down the second
   # Establish that 100% of traffic made the endpoint
   # Capture the ping output

network_tests.BondingTestClass.test_nic_bond_balance_slb
----------------------------------------------------------
Bonding test between two VMs (one on each host). Must establish
that traffic fails over to the secondary interface.

   # Setup VMs
   # Setup Bond using balanced_slb mode (must include interface under test)
   # Start a ping between VMs
   # ifconfig down the first interface
   # ifconfig up the first interface, ifconfig down the second
   # Establish that 100% of traffic made the endpoint
   # Capture the ping output



Dom0 performance tests
======================
For concisness, the following instructions are generalised. The test kit
runs a number of iperf tests, with particular configuration changes. 

Each test will indicate the specified offload configuration, and required
XenServer networking backened. 

   # Configure hardware offloads
   # Verify that XenServer the correct backend.
   # Setup iperf server in one dom0
   # Setup iperf client in the other dom0
   # Run iperf from client to server
      iperf -y csv -w 256K -l 256K -f m -P 4 -m -c <SERVER_IP>
   # Capture and label the results
   # Repeat the above steps, reversing server and client

network_tests.Dom0BridgePIFParamTestClass1
------------------------------------------
    
    BACKEND = 'Bridge'

    OFFLOAD_CONFIG = {'tx': 'on',                                         
                      'rx': 'on',                                         
                      'sg': 'on',                                         
                     'tso': 'on',                                        
                     'gso': 'on',                                        
                     'gro': 'off',                                       
                     'ufo': 'off',                                       
                     'lro': 'off',                                       
                  'rxvlan': 'off',                                    
                  'txvlan': 'off',                                    
                  'ntuple': 'off',                                    
                  'rxhash': 'off'}        


network_tests.Dom0BridgePIFParamTestClass2
------------------------------------------

    BACKEND = 'Bridge'

    OFFLOAD_CONFIG = {'tx': 'on',                                         
                      'rx': 'on',                                         
                      'sg': 'on',                                         
                     'tso': 'on',                                        
                     'gso': 'on',                                        
                     'gro': 'off',                                       
                     'ufo': 'off',                                       
                     'lro': 'off',                                       
                  'rxvlan': 'off',                                    
                  'txvlan': 'off',                                    
                  'ntuple': 'off',                                    
                  'rxhash': 'off'}        


network_tests.Dom0BridgePIFParamTestClass3
------------------------------------------

    BACKEND = 'Bridge'

    OFFLOAD_CONFIG = {'tx': 'on',                                         
                      'rx': 'on',                                         
                      'sg': 'on',                                         
                     'tso': 'on',                                        
                     'gso': 'on',                                        
                     'gro': 'on',                                       
                     'ufo': 'off',                                       
                     'lro': 'off',                                       
                  'rxvlan': 'off',                                    
                  'txvlan': 'off',                                    
                  'ntuple': 'off',                                    
                  'rxhash': 'off'}        

network_tests.Dom0PIFParamTestClass1
------------------------------------

    BACKEND = 'OVS'

    OFFLOAD_CONFIG = {'tx': 'on',                                         
                      'rx': 'on',                                         
                      'sg': 'on',                                         
                     'tso': 'on',                                        
                     'gso': 'on',                                        
                     'gro': 'off',                                       
                     'ufo': 'off',                                       
                     'lro': 'off',                                       
                  'rxvlan': 'off',                                    
                  'txvlan': 'off',                                    
                  'ntuple': 'off',                                    
                  'rxhash': 'off'}        


network_tests.Dom0PIFParamTestClass1
------------------------------------

    BACKEND = 'OVS'

    OFFLOAD_CONFIG = {'tx': 'on',                                         
                      'rx': 'on',                                         
                      'sg': 'on',                                         
                     'tso': 'on',                                        
                     'gso': 'on',                                        
                     'gro': 'off',                                       
                     'ufo': 'off',                                       
                     'lro': 'off',                                       
                  'rxvlan': 'off',                                    
                  'txvlan': 'off',                                    
                  'ntuple': 'off',                                    
                  'rxhash': 'off'}        

network_tests.Dom0PIFParamTestClass2
------------------------------------

    BACKEND = 'OVS'

    OFFLOAD_CONFIG = {'tx': 'on',                                         
                      'rx': 'on',                                         
                      'sg': 'on',                                         
                     'tso': 'on',                                        
                     'gso': 'on',                                        
                     'gro': 'off',                                       
                     'ufo': 'off',                                       
                     'lro': 'off',                                       
                  'rxvlan': 'off',                                    
                  'txvlan': 'off',                                    
                  'ntuple': 'off',                                    
                  'rxhash': 'off'}        

network_tests.Dom0PIFParamTestClass3
------------------------------------

    BACKEND = 'OVS'

    OFFLOAD_CONFIG = {'tx': 'on',                                         
                      'rx': 'on',                                         
                      'sg': 'on',                                         
                     'tso': 'on',                                        
                     'gso': 'on',                                        
                     'gro': 'on',                                       
                     'ufo': 'off',                                       
                     'lro': 'off',                                       
                  'rxvlan': 'off',                                    
                  'txvlan': 'off',                                    
                  'ntuple': 'off',                                    
                  'rxhash': 'off'}        


network_tests.Dom0VMBridgeIperfTestClass
----------------------------------------
Same as the above, Dom0PIFParamTestClass1 except the test is run in both
directions between Dom0 and a Droid VM. (Template provided in kit).

    BACKEND = 'Bridge'

network_tests.Dom0VMIperfTestClass
----------------------------------
Same as the above, Dom0PIFParamTestClass1 except the test is run in both
directions between Dom0 and a Droid VM. (Template provided in kit).

    BACKEND = 'OVS'

network_tests.IperfTestClass
----------------------------
Same as the above, Dom0PIFParamTestClass1 except the test is run in both
directions between two Droid VM. (Template provided in kit).

    BACKEND = 'OVS'

MTU Tests
=========

network_tests.MTUPingTestClass
------------------------------
This test is designed to ensure that the network card handles large MTU
packets.

    # Create two Droid VMs (on per host)
    # Configure MTU on VIFs, Dom0 interface and VM interface.
    # Run a ping between source VM and destination (over test interface)
        ping -I <INTERFACE> -s 8000 -c 20 -M do <DEST IP>
    # Verify success and capture the results for submission.

VLAN Tests
===============

network_tests.VLANTestClass.test_vlan_high_port
-----------------------------------------------
Test designed to verify that the network card handles VLANs with the OVS
correctly.

    # Setup a VLAN network using the adator which is being tested
    # Configure the switch for VLANs
    # Spin up two Droid VMs, one on each host
    # Create a second interface that is connected to the VLAN network on each.
    # Run a ping command between them
        ping -I eth1 <ETH1 on DEST VM>
    # Verify the results and include in submission.
