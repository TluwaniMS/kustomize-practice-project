# kustomize practice project

# What is Kustomize?

Kustomize serves as a configuration management tool, utilizing layering to maintain the fundamental settings of your applications and components. This is achieved by applying declarative yaml artifacts (referred to as patches) that selectively modify default settings without directly altering the original files.

# Kustomize folder structure:

### base:

A base, in the context of kustomization, serves as a reference point for other kustomizations. This means that any kustomization, including overlays, can use another kustomization as its base. Importantly, a base remains unaware of the overlays that make use of it.


### overlay:

An "overlay" is a type of kustomization that relies on another kustomization. The kustomizations to which an overlay refers (via file path, URI, or other means) are referred to as "bases." It's important to note that an overlay cannot function independently and requires its bases to be present. Additionally, an overlay can also serve as a base for another overlay.

# Kustomization file:

The kustomization file represents a YAML specification for a Kubernetes Resource Model (KRM) object referred to as a 'Kustomization.' It outlines the process of generating or modifying other KRM objects.
