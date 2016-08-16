# vf:Resource

An economic resource, which is useful to people or the ecosystem.

## Object Properties
(relationships with other entities)

**vf:resourceType**

**vf:underlyingResource**: A more concrete resource which a resource is based upon.  For example, a resource which defines the rental of an apartment has the apartment itself as its underlying resource.

(data nodes)

**vf:quantity**: The quantity and unit of the resource.

*NOTE: resource can have 0 quantity, one can use it for historical resources which some process consumed as well as for planned resources which a planned process will create [Issue#24](https://github.com/valueflows/resource/issues/24)*

**vf:quantityAvailable**:  The quantity and unit of the resource that is available for transfers or processes.  This could be a calculated amount based on the *vf:quantity* less the quantity committed or otherwise unable to be promised for a transfer or process.


## Data Properties
(attributes)

**vf:trackingIdentifier**: For a resource, this can be a serial number for serialized resources (like a computer), or a lot number for batched resources (like a lot of asparagus that will be distributed in smaller quantities but may need to be tracked to its source in case of an e-coli outbreak).  Or it can just be another useful identifier.

## Open Issues
* Resource stage (where it is based on the last process or transfer made for the same resource in a work flow situation, like Translation@translated, Translation@edited, Translation@proofread). [Issue#30](https://github.com/valueflows/resource/issues/30)
* Resource access rules
* Resource agent roles
* Replace *vf:quantityAvailable** with logical resources [Issue#39](https://github.com/valueflows/resource/issues/39)

## Examples

### Value Flows ontology

```yaml
'@context': https://w3id.org/valueflows/v1
'@id': https://w3id.org/valueflows
'@type':
  - vf:Resource
  - owl:Ontology
'skos:note': Web ontology for modeling economic relationships and interactions
```

### Olive oil
From [Olive oil request](https://github.com/valueflows/valueflows/blob/master/use-cases/olive-oil-request.md) use case.

Some 2L of Olive Oil

```yaml
'@context': https://w3id.org/valueflows/v1
'@type':
  - vf:Resource
  - prodont:Olive_oil
vf:quantity':
  '@type': qudt:QuantityValue
  'qudt:unit': unit:Liter
  'qudt:numericValue': 2
```

### Bicycle
From [Broken bike](https://github.com/valueflows/valueflows/blob/master/use-cases/broken-bike.md) use case.

Particular bike
```yaml
'@context': https://w3id.org/valueflows/v1
'@id': https://john.example/inventory/supersonic-bike
'@type':
  - vf:Resource
  - prodont:Bicycle
  - https://osbike.example/models/supersonic
'skos:note': dodgy brake
'vf:currentLocation': http://sws.geonames.org/2654675/
```
