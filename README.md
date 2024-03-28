# kustomize practice project

# Main Objective:

This repository was created with the intention of giving one a quick guide on how to use `Kustomize`.

# What is Kustomize?

Kustomize serves as a configuration management tool, utilizing layering to maintain the fundamental settings of your applications and components. This is achieved by applying declarative yaml artifacts (referred to as patches) that selectively modify default settings without directly altering the original files.

# Kustomize folder structure:

![Kustomize Folder Structure](https://github.com/TluwaniMS/kustomize-practice-project/blob/master/supporting-images/Screenshot%202023-08-04%20at%2012.13.28.png)

### base:

A base, in the context of kustomization, serves as a reference point for other kustomizations. This means that any kustomization, including overlays, can use another kustomization as its base. Importantly, a base remains unaware of the overlays that make use of it.


### overlay:

An "overlay" is a type of kustomization that relies on another kustomization. The kustomizations to which an overlay refers (via file path, URI, or other means) are referred to as "bases." It's important to note that an overlay cannot function independently and requires its bases to be present. Additionally, an overlay can also serve as a base for another overlay.

# Kustomization file:

The kustomization file represents a YAML specification for a Kubernetes Resource Model (KRM) object referred to as a 'Kustomization.' It outlines the process of generating or modifying other KRM objects.


# Practice commands

###### building from `overlays/dev-patches`:

```
kustomize build overlays/dev-patches
```

###### To apply the app manifests:

```
kustomize build overlays/dev-patches | kubectl apply -f -
```

###### building from `overlays/dev-patch-strategic-merge`

```
kustomize build overlays/dev-patch-strategic-merge
```

###### To apply the app manifests:

```
kustomize build overlays/dev-patch-strategic-merge | kubectl apply -f -
```

###### building from `overlays/dev-patch-json-6902`

```
kustomize build overlays/dev-patch-json-6902
```

###### To apply the app manifests:

```
kustomize build overlays/dev-patch-json-6902 | kubectl apply -f -
```
