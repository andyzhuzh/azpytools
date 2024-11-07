
import pandas as pd

    # df['销售额'] = df['访客数'] * df['转化率'] * df['客单价']

if __name__ == '__main__':

    # 连接
    # dat_left 与dat_right 通过 dat_left.left_fields = dat_right.right_fields 关联
    # 结果放在dat_result中
    # excel.vlook(dat_left=r'E:\data\data1.xlsx',dat_right=r'E:\data\data2.xlsx',dat_result=r'E:\data\tresult_vlook.xlsx',left_fields=['matnr','mat1'],right_fields=["mat","mat_1"] )

    # 去重
    # excel.record_duplicates(file_in = r'E:\data\data1.xlsx',file_result=r'E:\data\tresult_duplicates.xlsx',fields = ['date1','uname'])

    # 排序
    # excel.record_sort(file_in = r'E:\data\data1.xlsx',file_result=r'E:\data\tresult_sort.xlsx',fields = ['date1','uname'],ascendings=[False,True] )

    #单元格数值替换 values_old,values_new
    # excel.record_replace(file_in = r'E:\data\data1.xlsx',file_result=r'E:\data\tresult_replace.xlsx',values_old= [r'.',150],values_new= ["",680])

    #单元格中字符替换 values_old,values_new
    # excel.cell_replace_char(file_in = r'E:\data\data1.xlsx',file_result=r'E:\data\tresult_replace_char.xlsx',fields = ['date1','uname'],values_old= r'.',values_new="")

    #负号提前
    excel.cell_sign_left(file_in = r'E:\data\data1.xlsx',file_result=r'E:\data\tresult_sign_left.xlsx',fields = ['QTY'])

    # 分组,汇总
    # excel.record__group(file_in = r'E:\data\data1.xlsx',file_result=r'E:\data\tresult_group.xlsx',fields = ['date1','uname'],field_sum = 'QTY')

    # 统计 date1 ，uname 记录数
    # excel.record_count(file_in = r'E:\data\data1.xlsx',file_result=r'E:\data\tresult_count.xlsx',fields = ['date1','uname'])




