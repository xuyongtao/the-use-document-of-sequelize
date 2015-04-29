# the-use-document-of-sequelize 记录一下使用sequelize的文档

###1.软删除设置
  
  在对应的model文件设置 {paranoid: true};当你在model设置了后，以后的查询都不会把deleted_at不为null的数据查询出来；但有时我们需要那些被软删除的数据时，可在查询中加 {paranoid: false} 即可查出。
  
  软删除操作：UserModel.destroy({
                where: { id: userId }
            }, { force: false })
            
  软删除对应的恢复操作：restore方法 (http://sequelize.readthedocs.org/en/latest/api/instance/index.html?highlight=restore#restoreoptions-promiseundefined)

###2.多个model（表）关联有如下几个关系

(1)hasOne

(2)hasMany

(3)belongsTo

###3.跨表查询

可以用如 {include: UserModel},前提是由配置各个model（表）的关系，即第二点

###4.query

如果查询语句比较复杂，无法满足你的需求，可用sequelize.query('SELECT * .....')来实现

