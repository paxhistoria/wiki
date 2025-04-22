# 🏝️ regions

### Basic Usage

```javascript
// Get all regions as a comma-separated list
${regions}

// Get information about straits and their owners
${regions.straitsAndOwners}

// Get all regions owned by your country
${regions.with({ owner: thisCountry.name })}
```

### Filter Behavior

Filters can be combined to create complex queries. When multiple filters are specified, a region must match ALL conditions to be included (AND logic).

#### Array Filter Behavior

Different array filters have different matching rules:

* `borderingRegions` and `borderingCountries`: Region must border ALL specified regions/countries (ALL must match)
* `hasTroopsFrom`, `hasAttackingTroopsFrom`, `hasDefendingTroopsFrom`: Region must have troops from ANY of the specified countries (ANY can match)
* `notOwner`: Region must NOT be owned by ANY of the specified countries
* `sameOwnerAs`: Region must have the same owner as ANY of the specified regions
* `differentOwnerThan`: Region must have a different owner than ALL of the specified regions

### Geographic Filters

```javascript
// Population range
${regions.with({ minPopulation: 500000, maxPopulation: 2000000 })}

// Economic filters
${regions.with({ minGDPPerCapita: 20000 })}
${regions.with({ maxGDPPerCapita: 15000 })}

// Region type filters
${regions.with({ type: "Coastal" })}  // Also supports "Land" and "Strait"

// Find by name
${regions.with({ name: "Paris" })}
```

### Ownership Filters

```javascript
// Regions owned by a specific country
${regions.with({ owner: "France" })}

// Regions NOT owned by specific countries (ANY in the array)
${regions.with({ notOwner: ["France", "Germany"] })}

// Regions with same owner as another region
// Can accept region ID, region name, or TransformedRegion object
${regions.with({ sameOwnerAs: "Paris" })}  // Region name
${regions.with({ sameOwnerAs: "64" })}  // Region ID
${regions.with({ sameOwnerAs: someRegion })}  // TransformedRegion object
${regions.with({ sameOwnerAs: ["England", "Austria"] })}  // Match if same owner as ANY

// Regions with different owner than another region
// Can accept region ID, region name, or TransformedRegion object
${regions.with({ differentOwnerThan: "Savoy" })}  // Region name
${regions.with({ differentOwnerThan: "22" })}  // Region ID
${regions.with({ differentOwnerThan: someRegion })}  // TransformedRegion object
${regions.with({ differentOwnerThan: ["Savoy", "Normandy"] })}  // Match if different from ALL
```

### Border Filters

```javascript
// Regions bordering a specific region
${regions.with({ borderingRegions: "Berlin" })}

// Regions bordering ALL of these regions
${regions.with({ borderingRegions: ["Berlin", "Warsaw"] })}

// Regions bordering a specific country
${regions.with({ borderingCountries: "Germany" })}

// Regions bordering ALL of these countries
${regions.with({ borderingCountries: ["Germany", "Poland"] })}
```

### Troop Presence Filters

```javascript
// Regions with/without troops
${regions.with({ hasTroops: true })}
${regions.with({ hasTroops: false })}

// Regions with troops from ANY of these countries
${regions.with({ hasTroopsFrom: ["Germany", "Italy"] })}

// Regions with attacking/defending troops from specific countries
${regions.with({ hasAttackingTroopsFrom: thisCountry.name })}
${regions.with({ hasDefendingTroopsFrom: thisCountry.name })}
```

### Troop Count Filters

```javascript
// Attacking troop thresholds
${regions.with({ minAttackingTroops: 5000 })}
${regions.with({ maxAttackingTroops: 10000 })}

// Defending troop thresholds
${regions.with({ minDefendingTroops: 2000 })}
${regions.with({ maxDefendingTroops: 8000 })}

// Total troop thresholds
${regions.with({ minTotalTroops: 7000 })}
${regions.with({ maxTotalTroops: 15000 })}
```

### Combining & Chaining Filters

```javascript
// Combine multiple conditions in a single query (AND logic)
${regions.with({ 
  type: "Coastal", 
  owner: thisCountry.name,
  minPopulation: 500000
})}

// Chain filters for more complex queries
${regions.with({ type: "Coastal" }).with({ borderingCountries: "EnemyCountry" })}
```

### Strategic Report Example

Below is a comprehensive example showing how to create a detailed strategic report using multiple filters:

```javascript
// This example shows how to create a comprehensive strategic report
// Replace "EnemyCountry1" and "EnemyCountry2" with actual enemy country names

`
# ${thisCountry.name} Strategic Analysis Report

## Territory Overview
Total Regions: ${Object.keys(regions.all).length}
Our Regions: ${regions.with({ owner: thisCountry.name })}
Straits Control: 
${regions.straitsAndOwners}

