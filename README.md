# Brocade-OSPF
Brocade Rx8/ ICX7750 

interface create

config t
route-only (disables layer 2 switching)
rx8(config-ospf-router)# router ospf area area 14.0.0.0( ip address (or decimal area value default is 0)) virtual-link 14.0.0.1 md5-authentication key-id 255 key unencrypted password

int e 5/1 // Configured on 10 Gb SFP interface uplink to campus network
vlan 873
tagged eth 5/1
router-interface ve 873
ip address 14.0.0.10 255.255.255.0 
int ve873
ip ospf md5-authentication key-id 255 key (password)
ip ospf hello-interval 1
end

// router pim mode  and pim-sparse
config t

router pim
ip pim-sparse

end

