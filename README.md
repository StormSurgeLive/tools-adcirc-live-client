
# README

This repository is the home of the Official commandline client and reference
client library implemention for the SaaS features and APIs available for users
of http://tools.adcirc.live.

# State of Client

This is a work in progress. For more information, feel free to email us at
hello@support.adcirc.live

## Supported Calls:

Note: an account and API key/secret is required from https://tools.adcirc.live.

### List Supported Meshes

```
  $ ./bin/adclive meshes
  
  [{"nodes":22425,"elements":41330,"name":"APES"},{"nodes":32218,"name":"BeaufortInlet","elements":58641},{"name":"EC2001","elements":492179,"nodes":254565},{"elements":3770720,"name":"EC2012","nodes":2066216},{"name":"EC95d","elements":58369,"nodes":31435},{"elements":3564104,"name":"HSOFS","nodes":1813443},{"name":"NAC2014","elements":6167588,"nodes":3110470},{"name":"NCv6d","elements":575512,"nodes":295328},{"nodes":2249093,"elements":4480230,"name":"SFLv111"},{"name":"Shinnecock","elements":5780,"nodes":3070},{"nodes":3352598,"elements":6675517,"name":"TX2008"},{"nodes":417642,"name":"ULLR2D","elements":826866}]APES             (22425    nodes, 41330    elements)
```

```
  $ ./bin/adclive meshes --as list
  
  BeaufortInlet    (32218    nodes, 58641    elements)
  EC2001           (254565   nodes, 492179   elements)
  EC2012           (2066216  nodes, 3770720  elements)
  EC95d            (31435    nodes, 58369    elements)
  HSOFS            (1813443  nodes, 3564104  elements)
  NAC2014          (3110470  nodes, 6167588  elements)
  NCv6d            (295328   nodes, 575512   elements)
  SFLv111          (2249093  nodes, 4480230  elements)
  Shinnecock       (3070     nodes, 5780     elements)
  TX2008           (3352598  nodes, 6675517  elements)
  ULLR2D           (417642   nodes, 826866   elements)
  
  tip: use "--as json" to get list in JSON for more flexible processing
```

### Static XDMF for Paraview Visualization

