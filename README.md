
### 7_17_2018
- 虚拟机:  paul.bi	    SHVM00813	172.30.4.134
- 项目: http://172.25.17.39:8080/ls/loginPage.do
- user:                      **paul**
   password:           **eBao123**
- 员工信息   http://staff.ebaotech.com/ls/mainMenu.do
- TeamForge工作空间:    https://alm.ebaotech.com/sf/sfmain/do/myPage 
- 项目测试文档:     https://test.ebaotech.com/SpiraTest

### 7_19_2018
- 修改jre:Default VM arguments  -Xms256m -Xmx512m
- 在 tomcat的Arguments最后面加-Xms256m -Xmx512m -XX:PermSize=256M -XX:MaxPermSize=512M
- 修改tomcat下ls.xml的docBase为自己的目录
### 7_20_2018
- 运行中的jdk7+tomcat6 + 不运行的jdk6+tomcat5 + 系统环境变量为tomcat5
### 7_23_2018
- 将E:\workspaceSVN\AssetLink\trunk\lib下所有jar包添加到WEB-INF下的lib文件夹中
- 修改Tomcat下Classpath的User Entries为当前工程trunk\app_config\local
- 登入p盘\\shdoc01\fs$
- paul.bi@ebaotech.com Project Code : **7103698 - SL AL Maintenance**
- PT2619	Paul Bi	SEA - SBM1 Segment - 2

### 7_26_2018
- 测试: **admin** / **eBao1234**

### 7_27_2018
- Sql语句：
```
select * from t_module;
select * from t_module_url;

--policy
SELECT T.* FROM T_CONTRACT_MASTER t;

--Lump sum / Annuity decision date
SELECT T.LS_ANN_DECIS_DATE, T.Lump_sum ,T.*
  FROM T_CONTRACT_PRODUCT T
 WHERE T.LS_ANN_DECIS_DATE IS NOT NULL
 ORDER BY T.ITEM_ID DESC;

--product
select * from t_product_life ;

--batch related
select * from T_BATCH_JOB t order by t.job_id desc;
SELECT T.*, t.rowid FROM T_BATCH_JOB T WHERE T.JOB_NAME LIKE '%maturity%';
SELECT T.* FROM T_BATCH_JOB T WHERE T.JOB_NAME LIKE '%Com%';
SELECT T.* FROM T_BATCH_JOB T WHERE T.JOB_NAME LIKE '%Ass%';
SELECT T.* FROM T_BATCH_JOB_PARAMETER T WHERE T.JOB_ID IN (812, 18);
desc T_BATCH_JOB_PARAMETER;
select * from t_account_cate;
select * from t_bank_account ba where ba.account_cate is null;

select cm.policy_code,
       cm.validate_date,
       cp.ls_ann_decis_date,
       pl.product_name,
       pkg_ls_rpt_mis.f_get_domicile(cm.policy_holder) domicile_ph,
       tft.term_fix_name
  from t_contract_master  cm,
       t_product_life     pl,
       t_contract_product cp,
       t_term_fix_type    tft
 where cm.liability_state = 1
   and cm.policy_id = cp.policy_id
   and cp.product_id = pl.product_id
   and cm.term_fix_type = tft.term_fix_type
   and cp.ls_ann_decis_date <=
       add_months(pkg_pub_app_context.F_GET_USER_LOCAL_TIME, 6)
```       
### 7/31/2018
- DDM：粘贴在configuration中
```
-------SLCL_MAIN_DEV-----
slcl_main_dev/slcl_main_devpwd@g22u1
--------SL CL DDM-----
slcl_ddm/slcl_ddmpwd@o29g21 
```
- 修复的发布版本:**Main>V1.03.828**
- eclipse脚本存放路径:plsql/dbscript
- DDM存放路径:C:\Program Files (x86)\Data Dictionary Maintenance
- junit打了断点之后不报错
- DDM生成脚本要看一下，可能还没有更新数据库
- DDM 上传comment形式 **[artf527545]Complete - task artf527545: 3548: Cannot find recievable to confirm for policy 4905165874**
### 8/2/2018
- sql:
```
--3527
--party
select * from t_party_display_config t where t.id = 10;
select t.pep, t.pep_comment, t.* from t_customer t where t.pep is not null;
select t.pep, t.pep_comment, t.* from t_company_customer t where t.pep is not null;

--Query
select t.*, t.rowid from t_query_table_extend t where t.table_name = 'T_CUSTOMER_PH_ORGAN';
select * from t_query_column_extend t where t.table_name = 'T_CUSTOMER_PH_ORGAN';
select * from t_string_resource t where t.org_table = 'T_CUSTOMER_PH_ORGAN';

--Risk & compliance
--PKG_LS_LC.P_CHECK_POLICY_PEP

--Report
--Teamforge (AssetLink / Documents / Root Folder / 02-Analysis&Design / Script /)
```
- 修改t_party_display_config这张表下FIELD_NAME的PEP,PARTY_TYPE为1表示只在individual下显示，2表示organization,3表示全显示.
- PL/SQL查询 Find Database Objects Text to find:pep 勾选Package Bodies , Triggers
- 这样的查询结果是找不到页面的，由数据库表直接拼凑出来的
![](https://raw.githubusercontent.com/Bihanghang/MarkDown/master/MarkDownPictures/SearchResult.PNG)
### 8/3/2018
- 通过structs配置文件去找对应的action
### 8/6/2018
- 修改文件的时候要把对应的log文件也改掉


