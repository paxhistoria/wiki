# 🏭 countries

```javascript
`
  Active Countries: ${countries.with({ isPuppet: false })}
  Puppet Countries: ${countries.with({ isPuppet: true })}
  Countries bordering ${thisCountry.name}: ${countries.with({ borderingCountry: thisCountry.name })}
  Countries with Master: ${countries.with({ master: thisCountry.master })}
  Countries with Min Core Population: ${countries.with({ minCorePopulation: thisCountry.corePopulation })}
  Countries with Max Core Population: ${countries.with({ maxCorePopulation: thisCountry.corePopulation })}
  Countries with Puppets: ${countries.with({ puppets: thisCountry.name })}
`
```

include the output examples bc the default toString will just be a comma separated list of the country names
