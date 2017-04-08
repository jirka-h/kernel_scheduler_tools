# Kernel Scheduler Tools

There are the tools to debug Linux Kernel Scheduler derived from https://github.com/jirka-h/wastedcores and inspired by this paper https://www.ece.ubc.ca/~sasha/papers/eurosys16-final29.pdf

### Directories:

* `sched_profiler` - kernel patches and kernel module to debug the scheduler. It records several scheduler events and allows to create graphs displaying the run queue for each CPU over time and how scheduler moves the threads around. Events are:
  * set_sp_module_set_nr_running
  * set_sp_module_record_scheduling_event
  * set_sp_module_record_balancing_event
  * set_sp_module_record_load_change

* `invariants` - kernel patches and kernel module to verify that following scheduler invariants are not violated for high number of CPU cycles. Systemtap can be used to automatically dump execution traces of load balancing calls that failed to balance the load. 
  * invariant 1: no idle cpu while another CPU is overloaded
  * invariant 2: Check that all threads have a similar "deficit" in runtime. NOT USED.
  * invariant 3: no useless migration

After discussion with Radim Krcmar the goal is to rewrite sched_profiler events using kernel traces and propose the change to the upstream. 

Patch files are stored in the directory `trace_events`




