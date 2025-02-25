# Backstage file for SCM Integrations

Backstage is a service catalog that allows users to add metadata or annotations to their repositories, helping to organize and categorize the available resources for easier navigation and understanding. You can leverage your SCM integration to pull metadata associated with Backstage catalog files into Snyk AppRisk.

You can use the Backstage catalog file for GitHub, GitLab, Azure DevOps, BitBucket Cloud, and BitBucket on-prem SCM integrations.

## Prerequisites

* Configured SCM integration for Snyk AppRisk.
* The `catalog-info.yaml` file is available in the root folder or your Project.&#x20;

## Required Parameters

* A configured SCM integration.&#x20;
* The `catalog-info.yaml` file from your Project.

## Integration Hub setup

1. Open the **Integration Hub** menu.&#x20;
2. Select an SCM integration.&#x20;
3. Click the **Settings** option of the SCM integration.&#x20;
4. Enable the **Add Backstage Catalog** option.
5. Optional - if the Backstage catalog filename in your repository is not `catalog-info.yaml` you can change the default value in the Backstage catalog filename field.
6. Select at least one attribute you want to add to Snyk AppRisk.

{% hint style="info" %}
Snyk AppRisk parses the fields of the detected file using the default field names unless an alternate field name is specified.
{% endhint %}

7. Click the **Done** button.

<figure><img src="../../../.gitbook/assets/image (1) (12) (1).png" alt="Integration Hub - Backstage setup"><figcaption><p>Integration Hub - Backstage setup</p></figcaption></figure>

After you finish configuring the Backstage catalog, Snyk AppRisk starts enriching your repository assets with the data found in the backstage catalog .yaml file.

## Backstage catalog in Asset Inventory

Use the Backstage catalog to enrich the repository assets and to define the component entity. For this type of situation, a component is defined as a software component, like a service, repository, a website, library, and so on.&#x20;

Components have several attributes and most of them are optional:

* `spec.type` (mandatory) - represents the classification of the repository.&#x20;
* `spec.owner` (mandatory) - represents the team owning the repository.
* `spec.lifecycle` - represents the lifecycle state of the component, for example `production`, `experimental`, `deprecated`.
* `spec.system` (optional) - represents a group of components that serve the same purpose. This concept is referred to as “Application”.
* `Metadata.name` (mandatory) - represents the name of the component.
* `Metadata.title` (optional) - represents the name of the component.

The Backstage data is dynamic and may change over time:

* If new commits or updates are made on the `catalog-info.yaml` file, then Snyk AppRisk updates the asset attribute for that specific repository asset.
* If the`catalog-info.yaml` file is removed from the repository, then Snyk AppRisk deletes the asset attribute from that specific repository assets.

### Inventory menu

Depending on the selection you made on the Integration Hub configuration menu, only those selections are displayed in filters from the Inventory menu. For example, if you selected the Category attribute, then it will also be displayed in the filters list.

<figure><img src="../../../.gitbook/assets/image (448).png" alt="Backstage selections in the Integration Hub menu"><figcaption><p>Backstage selections in the Integration Hub menu</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (367).png" alt="Backstage selections in the Snyk AppRisk Inventory menu" width="375"><figcaption><p>Backstage selections in the Snyk AppRisk Inventory menu</p></figcaption></figure>

### Asset Summary Tab

The Asset Summary tab shows the six Backstage attributes that are configured in the Integration Hub only if you choose to integrate with Backstage.

<figure><img src="../../../.gitbook/assets/image (368).png" alt="Backstage selections in the Asset Summary menu"><figcaption><p>Backstage selections in the Asset Summary menu</p></figcaption></figure>

### Asset Attributes Tab

In the Asset Attributes tab only the selected attributes should be added as metadata to the repository asset.

```
{
    name:"spring.goof",
    repositoryURL:"https://github.com/snyk/spring.goof.git",
    context:[
             {
              name: "super-duper-component",
              title: "Super Duper Component",
	      application: "super-duper-app",
	      lifecycle: "production",
	      owner: "super-duper-team",
	      category: "service",
              source: "Backstage"
              }]
}
```

### Policies Filter

In the policy builder you can find only the attributes you have previously selected when configuring the backstage catalog file.&#x20;

<figure><img src="../../../.gitbook/assets/image (369).png" alt="Backstage selections in the Policies menu" width="375"><figcaption><p>Backstage selections in the Policies menu</p></figcaption></figure>

The following list describes all possible backstage attributes that you can choose from when you configure the backstage catalog file.&#x20;

* **Application** - represents a group of components that serve the same purpose.&#x20;
* **Owner** - specifies the team owning the repository.
* **Catalog name** - the metadata name.
* **Title** - a name to display for the entity instead of the property. It is an alternative to the metadata name, when the catalog name is too hard to read.
* **Category** - represents the classification of the repository. The Organization can choose any name or text.
* **Lifecycle** - specifies the lifecycle state of the component, for example production, experimental, deprecated.

The following video provides an overview of the Backstage file option from the Integration Hub and a quick explanation of the available attributes:

{% embed url="https://www.youtube.com/watch?v=gfOUSE0UhHA" %}
Liked the video? Checkout the rest of the course on [Snyk Learn](https://learn.snyk.io/catalog/?type=product-training\&topics=AppRisk)!
{% endembed %}
