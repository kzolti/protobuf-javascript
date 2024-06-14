# kzolti/protobuf-javascript


## Diferencies with upstream 
This is a fork of [protocolbuffers/protobuf-javascript](https://github.com/protocolbuffers/protobuf-javascript) with the following changes:

###  Changes Made

    Added a fromObject method to the generated JavaScript protobuf classes.
    Referenced changes made in js_generator.cc to enable fromObject functionality.


## Manual check differencies

```
git remote add upstream https://github.com/protocolbuffers/protobuf-javascript.git
git fetch upstream
git diff upstream/main main  
```
### Changes to make in js_generator.cc (2024-06-12)
```
diff --git a/generator/js_generator.cc b/generator/js_generator.cc
index 44d00b1..7b97962 100644
--- a/generator/js_generator.cc
+++ b/generator/js_generator.cc
@@ -1980,7 +1980,7 @@ void Generator::GenerateClass(const GeneratorOptions& options,
   if (!NamespaceOnly(desc)) {
     printer->Print("\n");
     GenerateClassFieldInfo(options, printer, desc);
-
+    GenerateClassFromObject(options, printer, desc);
     GenerateClassToObject(options, printer, desc);
     // These must come *before* the extension-field info generation in
     // GenerateClassRegistration so that references to the binary
```


## Building from source

```
git clone https://github.com/kzolti/protobuf-javascript.git
cd protobuf-javascript
npm install
npm run build
```
## Installation

    npm install kzolti/protobuf-javascript --save
    


    