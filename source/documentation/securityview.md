# Security View

This section should include an overview of the nature of the system with regard to the information being processed or stored and the likely attack vectors that should be considered, result of a compromise with a brief indication of the measures in place to reduce the risk of compromise.

## Stored Data
Indicate the nature of the data being stored, for example, demographic, financial, health, commercially sensitive, public.

## Processed Data
Indicate the nature of the data being processed, for example, demographic, financial, health, commercially sensitive, public.

It is possible that in some instances, data cached or processed may include addtional data that makes it more valuable than data at rest.

## Attack Vectors
### Example: CSRF Attack
#### Risk: High
#### Implications of Compromise
Data theft etc. etc.
#### Mitigations
What we are doing to reduce the risk, can link to princinples outlined below.


# Security Principles
## Example: TLS will be enabled for all communication
#### Rationale
To prevent Man in the middle attacks, all communication will be over TLS version 1.2

#### Implications
Key management, key rotation etc. etc.

####  Applicability
All inter process communication over the network.