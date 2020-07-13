# X Usecase Profile

Xは、章番号

## Overview


---------
\< Manage licenses compatible with the final product and clarify responsibility in the supply chain\>

下記を先行して記載を試みる

下記の各アイテムを、タグ名(Field)に分解するところから

・ Product information ( Product name, product number, etc. )

・ Compatible license with final product or not

下記についても、まずは、同Profile内で提案する

・ Who adopted the package

・ When adopted the package

・ Temporary adoption or using for Final Product

(If the package is temporary adoption)

   -The schedule of remove
   
   -Who has the responsibility of remove

・Schedule of next report

下記については、先送りの可能性も考慮

\<Functional Safety\>

・ Who obtained certification

・ Information of authentication

  FuSaに関して、ガワだけ作って、後から成型、というのがＯＫか、あるいは、SPDX 3.0からドロップか要議論
  
  以下は、AGL IC-EGからの提案で、CommunityのFuSa(QM)関連の健全性情報がSPDXとして取り扱えると良い、という提案
  URL情報をSPDXに埋め込むなどとして、Ruleの所在有無をトレースできるようにしたい、とのこと

・ Contribution Rule

・ Coding Rule and/or Style Guide


\<Clarification of who contributed to the community\>

・ Who contributed to the community in the Supply Chain

・ The evidences of the contribution
  
  Fusa, Contribution責任は別Profileとすべきか要議論
  
  
  下記は、下流から上流への送付を前提とした記述が残っているので、要修正

-----

## Product information fields <a name="X.1"></a>

