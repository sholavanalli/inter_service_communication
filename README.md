# Inter-service Communication 

## Demands of inter-service communication 

1. Compatibility between several programming languages. 
2. Message passing must be fast. 
3. Rolling upgrades make it necessary that services be backward and forward compatible. 
4. Messages must be compact to reduce data transfer costs in public cloud. 

## What is Apache Thrift? 

See git repository for a client server demo of Thrift. 

https://github.com/sholavanalli/apache_thrift_demo 

## Why use Apache Thrift?

1. Developed and open sourced by FB. Still widely used. 
2. Encoded data contains field tags. They are compact aliases for a field. 
3. Field names can be changed but tags cannot be changed since field names are never in the encoded data. 
4. Forward compatibility (old code can work with new code): New fields can be added provided they are given new tag numbers. 
5. Backward compatibility (new code can work with old code): As far as new fields are not marked as required, new code can   
   read old data. 
6. Optional fields can be removed and that tag number should not be used again. 

## When not to use Apache Thrift? 

It is not a good idea to use Thrift when we’re working with legacy RPC systems. Lot of code must be re-written or duplicate code must exist to bridge the legacy code and the Thrift generated code. 

## Problems with JSON 

1. Not compact. Field names are encoded. 
2. As fields are encoded they cannot be removed or renamed. Hard to maintain forward and backward compatibility. 
3. Have to write lot of code for marshalling, unmarshalling, validation and exception handling. 
4. Ambiguity around encoding of numbers. Doesn’t distinguish integer and floating point numbers. Doesn’t specify a precision.
   Large integers cannot be represented in double precision floating point numbers. 
5. Passing a sequence of bytes without a character encoding cannot be done without hacks. 

## Object binding with Jackson

See git repository for a client and server demo of Jackson with JAX-RS. 

https://github.com/sholavanalli/jax_rs_jackson_demo 

## Why use Jackson? 

1. No need to write extra code for marshalling, unmarshalling, validation and exception handling.
2. Backward and forward compatibility is possible as Jackson can ignore unknown properties and set defaults to removed 
   properties. 
3. Works nicely with legacy RPC systems, especially when used with JAX-RS. 















