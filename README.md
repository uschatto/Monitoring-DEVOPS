# HW4-Monitoring

**CONCEPTUAL QUESTIONS**
> *Compare a channel deployment model with a ring deployment model.*
<p align="justify">Mozilla uses channel model to perform rapid releases. Changes are grouped and tested in channels. For example, if there are several commits made they are grouped together and tested. If the release engineer feels a commit has passed all test results, it is pushed to the next channel. If in case a commit is extremely important for a release then it is fast tracked and pushed directly to the release channel. While they are in the channel, the company not only run their internal testing but also corporate customer specific testing used by IBM etc. By the time all the changes that have made it to the release candidates, it is already 6 weeks then these changes are packaged and pushed together to be updated by the customers. The cost of delivering here is pretty high where you can easily roll back and do a lot of testing upfront.</p>

<p align="justify">On the other hand Microsoft uses ring model. Instead of channels, the changes are tested and promoted in rings of internal users. Whenever a change is committed, the early developers who are internal users will test the change. Slowly the change will be pushed to the outer ring with testing from wider groups of users. To leave a ring, the users will need to manually sign off or pass more advanced testing.</p>

<p align="justify">In channel model, all the changes are promoted to the next channel at once where as in the ring model only a selective changes could be promoted to the next ring. The number of people exposed to that change also varies.</p>

> *Identify 2 situations where an expand/contract deployment could be useful.*
<p align="justify">A situation where the schema of a database need to be changed. If one column needs to be splitted into two columns, this deployment model could be useful where the new schema is deployed, data is migrated and once the old data is migrated the old schema is removed without any downtime. The other scenario is when the datatype of a field changes, this change also needs to be deployed everywhere else type errors can be reported or there could be truncation of values or overflowing values which can be fatal to the business.</p>

> *What are some tradeoffs associated with dark launches?*
<p align="justify">The benefits of using dark launches are as follows: No release branches which can help eliminate the need to support long-running release branch and reduce merge issues. It also allows stability and experimentation.Developer can test in production like test load speeds for recent images without user needing to see. Can conditionally turn on for some segments of users to gather usage data. Improve disaster recovery. No rollback, just turn off feature. 

However the issues with using dark launching are as follows: Technical debt like removing flags is a highly variable practice. Reusing old flags can be disastrous. Mixed experiences like Inconsistent user experiences can reduce satisfaction. Stability like Supporting multiple permutations of software can increase engineering costs and reduce stability. </p>

> *Describe the Netflix style green-blue deployment. What can canary analysis tell us?*
<p align="justify">Blue-green deployment involves having a live green instance which has the newly deployed changes. The live traffic flows through this instance. The proxy connects to the green instance as well as the blue failover instance. Whenever a commit is made which turns out to be a bad one, the healthchecker detects the same and failsover to the blue instance. The advantage of this deployment is that the rollback is seamless but the disadvantage is that the infrastructure cost rises up because of double the amount of infrastructure needed now. The migration of live data can be complex. The netflix style of deployment first builds an image for the microservice, then builds clusters via spinnaker and then does the redblack deployment. Canary analysis can tell whether a deployment can be safely promoted to more and more users. Each metric is classified as either “Pass”, “High”, or “Low”, based on confidence intervals, computed by the Mann-Whitney U test, to classify whether a significant difference exists between the canary and baseline metrics. The canary score is calculated as the ratio of metrics classified as “Pass” out of the total number of metrics. </p>


<p align="center"> 
<img src="https://media.github.ncsu.edu/user/12214/files/1e62d600-84f1-11ea-8e2a-1119673265de" width="800" height="200">
</p>

[*SCREENCAST*](https://drive.google.com/open?id=14738bN3TlmcxQBwz9jAqdYm2j1Uhxduk)
