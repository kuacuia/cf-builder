# CloudFormation Development Template

This repository consists of a template for developing Cloudformation templates in a sane manner.  Base.yaml or Base.json define the structure of the template with placeholders for each section of the cloudformation template.  Within the partials directory there is a subdirectory for each section, and within that subdirectory is where the objects are defined.  Objects are defined one (or whatever grouping you prefer) per file, allowing each file to be focused on one object.  See the partials-example directory for an example that asks for a key pair, creates an ec2 instance, security group, and outputs the instance id and security group id.

Using the included gulp file, gulp will merge either the json or yaml files into a single template and output it to the dist subdirectory.

## Requirements

You will need to have node.js and gulp installed on your development machine.  Once they are installed, you will need to install the gulp-merge-json and gulp-yaml-merge modules via npm.

This can be accomplished by running:

```
npm install gulp-merge-json gulp-yaml-merge --save-dev
```

## Building templates

To build the example template, run the command 

```
gulp example
```

in the top level directory.

Once you have your partials complete, you can build your template by running either

```
gulp json
```

or 

```
gulp yaml
```

in the top-level directory, depending on the format you prefer to write your templates in.  When that completes, you should have a fully baked cloudformation template that you can upload to s3, use with the awscli, or paste into the cloudformation console to create your stack.