```
  $ ./bin/adclive xdmf --mesh TX2008 --paraview 5.9.1 --adcirc v53.01 --maxele --maxvel --maxwvel --minpr --maxrs --swanhsmax --swantpsmax --as stdout 

  <?xml version="1.0" encoding="utf-8" ?>
  <Xdmf xmlns:xi="http://www.w3.org/2001/XInclude" Version="2.1">
  <!--
  This XML file was generated by the adcirc.live web application at 
  https://tools.adcirc.live/spa/paraview/XDMF 
  
  For more information, please visit us at https://tools.adcirc.live,
  have a look at our training courses at https://courses.adcirc.live,
  or contact us at . 
  
  This xml file was generated for the TX2008 mesh (3352598 vertices
  and 6675517 elements) for use in Paraview (version 5.9.1 on
  Monday, January 29, 2024 for the following ADCIRC (version v53.01)
  files: 
  
  Information Summary about this file,
  
  Mesh                  : TX2008 ( 3352598 nodes, 6675517 elements )
  ADCIRC                : v53.01
  Paraview              : 5.9.1
  
  Contains description for the following ADCIRC
  data files:
  
    * maxele.63.nc
    * maxwvel.63.nc
    * maxvel.63.nc
    * minpr.63.nc
    * maxrs.63.nc
    * swan_HS_max.63.nc
    * swan_TPS_max.63.nc
  -->
    <Domain Name="TX2008">
      <Grid GridType="Uniform">
        <Topology Name="ADCIRCMesh"
          TopologyType="Triangle"
          NodesPerElement="3"
          NumberOfElements="6675517"
          BaseOffset="1">
           <DataItem Dimensions="6675517  3"
             DataType="Int"
             Format="HDF">maxele.63.nc:/element
           </DataItem>
        </Topology>
        <Geometry Name="NodeLocations"
          GeometryType="X_Y">
           <DataItem Dimensions="3352598"
              NumberType="Float"
              Precision="8"
              Format="HDF">maxele.63.nc:/x
           </DataItem>
           <DataItem Dimensions="3352598"
             NumberType="Float"
             Precision="8"
             Format="HDF">maxele.63.nc:/y
           </DataItem>
        </Geometry>
        <Attribute Name="BathymetricDepth"
          AttributeType="Scalar"
          Center="Node">
           <DataItem Dimensions="3352598"
             NumberType="Float"
             Precision="8"
             Format="HDF">maxele.63.nc:/depth
           </DataItem>
        </Attribute>
  
        <!-- maxele.63.nc -->
        <Attribute Name="maximum_sea_surface_height_above_geoid"
          Center="Node"
          AttributeType="Scalar">
           <DataItem Dimensions="3352598"
             NumberType="Float"
             Precision="8"
             Format="HDF">maxele.63.nc:/zeta_max
           </DataItem>
        </Attribute>
        <Attribute Name="time_of_maximum_sea_surface_height_above_geoid"
          Center="Node"
          AttributeType="Scalar">
           <DataItem Dimensions="3352598"
             NumberType="Float"
             Precision="8"
             Format="HDF">maxele.63.nc:/time_of_zeta_max
           </DataItem>
        </Attribute>
  
        <!-- maxwvel.63.nc      -->
        <Attribute Name="maximum_wind"
          Center="Node"
          AttributeType="Scalar">
           <DataItem Dimensions="3352598"
             NumberType="Float"
             Precision="8"
             Format="HDF">maxwvel.63.nc:/wind_max
           </DataItem>
        </Attribute>
        <Attribute Name="time_of_maximum_wind"
          Center="Node"
          AttributeType="Scalar">
           <DataItem Dimensions="3352598"
             NumberType="Float"
             Precision="8"
             Format="HDF">maxwvel.63.nc:/time_of_wind_max
           </DataItem>
        </Attribute>
  
        <!-- maxvel.63.nc       -->
        <Attribute Name="maximum_water_velocity"
          Center="Node"
          AttributeType="Scalar">
           <DataItem Dimensions="3352598"
             NumberType="Float"
             Precision="8"
             Format="HDF">maxvel.63.nc:/vel_max
           </DataItem>
        </Attribute>
        <Attribute Name="time_of_maximum_water_velocity"
          Center="Node"
          AttributeType="Scalar">
           <DataItem Dimensions="3352598"
             NumberType="Float"
             Precision="8"
             Format="HDF">maxvel.63.nc:/time_of_vel_max
           </DataItem>
        </Attribute>
  
        <!-- minpr.63.nc        -->
        <Attribute Name="minimum_air_pressure_at_sea_level"
          Center="Node"
          AttributeType="Scalar">
           <DataItem Dimensions="3352598"
             NumberType="Float"
             Precision="8"
             Format="HDF">minpr.63.nc:/pressure_min
           </DataItem>
        </Attribute>
        <Attribute Name="time_of_minimum_air_pressure_at_sea_level"
          Center="Node"
          AttributeType="Scalar">
           <DataItem Dimensions="3352598"
             NumberType="Float"
             Precision="8"
             Format="HDF">minpr.63.nc:/time_of_pressure_min
           </DataItem>
        </Attribute>
  
        <!-- swan_HS_max.63.nc  -->
        <Attribute Name="maximum_sea_surface_wave_significant_height"
          Center="Node"
          AttributeType="Scalar">
           <DataItem Dimensions="3352598"
             NumberType="Float"
             Precision="8"
             Format="HDF">swan_HS_max.63.nc:/swan_HS_max
           </DataItem>
        </Attribute>
  
        <!-- swan_TPS_max.63.nc -->
        <Attribute Name="maximum_sea_surface_wave_period_at_variance_spectral_density_maximum"
          Center="Node"
          AttributeType="Scalar">
           <DataItem Dimensions="3352598"
             NumberType="Float"
             Precision="8"
             Format="HDF">swan_TPS_max.63.nc:/swan_TPS_max
           </DataItem>
        </Attribute>
  
        <!-- maxrs.63.nc       -->
        <Attribute Name="maximum_radiation_stress"
          Center="Node"
          AttributeType="Scalar">
           <DataItem Dimensions="3352598"
             NumberType="Float"
             Precision="8"
             Format="HDF">maxrs.63.nc:/radstress_max
           </DataItem>
        </Attribute>
        <Attribute Name="time_of_maximum_radiation_stress"
          Center="Node"
          AttributeType="Scalar">
           <DataItem Dimensions="3352598"
             NumberType="Float"
             Precision="8"
             Format="HDF">maxrs.63.nc:/time_of_radstress_max
           </DataItem>
        </Attribute>
      </Grid>
    </Domain>
  </Xdmf>
```
