原码如下

```cpp
#include <iostream>
#include <fstream>
#include <vector>
#include <cstdlib>
#include <ctime>
#include <string>
#include <windows.h>
#include<algorithm> 
using namespace std;

const int ROWS = 7; // 行数
const int COLUMNS = 8; // 列数
const int TOTAL = ROWS * (COLUMNS - 2) + 2 * 6; // 座位总数
const int RESERVED_LEFT = 6; // 左侧保留座位数
const int RESERVED_RIGHT = 6; // 右侧保留座位数

vector<int> seats(TOTAL); // 座位编号

void init_seats() {
    for (int i = 0; i < TOTAL; i++) {
        seats[i] = i + 1;
    }
}

void shuffle_seats() {
    srand(time(NULL)); // 初始化随机数种子
    random_shuffle(seats.begin() , seats.end() );
}

void output_seats() {
    string filename = "班级座位表.csv";
    ofstream ofs(filename.c_str());
    if (!ofs) {
        cout << "无法打开文件 " << filename << "!" << endl;
        return;
    }
    int index = 0;
    for (int i = 0; i < ROWS; i++) {
        for (int j = 0; j < COLUMNS; j++) { 
            if ((j == 0) && (i==0) || (j == COLUMNS - 1) && (i==0))  { // 左右两侧保留空座位
                ofs << ",";
                continue;
            }
            if (index < TOTAL) 
			{
				switch (seats[index])
				{
					case 1:
						ofs << "蔡泽民";
						break;
					case 2:
						ofs << "岑在尧";
						break;
					case 3:
						ofs << "陈雅兰";
						break;
					case 4:
						ofs << "陈紫略";
						break;
					case 5:
						ofs << "邓钧";
						break;
					case 6:
					 	ofs << "邓宇迪";
						break;
					case 7:
						ofs << "杜杨威";
						break;
					case 8:
						ofs << "范鰆杨";
						break;
					case 9:
						ofs << "古力允";
						break;
					case 10:
						ofs << "何汶羲";
						break;
					case 11:
						ofs << "贺玟颐";
						break;
					case 12:
						ofs << "黄均穗";
						break;
					case 13:
						ofs << "黄瑞沣";
						break;
					case 14:
						ofs << "黄思豪";
						break;
					case 15:
						ofs << "黄文轩";
						break;
					case 16:
						ofs << "黄永宁";
						break;
					case 17:
						ofs << "李建明";
						break;
					case 18:
						ofs << "李瑞楠";
						break;
					case 19:
						ofs << "李思颖";
						break;
					case 20:
						ofs << "梁晓昕";
						break;
					case 21:
						ofs << "刘廷翊";
						break;
					case 22:
						ofs << "刘心岚";
						break;
					case 23:
						ofs << "刘泽涛";
						break;
					case 24:
						ofs << "罗丽颖";
						break;
					case 25:
						ofs << "罗小睿";
						break;
					case 26:
						ofs << "麦慧链";
						break;
					case 27:
						ofs << "丘倡州";
						break;
					case 28:
						ofs << "阮煕雅";
						break;
					case 29:
						ofs << "史浩天";
						break;
					case 30:
						ofs << "宋龄序";
						break;
					case 31:
						ofs << "苏明基";
						break;
					case 32:
						ofs << "田欢";
						break;
					case 33:
						ofs << "万祖源";
						break;
					case 34:
						ofs << "王梓旭";
						break;
					case 35:
						ofs << "温麒霖";
						break;
					case 36:
						ofs << "吴梓锋";
						break;
					case 37:
						ofs << "肖启阳";
						break;
					case 38:
						ofs << "肖哲园";
						break;
					case 39:
						ofs << "徐米嘉";
						break;
					case 40:
						ofs << "许嘉琪";
						break;
					case 41:
						ofs << "薛钦宇";
						break;
					case 42:
						ofs << "喻隆柯";
						break;
					case 43:
						ofs << "袁文灏";
						break;
					case 44:
						ofs << "曾慧璇";
						break;
					case 45:
						ofs << "张弛";
						break;
					case 46:
						ofs << "张杰航";
						break;
					case 47:
						ofs << "张睿";
						break;
					case 48:
						ofs << "张文俊";
						break;
					case 49:
						ofs << "张向荣";
						break;
					case 50:
						ofs << "张芷榕";
						break;
					case 51:
						ofs << "张智燊";
						break;
					case 52:
						ofs << "张子豪";
						break;
					case 53:
						ofs << "郑日朗";
						break;
					case 54:
						ofs << "周家丞";
						break;
					default:	
                		break; 
				}
            	index++;   
            } else {
                ofs << ",";
            }
            ofs << ",";
        }
        ofs << endl;
    }
    ofs.close();
    string cmd = "start excel.exe " + filename;
    ShellExecute(NULL, "open", cmd.c_str(), NULL, NULL, SW_SHOWNORMAL);
}

int main() {
    init_seats();
    shuffle_seats();
    output_seats();
    return 0;
}
```
