file:: [Caliptra_--_Silicon_RoT_Services_09012022_1712759217891_0.pdf](../assets/Caliptra_--_Silicon_RoT_Services_09012022_1712759217891_0.pdf)
file-path:: ../assets/Caliptra_--_Silicon_RoT_Services_09012022_1712759217891_0.pdf

- Traditional RoT architectures have offered a multitude of intrinsic security services and hosted security applications on a trusted execution environment (TEE) that consist of (but not limited to) hardware capabilities (cryptographic and microprocessor), ROM, Firmware & API infrastructure
  ls-type:: annotation
  hl-page:: 14
  hl-color:: blue
  id:: 6616a67b-57ae-4aa7-a5ca-501ce0c861c3
- Establishing a consistent root of trust on very different hardware configurations while maintaining configuration and deployment flexibility is challenging
  ls-type:: annotation
  hl-page:: 14
  hl-color:: blue
  id:: 6616a6bd-2b58-44ea-9c09-f001413ba2a3
- The OCP Security WG specifications are making progress towards establishing the platform and peripheral security architecture recommendations necessary to attain the desired consistency in platform security orchestration.
  ls-type:: annotation
  hl-page:: 14
  hl-color:: blue
  id:: 6616a6de-e130-4ea0-a14a-490c715418cf
- The Caliptra Silicon RoT must boot the SoC, measure the mutable code it loads, and measure and control mutation of non-volatile configuration bits in the SoC.
  ls-type:: annotation
  hl-page:: 15
  hl-color:: blue
  id:: 6616a71f-7906-4850-b8cd-c08fa424a76c
- the goals for a Caliptra 1.0 specification include
  ls-type:: annotation
  hl-page:: 15
  hl-color:: blue
  id:: 6616a770-3d9c-4371-9cd0-293b913e8e41
- Industry Standards and Association / Consortium Specifications
  ls-type:: annotation
  hl-page:: 17
  hl-color:: blue
  id:: 6616a992-6259-45f1-b174-471678c1c82f
- Threat Model
  ls-type:: annotation
  hl-page:: 20
  hl-color:: blue
  id:: 6616a9f0-e0f1-419c-84fb-cb40b2133d77
- Tools Accessible to Attacker
  ls-type:: annotation
  hl-page:: 20
  hl-color:: blue
  id:: 6616ab07-3e3f-435c-b052-be29002c3583
- Definition of Expertise* (JIL)
  ls-type:: annotation
  hl-page:: 21
  hl-color:: blue
  id:: 6616ab2b-f8c7-451a-a6eb-11bd82109d06
- Types of Attacks
  ls-type:: annotation
  hl-page:: 22
  hl-color:: blue
  id:: 6616ab3f-8820-4c43-aeb6-7c75475e4c26
- Trust Boundaries
  ls-type:: annotation
  hl-page:: 27
  hl-color:: blue
  id:: 6616ab61-b022-42bf-8edc-f12521649e5d
- High Level Architecture
  ls-type:: annotation
  hl-page:: 33
  hl-color:: blue
  id:: 6616abb8-a9b8-4049-a75a-2f15c53bb0f7
- Caliptra Profiles
  ls-type:: annotation
  hl-page:: 33
  hl-color:: blue
  id:: 6616ac65-5698-4e5f-a8ae-b4eef7524b5b
- Identity
  ls-type:: annotation
  hl-page:: 36
  hl-color:: blue
  id:: 6616acf3-36ff-430a-8655-68a071fadd65
- A Caliptra RTM must provide its runtime code with a cryptographic identity in accordance with the TCG DICE specification
  ls-type:: annotation
  hl-page:: 36
  hl-color:: blue
  id:: 6616ad03-89ec-4aa0-a310-94d7c7fbfca6
- Certificate Format
  ls-type:: annotation
  hl-page:: 40
  hl-color:: blue
  id:: 6616af10-1935-4fa5-a656-1c86313382c4
- Device Identity Certificates are following X.509 v3 format described in RFC 5280. The values in the X.509 certificate shall follow the DICE TCBInfo fields, as defined in [12]. The owner public key shall be extended into VendorInfo, with the security operational state reflecting the flags of DICE TCBInfo. Additional fields may be extended into VendorInfo
  ls-type:: annotation
  hl-page:: 40
  hl-color:: blue
  id:: 6616af1b-e223-4efd-957a-231e8ce4e4bf
