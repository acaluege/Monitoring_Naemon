# If you want to fill this file with all avalible options run the following command:
#   nscp settings --generate --add-defaults --load-all
# If you want to activate a module and bring in all its options use:
#   nscp settings --activate-module <MODULE NAME> --add-defaults
# For details run: nscp settings --help


; Undocumented section
[/modules]

; CheckDisk - CheckDisk can check various file and disk related things. The current version has commands to check Size of hard drives and directories.
CheckDisk = 1

; Event log Checker. - Check for errors and warnings in the event log. This is only supported through NRPE so if you plan to use only NSClient this wont help you at all.
CheckEventLog = 1

; Check External Scripts - A simple wrapper to run external scripts and batch files.
CheckExternalScripts = 1

; Helper function - Various helper function to extend other checks. This is also only supported through NRPE.
CheckHelpers = 1

; Check NSCP - Checkes the state of the agent
CheckNSCP = 1

; CheckSystem - Various system related checks, such as CPU load, process state, service state memory usage and PDH counters.
CheckSystem = 1

; NSClient server - A simple server that listens for incoming NSClient (check_nt) connection and handles them. Although NRPE is the preferred method NSClient is fully supported and can be used for simplicity or for compatibility.
NSClientServer = 1


; Undocumented section
[/settings/default]

; ALLOWED HOSTS - A comaseparated list of allowed hosts. You can use netmasks (/ syntax) or * to create ranges.
allowed hosts = 192.168.232.137


; A list of aliases available. An alias is an internal command that has been "wrapped" (to add arguments). Be careful so you don't create loops (ie check_loop=check_a, check_a=check_loop)
[/settings/external scripts/alias]

; alias_cpu - Alias for alias_cpu. To configure this item add a section called: /settings/external scripts/alias/alias_cpu
alias_cpu = checkCPU warn=80 crit=90 time=5m time=1m time=30s

; alias_cpu_ex - Alias for alias_cpu_ex. To configure this item add a section called: /settings/external scripts/alias/alias_cpu_ex
alias_cpu_ex = checkCPU warn=$ARG1$ crit=$ARG2$ time=5m time=1m time=30s

; alias_disk - Alias for alias_disk. To configure this item add a section called: /settings/external scripts/alias/alias_disk
alias_disk = CheckDriveSize MinWarn=10% MinCrit=5% CheckAll FilterType=FIXED

; alias_disk_loose - Alias for alias_disk_loose. To configure this item add a section called: /settings/external scripts/alias/alias_disk_loose
alias_disk_loose = CheckDriveSize MinWarn=10% MinCrit=5% CheckAll FilterType=FIXED ignore-unreadable

; alias_event_log - Alias for alias_event_log. To configure this item add a section called: /settings/external scripts/alias/alias_event_log
alias_event_log = CheckEventLog file=application file=system MaxWarn=1 MaxCrit=1 "filter=generated gt -2d AND severity NOT IN ('success', 'informational') AND source != 'SideBySide'" truncate=800 unique descriptions "syntax=%severity%: %source%: %message% (%count%)"

; alias_file_age - Alias for alias_file_age. To configure this item add a section called: /settings/external scripts/alias/alias_file_age
alias_file_age = checkFile2 filter=out "file=$ARG1$" filter-written=>1d MaxWarn=1 MaxCrit=1 "syntax=%filename% %write%"

; alias_file_size - Alias for alias_file_size. To configure this item add a section called: /settings/external scripts/alias/alias_file_size
alias_file_size = CheckFiles "filter=size > $ARG2$" "path=$ARG1$" MaxWarn=1 MaxCrit=1 "syntax=%filename% %size%" max-dir-depth=10

; alias_mem - Alias for alias_mem. To configure this item add a section called: /settings/external scripts/alias/alias_mem
alias_mem = checkMem MaxWarn=80% MaxCrit=90% ShowAll=long type=physical type=virtual type=paged type=page

; alias_process - Alias for alias_process. To configure this item add a section called: /settings/external scripts/alias/alias_process
alias_process = checkProcState "$ARG1$=started"

; alias_process_count - Alias for alias_process_count. To configure this item add a section called: /settings/external scripts/alias/alias_process_count
alias_process_count = checkProcState MaxWarnCount=$ARG2$ MaxCritCount=$ARG3$ "$ARG1$=started"

; alias_process_hung - Alias for alias_process_hung. To configure this item add a section called: /settings/external scripts/alias/alias_process_hung
alias_process_hung = checkProcState MaxWarnCount=1 MaxCritCount=1 "$ARG1$=hung"

; alias_process_stopped - Alias for alias_process_stopped. To configure this item add a section called: /settings/external scripts/alias/alias_process_stopped
alias_process_stopped = checkProcState "$ARG1$=stopped"

; alias_sched_all - Alias for alias_sched_all. To configure this item add a section called: /settings/external scripts/alias/alias_sched_all
alias_sched_all = CheckTaskSched "filter=exit_code ne 0" "syntax=%title%: %exit_code%" warn=>0

; alias_sched_long - Alias for alias_sched_long. To configure this item add a section called: /settings/external scripts/alias/alias_sched_long
alias_sched_long = CheckTaskSched "filter=status = 'running' AND most_recent_run_time < -$ARG1$" "syntax=%title% (%most_recent_run_time%)" warn=>0

; alias_sched_task - Alias for alias_sched_task. To configure this item add a section called: /settings/external scripts/alias/alias_sched_task
alias_sched_task = CheckTaskSched "filter=title eq '$ARG1$' AND exit_code ne 0" "syntax=%title% (%most_recent_run_time%)" warn=>0

; alias_service - Alias for alias_service. To configure this item add a section called: /settings/external scripts/alias/alias_service
alias_service = checkServiceState CheckAll

; alias_service_ex - Alias for alias_service_ex. To configure this item add a section called: /settings/external scripts/alias/alias_service_ex
alias_service_ex = checkServiceState CheckAll "exclude=Net Driver HPZ12" "exclude=Pml Driver HPZ12" exclude=stisvc

; alias_up - Alias for alias_up. To configure this item add a section called: /settings/external scripts/alias/alias_up
alias_up = checkUpTime MinWarn=1d MinWarn=1h

; alias_updates - Alias for alias_updates. To configure this item add a section called: /settings/external scripts/alias/alias_updates
alias_updates = check_updates -warning 0 -critical 0

; alias_volumes - Alias for alias_volumes. To configure this item add a section called: /settings/external scripts/alias/alias_volumes
alias_volumes = CheckDriveSize MinWarn=10% MinCrit=5% CheckAll=volumes FilterType=FIXED

; alias_volumes_loose - Alias for alias_volumes_loose. To configure this item add a section called: /settings/external scripts/alias/alias_volumes_loose
alias_volumes_loose = CheckDriveSize MinWarn=10% MinCrit=5% CheckAll=volumes FilterType=FIXED ignore-unreadable 

; default - Alias for default. To configure this item add a section called: /settings/external scripts/alias/default
default =   