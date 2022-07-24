# Global Catalog

A Global Catalog server is a domain controller that stores copies of all Active Directory objects in the forest. It stores a complete copy of all objects in the directory of your domain and a partial copy of all objects of all other forest domains. Thus, the Global Catalog allows users and applications to find objects in any domain of the current forest by searching for attributes included to GC. 

The Global Catalog contains a basic (but incomplete) set of attributes for each forest object in each domain (Partial Attribute Set, PAT). The GC receives data from all the domain directory partitions in the forest, they are copied using the standard AD replication service. Whether the attribute is copied to the Global Catalog is determined by the schema. If necessary, you can configure additional attributes that will be replicated to the GC using the Active Directory Schema snap-in. To add an attribute to the GC, you must select the option Replicate This Attribute To The Global catalog. As a result, the value of the isMemberOfPartialAttributeSet attribute parameter is set to true. 

* * * 

### References  
- https://theitbros.com/global-catalog-active-directory/ 
- https://youtu.be/v0G2u_XUrwk

 


