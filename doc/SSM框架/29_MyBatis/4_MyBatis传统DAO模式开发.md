
# 4_MyBatis传统DAO模式开发

普通模式,也称为传统DAO模式,就是在传统DAO模式下,定义接口和实现类,如 interface EmpDao  class EmpDaoImpl
implements EmpDao.  在实现类中,用SQLSession对象调用select insert delete update 等方法实现.目前极为少见
.在传统模式下,我们需要知道SqlSession对象 实现CURD和 参数传递的处理 



------------------------------------------------------------

