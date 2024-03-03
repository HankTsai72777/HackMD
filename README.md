[https://hackmd.io/@HankTsai/](https://hackmd.io/@HankTsai/r1jAzGjh6)
# SystemC

1.Download SystemC
--
(1)先檢查`g++`版本: `g++ -v` or `gcc -v` <br/>
沒有就安裝g++: `apt-get install g++` <br/>
(2)下載systemc-2.3.3.tar.gz，並上傳至工作站或linux虛擬機 <br/>
載點: https://www.accellera.org/downloads/standards/systemc<br/>
(3)解壓縮: `tar xvf systemc-2.3.1.tar.gz` <br/>
(4)移動至systemc-2.3.3資料夾: cd systemc-2.3.3 <br/>
(5)建立目錄build，以存放編譯檔案: `mkdir build/` <br/>
(6)移動至build: `cd build/` <br/>
(7)執行config並設定libststemc安裝位置: `../configure –prefix=/usr/local/systemc-2.3.3` <br/>
(8)編譯systemc-2.3.3: `make` <br/>
(9)安裝libsystenc: `make install` or `sudo make install` <br/>

2.環境測試
--
(1)範例程式共6份檔案<br/>
![image](https://hackmd.io/_uploads/BkbqLzo26.png) <br/>
(2)其中Makefile.config、Makefile.rules從`/home/local/systemc-2.3.3/examples/build-unix` 資料夾複製 <br/>
![image](https://hackmd.io/_uploads/B1x0Uzonp.png) <br/>
(3)其餘檔案如下 <br/>
hello_module.cpp: <br/>
```cpp=
#include "hello_module.h"

void hello_module::method_func()
{
	if(clk){
		sc_time_stamp().print();
		printf(" Hello Word! \n");
	}
}
```
hello_module.h: <br/>
```clike=
#include "/home/local/systemc-2.3.3/src/systemc.h"

SC_MODULE(hello_module)
{
	// signal declaration
	sc_in_clk		clk;

	// fuction declaration
	void method_func();

	//Constructor 
	SC_CTOR(hello_module) {
		SC_METHOD(method_func);
		sensitive << clk.pos();
	}
};
```
main.cpp: <br/>
```clike=
#include "/home/local/systemc-2.3.3/src/systemc.h"
#include "hello_module.h"


int sc_main(int argc, char* argv[])
{
	// signal declaration
	sc_clock			clk("clk", 10, SC_NS, 0.5);

	// module declaration
	hello_module		module0("hello_word");

	// signal connection
	module0.clk(clk);

	// run simulation
	sc_start(1000, SC_NS);

	return 0;
}
```
Makefile:
```clike=
LIB_DIR=-L/home/local/systemc-2.3.3/lib-linux64
INC_DIR=-I/home/local/systemc-2.3.3/include
LIB=-lsystemc-2.3.3
RPATH=-Wl,-rpath=/home/local/systemc-2.3.3/lib-linux64

APP=hello_module
BPP=main

all:
	g++ -o $(APP) $(APP).cpp $(BPP).cpp $(LIB_DIR) $(INC_DIR) $(LIB) $(RPATH)

clean:
	rm -rf $(APP)
```
(4)編譯檔案: `make all` ，產生執行檔hello_module <br/>
![image](https://hackmd.io/_uploads/r1SCsMs3T.png)<br/>
![image](https://hackmd.io/_uploads/rkJ_M7sh6.png)<br/>
(5)執行檔案: `./hello_module` <br/>
![image](https://hackmd.io/_uploads/S1v6Mmjna.png)<br/>
