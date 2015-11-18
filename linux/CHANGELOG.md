
# CHANGELOG

v2.8.4.3
- Release Date: 2015-10-7
- 改进Firmware Version显示，在原有git tag基础上，添加对应具体版本号，如3.2
- 集成grantly平台驱动，后续浪潮服务器不再需要定制驱动
> 升级建议：该版本主要是提供给浪潮使用，其他客户可以忽略

v2.8.4.2
- Release Date: 2015-9-23
- 修正一个系统时间设置错误引起的refresh MBR bug  
> 升级建议：2.8.4版本驱动需要尽快升级此版本，原2.8.4版本驱动不再分发给客户

v2.8.4
- Release Date: 2015-8-7
- add refresh_mbr function
- add atomic_write/prioritize_write support
- fix shannon_force_rw bug
- add some new flash IDs
- add Oracle linux driver  
> 升级建议：暂无。要注意，使用这个版本驱动及以后的驱动，shannon-format格式化以后将会MBR变成4K模式，2.8.2以下的驱动将读不出MBR,mkfs格式化MBR不受影响。

v2.8.3
- Release Date: 2015-7-2
- 支持OP设置到10%以下，最低4%
- 支持Debian 8  
> 升级建议，没有OP特定设置需求的客户可以忽略该版本

v2.8.2
- Release Date: 2015-06.04
- Support New Micron and Toshiba nand flashchip. Shipped from late May in 2015.
- Support 4K format MBR.  
> 升级建议: 
> * This is a hotfix verison
> * When 2.8.1 not work and dmesg shows "shannon_probe(): can't read flashid or flashid isn't supported  shannon_probe(): ERROR: cannot read mbr. " Please upgrade Direct-IO Driver for Linux to 2.8.2

v2.8.1
- Release Date: 2015-02.05
- add: Support new Micron Flash module. A19.
- bugfix: fix an critical issue.  
> 升级建议: 所有新客户采用此版本驱动.所有在生产环境部署的Direct-IO设备必须升级为该版本或之后版本.

v2.8.0
- Release Date: 2015-01.24
- feature: add FPGA reconfig support, this feature may reduce probability of Direct-IO became readonly status caused by SEU.  
> 升级建议: 所有新客户采用此版本驱动.部署规模达到100片以上的客户,建议升级.

v2.7.9
- Release Date: 2014-12.17
- 修改SEU保护触发判断逻辑,降低误报概率.  
> 升级建议: 所有新客户采用此版本驱动.部署规模达到100片以上的客户,建议升级.

v2.7.8
- Release Date: 2014-11-13
- sysfs和shannon-utils显示SEU flag等SEU信息.
- 添加镁光 32GB L84C 闪存支持. 
- sysfs dir and shannon-utils will output SEU flag info.
- add Micron 32GB L84C support.  
> 升级建议:所有新客户采用最新版本驱动,已经升级为上以版本(2.7.6)驱动的客户,建议单独升级shannon-utils这个包,部署规模达到100片以上的客户,请尽量升级shannon-utils包到2.7.8版本.

v2.7.6
- Release Date: 2014-9-17
- bugfix: fix issues on Multi socket AMD CPU platform, AMD specific driver will be no longer provided separately in future. All AMD Platform must use this version(or above).
- bugfix: 修正Multi socket AMD CPU平台下的问题，不再提供AMD平台专用驱动 ,所有AMD平台的场景必须使用此版本驱动(或更高).

v2.7.5
- Release Date: 2014-9-17
- add: Support Micron 32GB Flash module, which is used on Fiji 600GB product, AKA Direct-IO G3S 600. All G3S 600 Direct-IO card must use this viersion(o abover).
- add: 支持使用Micron(镁光) 32GB Flash的Fiji 600GB产品, 即Direct-IO G3S 600 . 所有 G3S 600 的卡必须使用本版本(或更高)驱动.



