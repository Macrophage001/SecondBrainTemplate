
I wanted to figure out what equations I would need in order to split progress into sections on the bar.

MaxOfflineTime::12
OfflineTimePerAd::3
AdsWatched::2


## Code:
---
```js
const maxOfflineTime = parseInt(dv.current().MaxOfflineTime);
const offlineTimePerAd = parseInt(dv.current().OfflineTimePerAd);
const adsWatched = parseInt(dv.current().AdsWatched);

const rate = offlineTimePerAd / maxOfflineTime;
const progress = (adsWatched * offlineTimePerAd) / maxOfflineTime;

const maxTicks = 1 / rate;
const ticks = progress / rate;


// Equivalent to 'console.log'
dv.el('p', `Rate ${rate}`);
dv.el('p', `Progress ${progress * 100}%`);

dv.el('p', `Max Ticks: ${maxTicks}`)
dv.el('p', `Ticks ${ticks}`);
```

## Results:
---
```dataviewjs
const maxOfflineTime = parseInt(dv.current().MaxOfflineTime);
const offlineTimePerAd = parseInt(dv.current().OfflineTimePerAd);
const adsWatched = parseInt(dv.current().AdsWatched);

const rate = offlineTimePerAd / maxOfflineTime;
const progress = (adsWatched * offlineTimePerAd) / maxOfflineTime;

const maxTicks = 1 / rate;
const ticks = progress / rate;

dv.el('p', `Rate ${rate}`);
dv.el('p', `Progress ${progress * 100}%`);

dv.el('p', `Max Ticks: ${maxTicks}`)
dv.el('p', `Ticks ${ticks}`);
```