'''
以下是常用的处理excel 方法

# 对第english列进行修改
test_dict_df.loc[:,('english')]=[90,80,70,90,90,59]
#test_dict_df.loc[:,'english']=[90,80,70,90,90,59]
# 对第english列和id列进行修改，注意赋值的写法
test_dict_df.loc[:,('english','id')]=[[90,1],[80,2],[80,2],[80,2],[80,2],[80,2]]

# 对第1行进行修改
test_dict_df.loc[1:1,('english','id','math','name')]=[90,2,100,'Alice_m']
# 对第0行到第1行进行修改
test_dict_df.loc[0:1,('english','id','math','name')]=[[90,1,100,'Alice_m'],[70,2,100,'Bob']]
# 对第0行和第2行进行修改
test_dict_df.loc[0:3:2,('english','id','math','name')]=[[90,1,100,'Alice_m'],[70,2,100,'Bob']]


# 对第1、2行的english列和 id列进行修改
test_dict_df.loc[1:2,('english','id')]=[[38,2],[23,2]]

df2.drop_duplicates 去重
df.shape() # 查看⾏数和列数
df.columns() # 查看字段（⾸⾏）名称
df.describe() # 查看数值型列的汇总统计
df.apply(pd.Series.value_counts) # 查看DataFrame对象中每⼀列的唯⼀值和计数
df[df[column_name].duplicated()] # 查看column_name字段数据重复的数据信息
df[df[column_name].duplicated()].count() # 查看column_name字段数据重复的个数
df[[col1,col2]] # 以DataFrame形式返回多列
df.dropna() # 删除所有包含空值的⾏
s.replace([1,3],['one','three']) # ⽤'one'代替1，⽤'three'代替3
df.sort_values(col1) # 按照列col1排序数据，默认升序排列
df.sort_values(col2,ascending=False) # 按照列col1降序排列数据

df1.append(df2) # 将df2中的⾏添加到df1的尾部
df.groupby([col1,col2]) # 返回⼀个按多列进⾏分组的Groupby对象
df.groupby(col1)[col2].agg(mean) # 返回按列col1进⾏分组后，列col2的均值,agg可以接受列表参数，agg([len,np.mean])


df.head(n) # 查看DataFrame对象的前n⾏
df.tail(n) # 查看DataFrame对象的最后n⾏
df.info() # 查看索引、数据类型和内存信息
 s.value_counts(dropna=False) # 查看Series对象的唯⼀值和计数
df.isnull().any() # 查看是否有缺失值
df[col] # 根据列名，并以Series的形式返回列
s.iloc[0] # 按位置选取数据
s.loc['index_one'] # 按索引选取数据
df.iloc[0,:] # 返回第⼀⾏
df.iloc[0,0] # 返回第⼀列的第⼀个元素
df.loc[0,:] # 返回第⼀⾏（索引为默认的数字时，⽤法同df.iloc），但需要注意的是loc是按索引,iloc参数只接受数字参数
df.ix[[:5],["col1","col2"]] # 返回字段为col1和col2的前5条数据，可以理解为loc和iloc的结合体。
df.at[5,"col1"] # 选择索引名称为5，字段名称为col1的数据
df.iat[5,0] # 选择索引排序为5，字段排序为0的数据
df.columns= ['a','b','c'] # 重命名列名（需要将所有列名列出，否则会报错）
pd.isnull() # 检查DataFrame对象中的空值，并返回⼀个Boolean数组
pd.notnull() # 检查DataFrame对象中的⾮空值，并返回⼀个Boolean数组
df.dropna(axis=1) # 删除所有包含空值的列
df.dropna(axis=1,thresh=n) # 删除所有⼩于n个⾮空值的⾏
df.fillna(value=x) # ⽤x替换DataFrame对象中所有的空值，⽀持
df[column_name].fillna(x)
s.astype(float) # 将Series中的数据类型更改为float类型
s.replace(1,'one') # ⽤‘one'代替所有等于1的值
df.rename(columns=lambdax:x+1) # 批量更改列名
df.rename(columns={'old_name':'new_ name'}) # 选择性更改列名
df.set_index('column_one') # 将某个字段设为索引，可接受列表参数，即设置多个索引
df.reset_index("col1") # 将索引设置为col1字段，并将索引新设置为0,1,2..
df.rename(index=lambdax:x+1) # 批量重命名索引
df.sort_index().loc[:5] # 对前5条数据进⾏索引排
df.groupby(col) # 返回⼀个按列col进⾏分组的Groupby对象
df.groupby([col1,col2]) # 返回⼀个按多列进⾏分组的Groupby对象
df.groupby(col1)[col2].agg(mean) # 返回按列col1进⾏分组后，列col2的均值,agg可以接受列表参数，agg([len,np.mean])
df.pivot_table(index=col1,values=[col2,col3],aggfunc={col2:max,col3:[ma,min]}) # 创建⼀个按列col1进⾏分组，计算col2的最⼤值和col3的最⼤值、最⼩值的数据透视表
df.groupby(col1).agg(np.mean) # 返回按列col1分组的所有列的均值,⽀持
df.groupby(col1).col2.agg(['min','max'])
data.apply(np.mean) # 对DataFrame中的每⼀列应⽤函数np.mean
data.apply(np.max,axis=1) # 对DataFrame中的每⼀⾏应⽤函数np.max
df.groupby(col1).col2.transform("sum") # 通常与groupby连⽤，避免索引更改
df.concat([df1,df2],axis=1,join='inner') # 将df2中的列添加到df1的尾部,值为空的对应⾏与对应列都不要
df1.join(df2.set_index(col1),on=col1,how='inner') # 对df1的列和df2的列执⾏SQL形式的join，默认按照索引来进⾏合并，如果df1和df2有共同字段时，会报错，可通过设置lsuffix,rsuffix来进⾏解决，如果需要按照共同列进⾏合并，就要⽤到set_index(col1)
pd.merge(df1,df2,on='col1',how='outer') # 对df1和df2合并，按照col1，⽅式为outer
pd.merge(df1,df2,left_index=True,right_index=True,how='outer') #与 df1.join(df2, how='outer')效果相同
'''