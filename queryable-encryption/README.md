# Queryable Encryption
Queryable Encryption enables a client application to encrypt data before transporting it over the network using fully randomized encryption, while maintaining queryability. Sensitive data is transparently encrypted and decrypted by the client and only communicated to and from the server in encrypted form.

The provided notebooks allows you to demonstrate MongoDB queryable encryption feature for both explicit and automatic mechanism using a local CMK.

## Prerequisite

1. Setup and start a [MongoDB Atlas Cluster](https://www.mongodb.com/docs/atlas/getting-started/?jmp=docs).
2. [Load sample data](https://www.mongodb.com/docs/atlas/sample-data/) into your cluster.
3. Download the [Automatic Encryption Shared Library](https://www.mongodb.com/docs/v7.0/core/queryable-encryption/reference/shared-library/#std-label-qe-reference-shared-library-download)
4. Extract the downloaded archive and put the `mongo_crypt.dylib` file in your project (or anywhere else).


## Configuration

- Copy `envrc_template.txt` file and rename it to `.env`.
- Overwrite the following variables in your newly created `.env` file.
```
export MONGODB_URI="<Your MongoDB URI>"
export SHARED_LIB_PATH="<Full path to your Automatic Encryption Shared Library>"

```
## Usage


* [demo-qe-automatic-load-dataset](demo-qe-automatic-load-dataset.ipynb) and [demo-qe-explicit-load-dataset](demo-qe-explicit-load-dataset.ipynb) notebooks create encrypted related stuff (local CMK, DEK, collection...) and load sample encryped data using respectively automatic and explicit encryption mechanism.
   
* [demo-qe-automatic](demo-qe-automatic.ipynb) and [demo-qe-explicit](demo-qe-explicit.ipynb) notebooks contains sample queries to execute:
    * Try to insert document with an unconfigured client for encryption and get an error.
    * Insert document with a properly configured client.
    * Query on an unencrypted String field with an unconfigured client for encryption and get a  document with encrypted fields.
    * Query on an encrypted String field with an unconfigured client for encryption and get no result.
    * Query on an encrypted String field and get a  document with all fields in clear.
    * Same as previous query but on a Date field.
    * Same as previous query but on a Boolean field and using $in operator.
    * Query on an unencrypted and encrypted String fields in the same query using $and operator.
    * Query on two encrypted String fields using $and operator.


