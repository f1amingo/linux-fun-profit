# 文件系统

物理上，磁盘只有0和1的信息，这对于用户是不可读的。

文件系统，就是用户和磁盘之间的一种“翻译”机制，在Linux中采用的是文件系统+虚拟文件系统（Virtual File System，VFS）的解决方案。

Linux支持多种不同的文件系统，包括ext2、ext3、ext4、zfs、iso9660、vfat、msdos、smbfs、nfs等，还能通过加载其他模块的方式支持更多的文件系统。

虽然文件系统多种多样，但是大部分Linux系统都具有类似的通用结构，包括超级块（superblock）、i节点（inode）、数据块（datablock）、目录块（directory block）等。

# 磁盘分区

磁盘使用前需要对其进行分割，这种动作被形象地称为分区。磁盘的分区分为两类，即主分区和扩展分区。