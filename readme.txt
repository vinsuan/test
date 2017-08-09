1.启动创建的私有链（ cd ~/tmpPrivate）
geth --datadir "./" --nodiscover console 2>>geth.log
2.挖矿
miner.start()

具体可以参考博客：http://blog.csdn.net/vinsuan1993/article/details/75208203
当然，还可以参考网上其他博客
3.部署一段智能合约
代码：
var browser_untitled_sol_demoContract = web3.eth.contract([{"constant":false,"inputs":[{"name":"a","type":"uint256"}],"name":"g","outputs":[{"name":"b","type":"uint256"}],"payable":false,"type":"function"}]);
var browser_untitled_sol_demo = browser_untitled_sol_demoContract.new(
   {
     from: web3.eth.accounts[0], 
     data: '0x6060604052341561000f57600080fd5b5b60ad8061001e6000396000f30060606040526000357c0100000000000000000000000000000000000000000000000000000000900463ffffffff168063e420264a14603d575b600080fd5b3415604757600080fd5b605b60048080359060200190919050506071565b6040518082815260200191505060405180910390f35b600060028283020290505b9190505600a165627a7a7230582020bf9f1423d584cbc239e258910b2df45f46e3ba0cb2fdcbf254ab46704aff1a0029', 
     gas: '4300000'
   }, function (e, contract){
    console.log(e, contract);
    if (typeof contract.address !== 'undefined') {
         console.log('Contract mined! address: ' + contract.address + ' transactionHash: ' + contract.transactionHash);
    }
 })
可直接将这段代码赋值到geth中，回车执行。
browser_untitled_sol_demo.g.call(3)调用智能合约。
具体可以参考博客：http://blog.csdn.net/vinsuan1993/article/details/75257945

注：由于挖矿需要消耗大量计算资源，建议尽可能多分配处理器资源给VM。