## Economic Analysis
Wealthiest Regions (GDP per capita > 30,000): 
${regions.with({ minGDPPerCapita: 30000 })}

Most Populous Regions (> 1M): 
${regions.with({ minPopulation: 1000000 })}

Our Economic Centers (Our regions with high GDP): 
${regions.with({ owner: thisCountry.name, minGDPPerCapita: 25000 })}

Development Targets (Our regions with low GDP): 
${regions.with({ owner: thisCountry.name, maxGDPPerCapita: 15000 })}

## Military Deployment
Our Troop Presence: 
${regions.with({ hasTroopsFrom: thisCountry.name })}

Our Offensive Operations: 
${regions.with({ hasAttackingTroopsFrom: thisCountry.name })}

Our Defensive Positions: 
${regions.with({ hasDefendingTroopsFrom: thisCountry.name })}

Forward Bases (Our troops in non-owned regions): 
${regions.with({ notOwner: thisCountry.name, hasTroopsFrom: thisCountry.name })}

## Border Security
Border Regions: 
${regions.with({ owner: thisCountry.name, borderingCountries: ["EnemyCountry1", "EnemyCountry2"] })}

Vulnerable Borders (Low defense): 
${regions.with({ 
  owner: thisCountry.name, 
  borderingCountries: ["EnemyCountry1", "EnemyCountry2"], 
  maxDefendingTroops: 2000 
})}

Heavily Fortified Borders: 
${regions.with({ 
  owner: thisCountry.name, 
  borderingCountries: ["EnemyCountry1", "EnemyCountry2"], 
  minDefendingTroops: 5000 
})}

## Expansion Opportunities
High-Value Targets (Enemy regions with high GDP bordering us): 
${regions.with({ 
  notOwner: thisCountry.name, 
  borderingCountries: thisCountry.name, 
  minGDPPerCapita: 25000 
})}

Vulnerable Targets (Enemy regions with low defense): 
${regions.with({ 
  notOwner: thisCountry.name, 
  borderingCountries: thisCountry.name, 
  maxDefendingTroops: 1000 
})}

## Naval Strategy
Strategic Straits: 
${regions.with({ type: "Strait" })}

Enemy-Controlled Straits: 
${regions.with({ type: "Strait", notOwner: thisCountry.name })}

Our Coastal Regions: 
${regions.with({ type: "Coastal", owner: thisCountry.name })}

## Threat Assessment
Regions Under Attack: 
${regions.with({ 
  owner: thisCountry.name, 
  minAttackingTroops: 1 
})}

Enemy Buildup Near Our Borders: 
${regions.with({ 
  notOwner: thisCountry.name, 
  borderingCountries: thisCountry.name, 
  minTotalTroops: 5000 
})}
`
```

### Technical Reference

```typescript
interface TransformedRegion {
    id: string;                 // Unique identifier
    name: string;               // Display name
    gdpPerCapita: number;       // Economic strength
    ownerID: string;            // ID of controlling country
    ownerName: string;          // Name of controlling country
    population: number;         // Population count
    type: 'Strait' | 'Coastal' | 'Land';  // Geographic type
    summerNavigability: number; // Summer navigation value
    winterNavigability: number; // Winter navigation value
    borderingRegions: string[]; // Names of adjacent regions
    borderingCountries: string[]; // Names of countries with adjacent regions
    troops: {                   // Battalions present in the region
        [battalionID: string]: Battalion;
    };
    toString: () => string;     // Returns region name
}

interface RegionFilterOptions {
    // Geographic filters
    minPopulation?: number;
    maxPopulation?: number;
    minGDPPerCapita?: number;
    maxGDPPerCapita?: number;
    name?: string;
    type?: 'Strait' | 'Coastal' | 'Land';
    
    // Ownership filters
    owner?: string; // country ID/name
    notOwner?: string | string[]; // country ID/name (ANY match)
    sameOwnerAs?: string | string[] | TransformedRegion | TransformedRegion[]; // Match if same as ANY
    differentOwnerThan?: string | string[] | TransformedRegion | TransformedRegion[]; // Match if different from ALL
    
    // Border filters
    borderingRegions?: string | string[] | TransformedRegion | TransformedRegion[]; // ALL must match
    borderingCountries?: string | string[]; // ALL must match
    
    // Troop presence filters
    hasTroops?: boolean;
    hasTroopsFrom?: string | string[]; // ANY match
    hasAttackingTroopsFrom?: string | string[]; // ANY match
    hasDefendingTroopsFrom?: string | string[]; // ANY match
    
    // Troop count filters
    minAttackingTroops?: number;
    maxAttackingTroops?: number;
    minDefendingTroops?: number;
    maxDefendingTroops?: number;
    minTotalTroops?: number;
    maxTotalTroops?: number;
}
```

