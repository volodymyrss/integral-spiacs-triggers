# Preliminary!

# Distributing INTEGRAL SPI-ACS triggers

Some ACS triggers are not distributed due to telemetry interruptions (as in case of 20200826_T79782) which temporarily disrupt buffer of the IBAS ACS trigger, preventing background estimation and hence detection.  In other cases - it is due to unusual or unstable background: it's hard to discriminate background reliably with only one channel,  especially with short latency (i.e. without background after the event). Also, IBAS ACS uses some basic discrimination for the CR-induced short spikes, which dismisses some real events as well.

I looked deeply in this software, it's a complex and old but well-written multi-threaded C code, it was written by Jerzy Borkowski and Arne Rau, and later modified by us here in Geneva.

Eventually, GCN Notices are only sent, in realtime (tens of seconds delay) for a subset of the events:

https://gcn.gsfc.nasa.gov/integral_spiacs.html

We could easily tune this pipeline, adjusting the significance thresholds and timescales. 

* * *

In addition, an variation of this pipeline is linked to another, more elaborate, realtime search (following VS2012, but adopted to account for lack of background after the event, and with restricted classification capabilities), which produces a large rate of prelimiary events.

* * *

Finally there is an offline search (following VS2012 pretty much completely) which runs with few hour delay, allowing for better background estimate, using other instruments, and CR discrimination based on the temporal properties.
The problem remains that it is hard to characterize the events, but it yields much more events.
We regularly discuss these detections in context of the IPN. Usually, they yield useful candidates.
This is also used to re-classify the events.
Since for GUANO this seems too late (more than 20 min), only the  re-classification would be possibly useful here.

* * *

There is also an additional near-realtime pipeline searching for signal in ACS and IBIS/PICsIT by association with other known events of all kinds. This produces a lot of events, including, for example the majority of the GBM events. 
But I guess GUANO already uses all of these external triggers?

* * *

Eventually, the results of these pipelines are recorded e.g. here:

https://www.isdc.unige.ch/integral/ibas/cgi-bin/ibas_acs_web.cgi?month=current

We considered adding more events to the GCN IBAS stream, but in principle, it would require other notice types: "IBAS ACS sub-threshold", "IBAS ACS offline", "IBAS Association", "IBIS PICsIT" etc, and hence some discussion with Scott.
It not been a high priority since there are very few interested consumers for this additional stream, since it is not sufficiently pure. It recovers some bright events (like 20200826_T79782) but such misses are rather exceptional (even if, unfortunately, regular and inevitable in realtime IBAS).

Turned out that instead of yielding a moderately pure additional offline and subthreshold stream of INTEGRAL (ACS and IBIS), it is much more useful to provide easy on-demand access to the public data.
These data are used routinely in IPN as well as multiple other instrument teams (of course Konus, GBM, CALET, Insight, BAT, etc) in order to confirm events and derive triangulations.

There is a note here:

https://github.com/volodymyrss/integral-spi-acs-data/

But, if someone is interested in such a stream, we can provide it, e.g. in VOEvent. Or, if justified, we can finally share it over GCN Notice.
And of course, we can simply adjust the thresholds of the current ACS stream, very easily.

# Extra Metadata

|  | |
| --- | :-- |
| AKA | https://gitlab.unige.ch/Volodymyr.Savchenko/integral-spi-acs-data | 
| AKA | https://gitlab.astro.unige.ch/savchenk/integral-spi-acs-data | 

