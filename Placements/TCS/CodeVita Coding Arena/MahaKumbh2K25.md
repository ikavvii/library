### Problem Description

1. The Kumbh is a massive spiritual event held every 12 years in India, attracting millions of pilgrims. Every 12th Kumbh which comes after 144 years of previous Maha Kumbh is the most recent Maha Kumbh. Most recent such Maha Kumbh happened in 2025. This influx of devotees puts significant pressure on transportation services, especially the railways.

This grand spiritual event takes place at the sacred confluence of the Ganga, Yamuna, and the Saraswati rivers. During this time, millions of people travel from various nearby cities to participate in the holy festival, which is believed to cleanse the soul and wash away sins through a sacred dip at the confluence.

Due to the massive number of travellers, transport services around the festival site experience heavy rush and delays. Among all available modes of transport, the railways become the most preferred and widely used service by the devotees. As a result, railway stations and trains get extremely crowded, and managing the smooth movement of trains becomes a major challenge for the authorities.

To accommodate heightened demand, railway officials systematically oversee and adjust track connections throughout the day. Their main activities include:

1. Disconnecting certain tracks between stations to divert train routes and manage traffic.
2. Connecting tracks between stations to create new travel routes as needed.

Additionally, ongoing railway construction can restrict some trains from passing through specific stations. These restrictions apply only to trains starting from certain source stations.

Many families travel according to their own priorities and schedules. Before traveling, they need to check if a valid route exists from their starting station to their destination, considering the latest track arrangements and any restrictions.

### Constraints

2 <= N, Q, R <= 14

### Input

The first line contains a single integer, _N_, indicating the number of lines that define station connections.

Lines **2** to **N+1** show each source station and its connected stations as follows:

_source_station, station1, station2 ... stationK_ (Connections are bidirectional.)

Line **N+2** contains single integer _Q_ - representing the number of queries.

The following Q lines, i. e. lines **N+3** to **N+Q+2** contains _Q_ queries in the below format.

- _source_station to destination_station_: Check if travel is possible between these stations.
- _station1 connects station2_: Connect these two stations.
- _station1 disconnects station2_: Disconnect these two stations.

The next line, Line **N+Q+3** contains a single integer, _R_, indicating the number of restriction lines.

The following R lines (N+Q+4 to N+Q+R+3) specify restrictions in this format:

_source_station, restricted_station1, restricted_station2.... restricted_stationM._

_(Trains starting from source_station cannot pass through the listed restricted stations.)_

### Output

For each travel query, output "yes" or "no" (without quotes) on a separate line, indicating whether the journey is possible.

### Time Limit (secs)

1

### Examples

Example 1

Input

3

prayagraj varanasi chitrakoot

chitrakoot ayodhya lucknow vindhyachal

sarnath ayodhya chitrakoot kushinagar jaunpur

5

prayagraj to jaunpur

prayagraj connects kushinagar

prayagraj to jaunpur

prayagraj disconnects kushinagar

prayagraj to sarnath

2

chitrakoot jaunpur varanasi

prayagraj ayodhya

Output

yes

yes

yes

Explanation

Initial connections between the stations are as follows:
![](attachments/Pasted%20image%2020260925222713.png)


When the first query is checked, the answer is visibly "yes", people can travel from _prayagraj_ to _jaunpur_. There are multiple paths to go from _prayagraj_ to _jaunpur_ which includes one path containing _ayodhya_, but we must exclude that path considering the restrictions.

The second query states that the track between _prayagraj_ and _kushinagar_ gets connected. After this, when the third query is checked, the answer is "yes", people can travel from _prayagraj_ to _jaunpur_.

The fourth query states that the track between _prayagraj_ to _kushinagar_ gets disconnected. After this, when the fifth query is checked, the answer remains "yes", people can travel through _prayagraj_ to _sarnath_.

Example 2

Input

3

prayagraj varanasi chitrakoot

chitrakoot ayodhya lucknow vindhyachal

sarnath ayodhya kushinagar jaunpur

5

prayagraj to jaunpur

prayagraj connects kushinagar

prayagraj to jaunpur

prayagraj disconnects kushinagar

prayagraj to sarnath

2

chitrakoot jaunpur varanasi

prayagraj ayodhya

Output

no

yes

no

Explanation

The initial connections between the stations are as follows:
![](attachments/Pasted%20image%2020260925222732.png)


When the first query is checked, the answer is "no" because there is only one path from _prayagraj_ to _jaunpur_ which includes visiting _ayodhya_. We must exclude that path because of the restrictions provided.

When the second query is executed, the track between _pyaragraj_ to _kushinagar_ is connected. Now when checking for the third query, the answer is "yes" as we have multiple paths going from _prayagraj_ to _jaunpur_.

When the fourth query is executed, the path beween _prayagraj_ and _kushinagar_ is disconnected.

When checking for the fifth query, the answer is "no" because for going from _prayagraj_ to _sarnath_, there is only one path, which passes through _ayodhya_ which is restricted if the train's source station is _prayagraj_.