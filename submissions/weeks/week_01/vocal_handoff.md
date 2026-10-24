# HANDOFF

```text
butterflai2 | week: 01 | turns: 6

- student: Name: ## Resources \nContent: []
- priors: none
- anchors: independent increments, null model, overdispersion, negative log-likelihood, Earth Mover's Distance
- self-check: none

point processes: point process | level: 2 | milestone: none | anchor: none
point process | claim: yes | prior: none | end: deployed | "To treat the catalog as a point process we have to commit to one event time per group."
event time | claim: yes | prior: none | end: deployed | "an event is a group's first observation: the first day it appears in the catalog"
counting process | claim: yes | prior: none | end: deployed | "The counting process N(s) is the number of events that have happened by time s."
inter-arrival time | claim: yes | prior: none | end: deployed | "The inter-arrival time is the gap between consecutive events."
Poisson process | claim: yes | prior: none | end: deployed | "A Poisson process is the point process with no memory"
independent increments | claim: yes | prior: none | end: deployed | "given its rate, what happens in one interval tells you nothing about any other, a property called independent increments"
memoryless | claim: yes | prior: none | end: deployed | "Equivalently it is memoryless — having waited ten days... does not change the distribution"
Fano factor | claim: yes | prior: none | end: deployed | "Var(counts in windows of width Delta) / Mean(counts in windows of width Delta) equals 1"
overdispersion | claim: yes | prior: none | end: deployed | "If F > 1 the counts are more variable than Poisson — overdispersion, the signature of events arriving in clumps"

statistical inference: statistical inference | level: 2 | milestone: none | anchor: none
negative log-likelihood | claim: yes | prior: none | end: deployed | "negative log-likelihood of an event is -log p, and the score for a dataset is the average"
Earth Mover's Distance | claim: yes | prior: none | end: deployed | "The Earth Mover's Distance between two distributions is the smallest amount of work..."
null model | claim: yes | prior: none | end: deployed | "To make F(Delta) say anything, we need... a null model: a process built to share with the data..."

solar cycle physics: solar cycle physics | level: 2 | milestone: none | anchor: none
emergence | claim: yes | prior: none | end: deployed | "First observation is not emergence. Recorded time lags true emergence by up to several days..."
hemispheric cycle | claim: yes | prior: none | end: deployed | "The unit of replication in this program is the hemispheric cycle: the north and the south..."
alignment coordinate | claim: yes | prior: none | end: deployed | "alignment coordinate s is the time in years since that wing's mean latitude crossed 15 degrees"

other deployed: none
other open: none
