---
description: Object used in prompt templates
---

# 🧩 thisCountry

**About**

The 'thisCountry' object represents a specific country within the [countries](countries.md) object.&#x20;

When a country needs to make a decision in the game (like to plan actions, respond to chats, etc) the game will turn mentions of 'thisCountry' within your prompt into a reference to the country that needs to make a decision.  &#x20;

**Names**

```tsx
`
Country Name: ${thisCountry.name}
Country ID: ${thisCountry.countryId}
Possessive Name: ${thisCountry.possessiveName}
Name as Puppet: ${thisCountry.nameAsPuppet}
Name in Sentence: ${thisCountry.nameInSentence}
`
```

**Guidance**

```tsx
`
Guidance: ${thisCountry.guidance || 'No Guidance'}
`
```

**Statistics**

```tsx
`
Core Population: ${thisCountry.corePopulation}
Tax Payers: ${thisCountry.taxPayers}
Tax Rate: ${thisCountry.taxRate}%
GDP Per Capita: $${thisCountry.gdpPerCapita}
Government Coffers: $${thisCountry.governmentCoffers}
`
```

**Puppet Status**

```tsx
`
Master: ${thisCountry.master || 'No Master'}
Is Puppet: ${thisCountry.isPuppet}
Independence Description: ${thisCountry.independenceDescription}
Puppets: ${thisCountry.puppets}
`
```

**Military**

```tsx
`
Defending Troops: ${thisCountry.defendingTroops}
Defending Troops Set Point: ${thisCountry.defendingTroopsSetPoint}%
Military Efficiency: ${thisCountry.militaryEfficiency}%
Given Military Access: ${thisCountry.givenMilitaryAccess}
Received Military Access: ${thisCountry.receivedMilitaryAccess}
`
```

**Geography**

```tsx
`
Bordering Countries: ${thisCountry.borderingCountries}
Regions: ${thisCountry.regions}
Bordering Regions: ${thisCountry.borderingRegions}
Distant Regions: ${thisCountry.distantAttackableRegions}
Is Coastal: ${thisCountry.isCoastal}
`
```

**Example Template**

Here's how you can generate a comprehensive report for a country:

```javascript
return `
[Country Names]
Country Name: ${thisCountry.name}
Country ID: ${thisCountry.countryId}
Possessive Name: ${thisCountry.possessiveName}
Name as Puppet: ${thisCountry.nameAsPuppet}
Name in Sentence: ${thisCountry.nameInSentence}

[Guidance]
Guidance: ${thisCountry.guidance || 'No Guidance'}

[Statistics]
Core Population: ${thisCountry.corePopulation}
Tax Payers: ${thisCountry.taxPayers}
Tax Rate: ${thisCountry.taxRate}%
GDP Per Capita: $${thisCountry.gdpPerCapita}
Government Coffers: $${thisCountry.governmentCoffers}

[Puppet Status]
Master: ${thisCountry.master || 'No Master'}
Is Puppet: ${thisCountry.isPuppet}
Independence Description: ${thisCountry.independenceDescription}
Puppets: ${thisCountry.puppets}

[Military]
Defending Troops: ${thisCountry.defendingTroops}
Defending Troops Set Point: ${thisCountry.defendingTroopsSetPoint}%
Military Efficiency: ${thisCountry.militaryEfficiency}%
Given Military Access: ${thisCountry.givenMilitaryAccess}
Received Military Access: ${thisCountry.receivedMilitaryAccess}

[Geography]
Bordering Countries: ${thisCountry.borderingCountries}
Regions: ${thisCountry.regions}
Bordering Regions: ${thisCountry.borderingRegions}
Distant Regions: ${thisCountry.distantAttackableRegions}
Is Coastal: ${thisCountry.isCoastal}
`;

```
