# Blob Storage

## What is Blob Storage?
Blob storage is a type of cloud storage service provided by Azure. It is designed to store and manage unstructured data, such as text or binary data like images, videos, documents, and backups.

## Difference from File Systems
The main difference between blob storage and the file system of Linux/Windows/Mac is the storage structure. Blob storage uses a flat architecture, where data is organized into containers and blobs, without a hierarchical file system. In contrast, the file system of operating systems like Linux, Windows, and Mac follows a hierarchical structure with directories and files.

## Advantages and Disadvantages
### Advantages
- Scalability: Blob storage can handle massive amounts of data, scaling up or down as needed.
- Durability: Data stored in blob storage is replicated across multiple servers and regions, ensuring high durability.
- Accessibility: Blob storage can be accessed from anywhere over the internet using HTTP/HTTPS protocols.
- Cost-effectiveness: Blob storage offers flexible pricing options based on data usage and access patterns.

### Disadvantages
- Limited file system features: Blob storage lacks some features of a traditional file system, such as file-level locking or direct file editing.
- No built-in hierarchical structure: Organizing and navigating data in blob storage requires custom naming conventions and metadata.

## Blob Storage Tiers
Azure Blob storage offers different tiers based on data access patterns and cost requirements:
- Hot tier: Optimized for frequently accessed data with higher storage costs but lower access costs.
- Cool tier: Designed for infrequently accessed data with lower storage costs but slightly higher access costs.
- Archive tier: Suitable for rarely accessed or long-term retention data with the lowest storage costs but higher access latency and costs.

It's recommended to use the Azure Pricing Calculator or the Azure portal to estimate costs based on specific storage and access patterns.

## Parts of Azure Blob Storage
- Account: An Azure storage account acts as a top-level namespace for your blob storage. It provides a unique identifier and authentication credentials for accessing the storage.
- Container: Containers are logical units within a storage account and are used to organize and group related blobs. They are similar to folders in a file system and provide a level of organization and security for the blobs.
- Blobs: Blobs are the actual data stored within containers. They can be of three types: block blobs (for general-purpose storage), append blobs (for append-only scenarios), or page blobs (for virtual machine disks).

In summary, Azure Blob storage is a scalable and durable cloud storage service designed for unstructured data. It differs from traditional file systems in terms of storage structure and offers advantages such as scalability and accessibility while having some limitations. Blob storage provides different tiers for cost optimization based on data access patterns and consists of storage accounts, containers, and blobs as its core components.

# Types of Redundancy in Azure Blob Storage

- LRS (Locally Redundant Storage):
  - Data is replicated within a single storage scale unit in a single region.
  - Provides high durability within a region.
  - Suitable for scenarios where data availability is critical within a specific region.

- ZRS (Zone-Redundant Storage):
  - Data is replicated across multiple availability zones within a single region.
  - Offers higher durability and availability compared to LRS.
  - Suitable for scenarios where higher availability is required within a region.

- GRS (Geo-Redundant Storage):
  - Data is replicated synchronously to a paired region, providing additional redundancy across regions.
  - Provides higher durability and availability by storing data in a primary and secondary region.
  - Suitable for scenarios where data must be highly available in case of a region-wide outage.

- RA-GRS (Read-Access Geo-Redundant Storage):
  - Similar to GRS, but with the additional ability to read data from the secondary region.
  - Allows read access to the data even if the primary region is unavailable.
  - Suitable for scenarios where read access to data is required during a primary region outage.

- GZRS (Geo-Zone-Redundant Storage):
  - Data is replicated across multiple availability zones in both the primary and secondary region.
  - Provides the highest durability and availability among the redundancy options.
  - Suitable for scenarios that require the highest level of data availability and durability.

- RA-GZRS (Read-Access Geo-Zone-Redundant Storage):
  - Similar to GZRS, but with the additional ability to read data from the secondary region.
  - Allows read access to the data even if both the primary region and primary availability zone are unavailable.
  - Suitable for scenarios where read access to data is required during a primary region and availability zone outage.
