[JasperReports+Jaspersoft Studio前后端打印模式 学习教程 V1.0.docx](https://www.yuque.com/attachments/yuque/0/2024/docx/43512689/1735482449863-33f77ead-62cb-4473-bcf5-1cf3ada359dd.docx)

下载 Jspersorft Studio 

新建一个Project

File->New->Project->JasperReports Project

![img](images/1735778194822.png)



![img](images/1735778344309.png)

新建一个Jasper Report模板

项目右键->New->Jasper Report

![img](images/1735778463200.png)

选择Blank A4（A4纸大小的模板），然后Next。

![img](images/1735778549485.png)

命名为DemoReport1.jrxml，点击Finish，生成一个报表模板

![img](images/1735778853185.png)



报表模板被垂直的分层，每一个部分都是一个Band，每一个Band的特点不同

![img](images/1735808341439.png)



Title（标题）



Page Header（页头）



Column Header（列头）



Detail 1（详细）



Column Footer（列脚）



Page Footer（页脚）





















































































































































![img](images/1735662044404-c4e2a030-325c-485f-9493-47fdea1615b5.png)



![img](images/1735662083877-6aee417f-7e33-47f4-9b53-73f689f1c84d.png)



![img](images/1735662145247-d16da736-40a4-4f36-a667-e7c5cc244fe6.png)



![img](images/1735662622788-47931f0e-8e34-4383-b131-73a86f971a6c.png)





```plain
@Log(title = "工单批量打印")
    @PostMapping("/purRcvDetail/{template}")
    public AjaxResult mergePwoPdfs(@RequestBody Long[] ids,@PathVariable("template") String template) throws IOException, JRException, NoSuchMethodException {
        AjaxResult ajax = new AjaxResult();
        ajax.put("pdfURL", wmsPurchaseReceiveService.purRcvDetail(ids, template));
        return ajax;
    }
```