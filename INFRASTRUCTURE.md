
## Insights
- 90% of the chaincode execution time is consumed by message transfers between the peer and the chaincode. 

## Question
- What is the standard transaction payload size that we must consider?
### Answer
- The transport (gRPC) layer currently has a max size of 100MB.  
- Overall transaction constains signatures, certificates, metadata, etc),
- Request and/or response payloads should not exceed 90MB or so.

## Question
- What are the contents of a block in Hyperledger Fabric
### Answer
- proposal, endorse signatures, read/write set and order signature in a transaction are inside one block

## Question
- How are blocks generated in Hyperledger Fabric

### Answer
- Transactions are collected into blocks/batches on the ordering service first. 
- Blocks are cut either when the BatchSize is met, or when BatchTimeout elapses (provided a non-empty block).

## Question
- Where are blocks stoed in a Hyperledger Fabric file system

### Answer
- Blocks are stored locally to disk on every ordering service node along with a LevelDB to index these blocks by number 