### Entities
| Entity | Parent | Required | Cardinality |
| ------ | ------ | -------- | ----------- |
| [Prerequisite Product Information](#prerequisite-product-information) | [Artifact](2-base-profile.md#artifact) ([Package](2-base-profile.md#package), [File](2-base-profile.md#file), [Snippet](2-base-profile.md#snippet)) | Yes | 1..1 |
| [License Compatiblity For Prerequisite Product](#license-compatibility-for-prerequisite-product) | [Artifact](2-base-profile.md#artifact) ([Product Information](X-usecase-profile.md#product-information)) | No | 0..* |
| [Acceptable Usecase of the License](#acceptable-usecase-of-the-license) | [Artifact](2-base-profile.md#artifact) ([Product Information](X-usecase-profile.md#product-information)) | No | 0..* |
| [Expriation Date of Usecase Information](#expiration-date-of-usecase-information) | [Artifact](2-base-profile.md#artifact) ([Product Information](X-usecase-profile.md#product-information)) | No | 0..* |

## Prerequisite Product Information

Parent: Package, File, Snippet, or External Artifact

Cardinality: upto 1 per Artifact

### Fields
| Field | Required | Cardinality |
| ----- | -------- | ----------- |
| [Prerequisite Product Name](#prerequisite-product-name-tag) | No | 0..1 |
| [Prerequisite Product Identifier](#prerequisite-product-identifier-tag) | Yes | one |
| [Prerequisite Product Version](#prerequisite-product-version-tag) | No | 0..* |

### Prerequisite Product Name
#### Purpose

Identify the name of the target product that used as the prerequisite for license compatibility assumption. The metadata for the Product Name field is shown in Table XX1.

Table XX1 — Metadata for the product information field

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..1 |
| Format | Single line of text. |

<br>

#### Intent

Describe target product to be identified with this "usecase" profile to manage Lisence Information of software packages to be integrated. 

#### Tag: `PrerequisiteProductName:`

Examples:

```text
ProductName: ABC COMPANYs Product to be Launched at 20YYMM-TBD
```


### Prerequisite Product Identifier
#### Purpose

Identify the target product even if the name of product not determined yet.

Required: Yes

Cardinality: One

Data Format: ["DocumentRef-"`[idstring]`":"`[SPDXID]`] |

 | `NONE` | `NOASSERTION`

"DocumentRef-"`[idstring]`: is an optional reference to an external SPDX
document as described in [section 2.6](2-document-creation-information.md#2.6)
`[idstring]` is a unique string containing letters, numbers, `.` and/or `-`

`[NONE]`, if the file contains no target product information whatsoever; or

`[NOASSERTION]`, if:

(i) the SPDX file creator has made no attempt to determine this field; or
(ii) the SPDX file creator has intentionally provided no information (no meaning should be implied by doing so).

<br>

#### Intent

Describe target product to be identified with this "usecase" profile to manage Lisence Information of software packages to be integrated. 

#### Tag: `PrerequisiteProductIdentifier:`

Examples:

```text
PrerequisiteProductIdentifier: DocumentRef-spdx-tool-1.2:SPDXRef-5
```

### Prerequisite Product Version

#### Purpose

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..* |
| Format | Single line of text. |

#### Intent

#### Tag: `PrerequisiteProductVersion:`

## License Compatiblity For Prerequisite Product

Parent: Product Information, or External Artifact

Cardinality: upto 1 per Artifact

### Fields
| Field | Required | Cardinality |
| ----- | -------- | ----------- |
| [License Compatiblity For Prerequisite Product](#license-compatibility-for-prerequistie-product-tag) | No | 0..* |

### License Compatiblity For Prerequisite Product

#### Purpose

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..* |
| Format | `[LicenseName]` |

#### Intent

#### Tag: `LicenseCompatiblityForPrerequisiteProduct:`

## Acceptable Usecase of the License

Parent: Product Information, or External Artifact

Cardinality: 0..*

### Fields
| Field | Required | Cardinality |
| ----- | -------- | ----------- |
| [Acceptable Usecase of the License](#acceptable-usecase-of-the-license-tag) | No | 0..* |
| [Acceptable License Inventory Deadline](#acceptable-license-inventory-deadline-tag) | No | 0..* |


### Acceptable Usecase of the License

#### Purpose

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..* |
| Format | `[LicenseName]` |

#### Intent

#### Tag: `AcceptableUsecaseOfTheLicense:`

### Acceptable License Inventory Deadline

#### Purpose

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..* |
| Format | Single line of text.  |

#### Intent

#### Tag: `AcceptableLicenseInventoryDeadLine:`




# From Here: Not modified yet.
# 以下は、Licensing Profileからのコピー

### Entities
| Entity | Parent | Required | Cardinality |
| ------ | ------ | -------- | ----------- |
| [Product Information](#product-information) | [Artifact](2-base-profile.md#artifact) ([Package](2-base-profile.md#package), [File](2-base-profile.md#file), [Snippet](2-base-profile.md#snippet)) | Yes | 1..1 |
| [License Reference](#license-reference) | [Document Root](2-base-profile.md#document-root) | No | 0..* |



## License Information

Parent: Package, File, Snippet, or External Artifact
Cardinality: 1 per Artifact

### Fields
| Field | Required | Cardinality |
| ----- | -------- | ----------- |
| [Discovered License](#discovered-license) | Yes | 1..1 |
| [Declared License](#declared-license) | Yes | 1..1 |
| [Concluded License](#concluded-license) | Yes | 1..1 |
| [Distributed License](#distributed-license) | Yes | 1..1 |
| [Copyright Text](#copyright-text) | Yes | 1..1 |

### Discovered License
#### Purpose

#### Intent
Here, the intent is to provide the license information actually in the file, as compared to the Concluded License field.

**4.6.3** Cardinality: Mandatory, one or many.

**4.6.4** Data Format: `<SPDX License Expression>` |

 ["DocumentRef-"`[idstring]`":"]"LicenseRef-"`[idstring]` |

 | `NONE` | `NOASSERTION`

where:

`<SPDX License Expression>` is a valid SPDX License Expression

as defined in [Appendix IV](appendix-IV-SPDX-license-expressions.md).

"DocumentRef-"`[idstring]`: is an optional reference to an external SPDX

document as described in [section 2.6](2-document-creation-information.md#2.6)

`[idstring]` is a unique string containing letters, numbers, `.` and/or `-`

**4.6.5** Tag: `LicenseInfoInFile:`

Example:

    LicenseInfoInFile: GPL-2.0-only
    LicenseInfoInFile: LicenseRef-2

**4.6.6** RDF: Property `spdx:licenseInfoInFile` in class `spdx:File`