- Table 1: Security States
  ls-type:: annotation
  hl-page:: 44
  hl-color:: blue
  id:: 6616af6b-bfa2-4bf0-b181-decf5be235ad
- Service Surface
  ls-type:: annotation
  hl-page:: 44
  hl-color:: blue
  id:: 6616af93-076f-48bb-bc49-f0bc1057f43d
- Device Resilience
  ls-type:: annotation
  hl-page:: 45
  hl-color:: blue
  id:: 6616af9a-75b7-4fb6-b6bc-44d324611c9e
- Informative comment: Example
  ls-type:: annotation
  hl-page:: 50
  hl-color:: blue
  id:: 6616b275-9d8a-479a-bd12-4fee380258dd
- Physical Attack Countermeasures
  ls-type:: annotation
  hl-page:: 51
  hl-color:: blue
  id:: 6616b292-d62c-417b-8ca1-b8ffc3694d9f
- Because a Caliptra RTM is expected to be a <1 mm2 fraction of a large SoC, side-channel mitigation is required only against extremely resourceful attackers that can wade and discern through a large number of confounding signals and power profiles. With that priority in mind, DPA and DMA attacks should be mitigated via decoy value generation.
  ls-type:: annotation
  hl-page:: 51
  hl-color:: blue
  id:: 6616b2b8-38f5-4098-b400-643ef19c11f5
- Any private key material or symmetric key material embedded in the RTL (and therefore“global”) must be treated as having low value, reaching zero value in a number of quarters
  ls-type:: annotation
  hl-page:: 51
  hl-color:: blue
  id:: 6616b2d3-6a46-43d7-8b58-f62dbe90a23a
- Mitigation against SCA is not necessarily trivial and may be implemented in a variety of ways.[14] provides a comprehensive overview of methods and techniques used in various SCA as well as recommendations for countermeasures against such attacks (including feasibility and applicability). Additionally, there are many academic papers available from NIST and other resources that discuss SCA and their countermeasures. July 202252
  ls-type:: annotation
  hl-page:: 52
  hl-color:: blue
  id:: 6616b2e5-1bc6-4a89-8599-6d902fb128a9
- Compliance and Certification Requirements
  ls-type:: annotation
  hl-page:: 53
  hl-color:: blue
  id:: 6616b2fb-c754-422d-b80c-f9bb31091ba4
- It is important to highlight it’s not necessary for the RTM itself to unilaterally attain e.g. FIPS140-3 L3. It is only relevant insofar the RTM is included in the “bag” that wants to obtain a compliance certification. For example, if a cloud provider wants to FIPS-certify PCIe link encryption in transit rooted to an ASIC identity emanating from a Caliptra RTM.
  ls-type:: annotation
  hl-page:: 53
  hl-color:: blue
  id:: 6616b30d-77dc-499a-a5e2-d040f029e7a4
- Known Answer Test (KAT) Support
  ls-type:: annotation
  hl-page:: 53
  hl-color:: blue
  id:: 6616b321-724f-4c55-a94d-4d6e462fe22c
- FW Signing/Verification Algorithms
  ls-type:: annotation
  hl-page:: 55
  hl-color:: blue
  id:: 6616b32d-9a70-447f-9f78-30481145e4bd
- Key Rotation
  ls-type:: annotation
  hl-page:: 55
  hl-color:: blue
  id:: 6616b34a-093f-4551-8e6f-c041b7275fcd
- HW Section
  ls-type:: annotation
  hl-page:: 56
  hl-color:: blue
  id:: 6616b358-66d8-43a8-bf6e-9be4576b2a99
- Mailbox
  ls-type:: annotation
  hl-page:: 61
  hl-color:: blue
  id:: 6616b3af-0c56-4054-bb68-8f9f85ce3da7
- Fuse Requirements
  ls-type:: annotation
  hl-page:: 66
  hl-color:: blue
  id:: 6616d3a1-8b85-45e3-90c2-5cc3d89a8982
- Since by default, unprogrammed Fuse bits are read as ‘0b’, zeroed in this context requires that all zero Fuse bits in a field be programmed to ‘1b’; Fuse bits already programmed to ‘1b’ must never be attempted to be programmed to ‘1b’.
  ls-type:: annotation
  hl-page:: 68
  hl-color:: blue
  id:: 6616d3d1-e5db-40e0-8805-a329b7abb11d