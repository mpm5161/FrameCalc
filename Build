/**
 * Frame.io Pricing & Packaging Configuration
 * Source: Frame SKUs, Contracting & Migration Handbook V2.2 (6/19/26)
 *        Frame Corp FY26 Product Playbook (7/10/26)
 *        CPro September Fast Start deck
 *
 * UPDATE THIS FILE when pricing, plans, or packaging changes.
 * DO NOT edit the main app for pricing updates. Only edit this file.
 *
 * Prices are USD, annual, per seat / unit unless noted.
 * List = standard list price | Target = target selling price | Floor = minimum price
 */

var PRICING_CONFIG = {
  version: '2.2',
  lastUpdated: '2026-06-19',
  currency: 'USD',

  // ─── BUYING PROGRAMS ────────────────────────────────────────────────────────
  buyingPrograms: {
    etla: {
      id: 'etla',
      name: 'ETLA',
      fullName: 'Enterprise Term License Agreement',
      description: '3-year minimum commitment. Primary buying vehicle for Frame.io enterprise deals.',
      minTermYears: 3,
      availablePlanIds: ['select', 'select_sbwm', 'prime'],
      notes: [],
    },
    vipc: {
      id: 'vipc',
      name: 'VIP Custom',
      fullName: 'VIP Custom (VIP-C)',
      description: '1–3 year terms. Customer must be on Frame.io V4.',
      minTermYears: 1,
      maxTermYears: 3,
      availablePlanIds: ['select', 'select_sbwm', 'prime'],
      notes: ['Customer must be on Frame.io V4 to use VIP Custom.'],
    },
    frame_paper: {
      id: 'frame_paper',
      name: 'Frame Paper',
      fullName: 'Frame Paper',
      description: 'Legacy Frame.io contract. ETLA or VIP Custom preferred for new deals.',
      minTermYears: 1,
      availablePlanIds: ['select_paper', 'prime_paper'],
      notes: [
        'No Adobe Admin Console.',
        'No seat-scaled storage. Legacy storage tiers apply.',
      ],
    },
  },

  // ─── PLANS ──────────────────────────────────────────────────────────────────
  plans: {
    // ── SELECT (ETLA / VIP Custom) ──
    select: {
      id: 'select',
      name: 'Frame.io Enterprise: Select',
      shortName: 'Select',
      buyingProgramIds: ['etla', 'vipc'],
      pricing: {
        type: 'flat_per_seat',
        perSeat: { list: 960, target: 720, floor: 580 },
      },
      storage: {
        managed: {
          type: 'seat_scaled',
          tbPerUser: 2,
          maxTB: 750,                   // ~375 users × 2TB
          label: '2 TB per user (up to 750 TB pooled)',
        },
        mounted: {
          includedTB: 2,
          label: '2 TB per account (included)',
        },
      },
      minSeats: 10,
      maxSeats: null,
      adminConsole: true,
      features: {
        sbwm: 'requires_combined_sku',  // must use Select+SBWM combined SKU
        forensicWatermarking: false,
        storageConnect: false,
        secureSharing: false,
        secureSharingAuthDomains: true,
        drm: false,
        workspaces: 'unlimited',
        watermarkTemplates: 'unlimited',
        internalComments: true,
        restrictedProjects: true,
        sso: true,
      },
      skus: { com: '30007966', gov: '30007972' },
      notes: [
        'Adobe Admin Console required.',
        'Session-based watermarking requires the "Select with SBWM" combined SKU.',
        'Select and Prime cannot coexist on the same Adobe Admin Console.',
      ],
    },

    // ── SELECT WITH SBWM (ETLA / VIP Custom) ──
    select_sbwm: {
      id: 'select_sbwm',
      name: 'Frame.io Enterprise: Select with SBWM',
      shortName: 'Select + SBWM',
      buyingProgramIds: ['etla', 'vipc'],
      pricing: {
        type: 'flat_per_seat',
        perSeat: { list: 1080, target: 840, floor: 700 },
      },
      storage: {
        managed: {
          type: 'seat_scaled',
          tbPerUser: 2,
          maxTB: 750,
          label: '2 TB per user (up to 750 TB pooled)',
        },
        mounted: {
          includedTB: 2,
          label: '2 TB per account (included)',
        },
      },
      minSeats: 10,
      maxSeats: null,
      adminConsole: true,
      features: {
        sbwm: 'included',
        forensicWatermarking: false,
        storageConnect: false,
        secureSharing: false,
        secureSharingAuthDomains: true,
        drm: false,
        workspaces: 'unlimited',
        watermarkTemplates: 'unlimited',
        internalComments: true,
        restrictedProjects: true,
        sso: true,
      },
      skus: { com: '30016015', gov: '30016016' },
      notes: [
        'Adobe Admin Console required.',
        'Session-based watermarking included (SBWM qty must match Select qty).',
        'Select and Prime cannot coexist on the same Adobe Admin Console.',
      ],
    },

    // ── PRIME (ETLA / VIP Custom) ──
    prime: {
      id: 'prime',
      name: 'Frame.io Enterprise: Prime',
      shortName: 'Prime',
      buyingProgramIds: ['etla', 'vipc'],
      pricing: {
        type: 'volume_tiered',
        // ETLA: volume-tiered pricing
        tiers: [
          { min: 1,    max: 19,   list: 1794, target: 1345, floor: 964  },
          { min: 20,   max: 49,   list: 1615, target: 1211, floor: 868  },
          { min: 50,   max: 99,   list: 1435, target: 1076, floor: 771  },
          { min: 100,  max: 499,  list: 1256, target: 942,  floor: 675  },
          { min: 500,  max: 999,  list: 1121, target: 841,  floor: 603  },
          { min: 1000, max: 2999, list: 987,  target: 740,  floor: 530  },
          { min: 3000, max: null, list: 897,  target: 673,  floor: 482  },
        ],
        // VIP Custom: flat per seat, no volume tiers
        vipc: { list: 1794, target: 1346, floor: 964 },
      },
      storage: {
        managed: {
          type: 'seat_scaled',
          tbPerUser: 3,
          maxTB: 1000,                  // 1 PB cap (~334 users × 3TB)
          label: '3 TB per user (up to 1 PB pooled)',
        },
        mounted: {
          includedTB: 2,
          label: '2 TB per account (included)',
        },
      },
      minSeats: 10,
      maxSeats: null,
      adminConsole: true,
      features: {
        sbwm: 'included',
        forensicWatermarking: true,
        storageConnect: true,
        secureSharing: true,
        secureSharingAuthDomains: true,
        drm: true,
        workspaces: 'unlimited',
        watermarkTemplates: 'unlimited',
        internalComments: true,
        restrictedProjects: true,
        sso: true,
        assetLifecycleManagement: true,
      },
      skus: { com: '30007968', gov: '30007969' },
      notes: [
        'Adobe Admin Console required.',
        'All enterprise security features included (forensic watermarking, DRM, Storage Connect, secure sharing).',
        'Session-based watermarking included.',
        'ETLA: volume-based pricing discounts apply (see tiers).',
        'VIP Custom: flat $1,346/seat (target), no volume tiers.',
        'Select and Prime cannot coexist on the same Adobe Admin Console.',
      ],
    },

    // ── SELECT (FRAME PAPER) ──
    select_paper: {
      id: 'select_paper',
      name: 'Frame.io Select (Frame Paper)',
      shortName: 'Select (Frame Paper)',
      buyingProgramIds: ['frame_paper'],
      pricing: {
        type: 'flat_per_seat',
        perSeat: { list: 960, target: 720, floor: null }, // floor: confirm with Deal Desk
      },
      storage: {
        managed: {
          type: 'account_level',
          tbTotal: 3,                 // 3 TB per account (not seat-scaled)
          label: '3 TB per account (not seat-scaled)',
        },
        mounted: {
          includedTB: 2,
          label: '2 TB per account (included)',
        },
      },
      minSeats: 10,
      maxSeats: null,
      adminConsole: false,
      features: {
        sbwm: 'legacy_addon',
        forensicWatermarking: false,
        storageConnect: false,
        secureSharing: false,
        secureSharingAuthDomains: true,
        drm: false,
        workspaces: 'unlimited',
        watermarkTemplates: 'unlimited',
        internalComments: true,
        restrictedProjects: true,
        sso: true,
      },
      notes: [
        'No Adobe Admin Console.',
        'Storage: 3 TB per account total (not seat-scaled). Additional: legacy Active Storage add-on.',
        'Session-based watermarking: legacy add-on only.',
      ],
    },

    // ── PRIME (FRAME PAPER) ──
    prime_paper: {
      id: 'prime_paper',
      name: 'Frame.io Prime (Frame Paper)',
      shortName: 'Prime (Frame Paper)',
      buyingProgramIds: ['frame_paper'],
      pricing: {
        type: 'volume_tiered',
        tiers: [
          { min: 1,    max: 19,   list: 1794, target: 1345, floor: null },
          { min: 20,   max: 49,   list: 1615, target: 1211, floor: null },
          { min: 50,   max: 99,   list: 1435, target: 1076, floor: null },
          { min: 100,  max: 499,  list: 1256, target: 942,  floor: null },
          { min: 500,  max: 999,  list: 1121, target: 841,  floor: null },
          { min: 1000, max: 2999, list: 987,  target: 740,  floor: null },
          { min: 3000, max: null, list: 897,  target: 673,  floor: null },
        ],
      },
      storage: {
        managed: {
          type: 'legacy_per_user_gb',
          gbPerUser: 200,             // 200 GB per user (legacy, not TB seat-scaled)
          label: '200 GB per user (legacy, not seat-scaled)',
        },
        mounted: {
          includedTB: 2,
          label: '2 TB per account (included)',
        },
      },
      minSeats: 10,
      maxSeats: null,
      adminConsole: false,
      features: {
        sbwm: 'included',
        forensicWatermarking: true,
        storageConnect: true,
        secureSharing: true,
        secureSharingAuthDomains: true,
        drm: true,
        workspaces: 'unlimited',
        watermarkTemplates: 'unlimited',
        internalComments: true,
        restrictedProjects: true,
        sso: true,
      },
      notes: [
        'No Adobe Admin Console.',
        'Storage: 200 GB per user (legacy). Not seat-scaled like Adobe Admin Console SKUs.',
        'Session-based watermarking included.',
      ],
    },
  },

  // ─── ADD-ONS ────────────────────────────────────────────────────────────────
  addons: {
    managedStorage: {
      id: 'managedStorage',
      name: 'Managed Storage',
      unit: 'per TB / year',
      pricing: { list: 720, target: 540, floor: 432 },
      skus: { com: '30007970', gov: '30007965' },
      availableWithPlanIds: ['select', 'select_sbwm', 'prime'],
      description: 'Additional managed storage beyond the included seat-scaled allocation.',
    },
    mountedStorage: {
      id: 'mountedStorage',
      name: 'Mounted Storage',
      unit: 'per 10 TB block / year',
      pricing: { list: 9600, target: 7680, floor: 7296 },
      skus: { com: '30015983', gov: '30015984' },
      blockSizeTB: 10,
      baseTBIncluded: 2,             // 2 TB always included per account
      availableWithPlanIds: ['select', 'select_sbwm', 'prime', 'select_paper', 'prime_paper'],
      description:
        'Mounts Frame.io cloud storage as a local OS drive (macOS/Windows). All plans include 2 TB per account. Each add-on block adds 10 TB.',
    },
  },

  // ─── BUSINESS RULES ─────────────────────────────────────────────────────────
  rules: {
    minSeats: 10,
    cannotMixSelectAndPrime:
      'Frame Select and Prime cannot be held simultaneously on the same Adobe Admin Console.',
    etlaMinTermYears: 3,
    workingWeeksPerYear: 48,          // used in ROI calculations
  },
};
