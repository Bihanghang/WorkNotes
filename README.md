
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
https://thief.one/2017/03/03/Hexo%E6%90%AD%E5%BB%BA%E5%8D%9A%E5%AE%A2%E6%95%99%E7%A8%8B/
