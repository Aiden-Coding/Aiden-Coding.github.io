
# 17_Spring_事务环境搭建

通过张三给李四转账案例演示事务的控制 




1 数据库中准备表格 


![image](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAANYAAABOCAIAAADTtH9XAAAAA3NCSVQICAjb4U/gAAAACXBIWXMAABJ0AAASdAHeZh94AAAI4UlEQVR4nO2dTUgcaRrHn9oMyJ5yicdFMFX2jkkgB2HtasgwZBCrAhthIOakAZkqyUBsN+OCEOcwDgyMM9PVwizTPQiJp0QI6JDpCrJhiWCbgAdBY2jr1UVyWpKDHmVZeg/12d1V3dXV1f2W7fMjh656P+vtv+/zVFl/wxwdHQGC0OMj69P58+f9NNjf37948WLT5uOXiEwjXPb39/93/k+0Z9FSzh2/+wPtOSBnHZQgQhmUIEIZlCBCGZQgQpmGJKjKDMMrxL2QKDzDyGoj/SNngUYkSArboc0DObN8VLuKJ2wyX0yGNhPkjIK5IEKZUHNBVWYs5GcNz80nRtJJFN4aWy0rrTivyqVNeIWUVC3NYZ19eOa+IbN2vyN2//nhL5/EOjtinR0xYf4QwD7svLvmrH0wP2yc74h1dnz9wp76Q6G0nyoNhflDa2jzM3icCZHwdkFVZsSslCvq5GByciO0vmuTFUdgUR9ZgqxoSogoc8bpopaKZ0WngKwmWiq+MckxDPd2prIHUGWGW7qlmZ3AJNcqFcLizb/DQuH9SeH13NXNqYHOjgFtuvD+pPB+ZRgWvrj/3Kj24m7sL1OxxyeF9yd65cLtjuFfiEs/Lg2fCq/1hm+mYWpAmD8EuCaOwebTfx1Y7Z//cxGGv7rX1ZyrDEuCqixm4yktIxjHQkZLxUPq2w/x1GKS1UeeSsUhu6wriE1mjNPAJmck2HirVTZhkzMSAEg5Y/bCkASwXSAAAESZzUq5vN3JYiq+sfSsNRrsm/t+nAUA6L735QgAjP364yAAAAx+NgKwu3cIAPD869sLV2fffHPdbNV97/vZ/q2Zn9Yq+4HBsdl+WPxtDQCAPPxhYfjxyzvdeiX2zs9zV3XlXf/bdN8rddW8yBe/PYGxz6z+w6aR2xEHpLANcCXGhtNbALzHVmVGzFpHkmeT+Mec+ZH7OA76zT55trQBGyKThRKuaAAtuNbenpKNp+/P1mEX1w+7AABwsFcAiHEls+niLgG8OTiAa91u/egc5NRN2Lrd8aT0dOzfAN3spzf7v1vJHY7f6wLy8IeFq7NvroVzSS609+2IKjOO7CAn1W7hhpVdWFib/Wln2Arf5j99N+0a+NzYEQ9y6ma/MNDEH7iQJMjGrlixy0B728pc0BV1OQt2dhDkMabLdUWM7p4YQEErmeGh9gbgUnd33Q0dpaLQ90pdJYerT7f6Pv+0eleNEdYuKAxJsDE5YiXqqixmqzZoFWb2R5SRIPdHwlQqvjHJ2XfIROGj9SufwbHZ/q2ZS/Zd8Iu7AzOvhh//o1borGh4MD9s3akAe+ersa2VnxZWXjXvRkQnpFwQQMgUc8CIHDMJAABSTkttc5Nh9R50Tlpqm9MzuXhKy0mcWHcfbDKvAc9Z6WA8peWjFYa7xl8WuLsxO6vrn359csfHvtU1/nIVPhmwGvbNraqDdvH1vw7fvvkExn5t2o2IDmO9uI9vTVMnYm9Nk4fCpe96Vwo/DtauGxR8axrx5iCnbvZPf9lE/emEFoiRNmPt56mtkZUnzbwR0cFdEClH/23eF7tzq80MwRa4CyLldI2/LIy3bjjcBRHK2HfEHz58oDsV5GxyWh/KHB8f+5zwKaItL6o6x8fHGIgRyqAEEcqgBBHKoAQRyqAEEcq0rQR1gxLtWSC1iboESTqBSmohThMkk0gTr8JwigAg0hIk6QTDcMk87XmcIVRZ3FE00wQp5ZOcLRpVZqxCTYHGiyyOTMr9ER4QQnzWbARN4YFXNN3vUendKBZrTtirYZTx/y20hpwE+regfyHO9bS+oKBFBkdHRxHdBdmJ9eL6hC/PTEnoKN/tSTrh6m+3T9vnSTrBMLLq0aQsoKh65coyR5tAo0QT8vtSHqQh+3Vxtucy5Jd+J0GLHERUgnUgZMp+ah9Z0s2Ko/DILMmKpjZJes44XdQU3j7v0sSyxKcTTqP+g13RkSA4g01xaC/4KNGCpL/NAn/rhrmafC/nKOV6efsgWJFJNAOxRR2B2BE2Ko4qQoLLAJrCezUp66y00LPrekeJUiDWFB4c86yyAMGKTKIbiOtHlcWscwcEALjcU8XfblBm9HNtQvZ2qnTG3rjFQ1Z0ud+rb5TIQNIJhkvmeUWrkQuV7nBBi9pEgqosZkF64Ct7DMff7oCdWC8WNYXPJzk7FQ19lNZgyE/KFUtyca6Xh/yu5qio7eYbKXLQFhLUBZjz9zcO1OUs8Irlb9/bqd2E7bkMsLNXYtQvX0t2Yl2XWj45pwYaJQKosiG/8qVkb9ziS1aA7O0YeWKwIgdtIMG6BKhj/miS9Kiv547CkAT55Gja1ahP0nJJBLYCTb2jUEdd9lxIduKBZK8ASY8m82bQCVZkc+olaKghKzKVD0BcETKawhvVR+GRvxApZPQntcYIy0N6ug4AAOzE0K5ZIO4YCVSgUShD9nZKF7LkGZeQ0RQwVoBLXs45dspgRSb41nQwSDrhsaINQPuiKIBvTQel4qErEhiUoC9IOuF45KLKXDLPK1OowDBAH7Ev2In1BzLDMOaxFHIIPsugBP0iZIrFDO1JtCMYiBHKBLGyX7hwoWnzQc4cdiD2+Zftzh2/i8KDg7Z8ftGWF1UdfCiD0AcliFAGJYhQBiWIUAYliFDGU4Kxzo5WzqMRVNl+n8P5uWZlJApU2wWpqrCqp9qTmu+GnpaXR2kRPSs7LRVW81RXg51YL1Z1f9ascKahbGUv++/wnHWc51vsoDNXo9yK5TSbVZaeUiLkoCsWi5Gysp/SvNDVYY65YBCiYGWnqcJyT7VP3B3miF9aZWX3K8Gy0Nw6SDrBJfPlDmE/DUvMv8IE5n/1ULbsbuZLw58VrMiBLwnS0p9vT7Ub3g5zpDqRs7JT0p+Hp7oOXB3mSHWiZ2Wntf95eqrrpcxhjlQlclZ2avlfNU+1bzwd5ogXEbOy09NfLU+1T1wd5kgVqFvZ//PfP/qZ57njd2hlbxJteVHVwbemEfqgBBHKoAQRyqAEEcqgBBHKoJUdoUzdf18QQcIFAzFCmf8DvISQ5Mgu9coAAAAASUVORK5CYII=)



applicationContext.xml 

jdbc.properties 

见上节课 













2 项目中准备实体类 




1.  package com.msb.pojo;
2.  import lombok.AllArgsConstructor;
3.  import lombok.Data;
4.  import lombok.NoArgsConstructor;
5.  import java.io.Serializable;
6.  /**
7.   * @Author: Ma HaiYang
8.   * @Description: MircoMessage:Mark_7001
9.   */
10. @AllArgsConstructor
11. @NoArgsConstructor
12. @Data
13. public class Account implements Serializable {
14.     private Integer id;
15.     private String name;
16.     private Integer money;
17. }

 

3 准备DAO层,创建一个根据id修改money的方法 




1.  package com.msb.dao;
2.  /**
3.   * @Author: Ma HaiYang
4.   * @Description: MircoMessage:Mark_7001
5.   */
6.  public interface AccountDao {
7.      int transMoney(int id,int money);
8.  }

 







1.  package com.msb.dao.impl;
2.  import com.msb.dao.AccountDao;
3.  import org.springframework.beans.factory.annotation.Autowired;
4.  import org.springframework.jdbc.core.JdbcTemplate;
5.  import org.springframework.stereotype.Repository;
6.  /**
7.   * @Author: Ma HaiYang
8.   * @Description: MircoMessage:Mark_7001
9.   */
10. @Repository
11. public class AccountDaoImpl implements AccountDao {
12.     @Autowired
13.     private JdbcTemplate jdbcTemplate;
14.     @Override
15.     public int transMoney(int id, int money) {
16.         String sql ="update account set money =money +? where id =?";
17.         return jdbcTemplate.update(sql,money,id);
18.     }
19. }

 







4 准备Service,创建一个转账的业务方法 







1.  package com.msb.service;
2.  /**
3.   * @Author: Ma HaiYang
4.   * @Description: MircoMessage:Mark_7001
5.   */
6.  public interface AccountService {
7.      int transMoney(int from ,int to,int money);
8.  }

 







1.  package com.msb.service.impl;
2.  import com.msb.dao.AccountDao;
3.  import com.msb.service.AccountService;
4.  import org.springframework.beans.factory.annotation.Autowired;
5.  import org.springframework.stereotype.Service;
6.  /**
7.   * @Author: Ma HaiYang
8.   * @Description: MircoMessage:Mark_7001
9.   */
10. @Service
11. public class AccountServiceImpl implements AccountService {
12.     @Autowired
13.     private AccountDao accountDao;
14.     @Override
15.     public int transMoney(int from, int to, int money) {
16.         int rows=0;
17.         rows+=accountDao.transMoney(from, 0 - money);       
18.         rows+=accountDao.transMoney(to, money);        
19.         return rows;
20.     }
21. }

 







5 测试代码,测试转账 







1.  package com.msb.test;
2.  import com.msb.service.AccountService;
3.  import org.junit.Test;
4.  import org.springframework.context.ApplicationContext;
5.  import org.springframework.context.support.ClassPathXmlApplicationContext;
6.  /**
7.   * @Author: Ma HaiYang
8.   * @Description: MircoMessage:Mark_7001
9.   */
10. public class TestTx {
11.     @Test()
12.     public void testTransaction(){
13.         ApplicationContext context =new
    ClassPathXmlApplicationContext("applicationContext.xml");
14.         AccountService accountService =
    context.getBean(AccountService.class);
15.         int rows = accountService.transMoney(1, 2, 100);
16.         System.out.println(rows);
17.     }
18.     
19. }

 


































































------------------------------------------------------------
Generated with [Mybase Desktop 8.2.13](http://www.wjjsoft.com/mybase.html?ref=markdown_export)
