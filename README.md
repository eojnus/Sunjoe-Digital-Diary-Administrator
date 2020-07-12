# Sunjoe-Digital-Diary-Administrator
A simple program for creating and browsing diaries.
#include<iostream>
#include<fstream>
#include<string>
using namespace std;
int main()
{
	cout << "///////////////////////////////////SunGio Digital Diary Administrator(SDDA) ver1.32///////////////////////////////////"<<endl;
	ifstream ifile,infile;
	ofstream ofile,otfile;
	
	string input = "0";
	
	for (int i = 0;i >= 0;i++)
	{
		cout << "1)Browse diaries" << endl << "2)Create a new diary" << endl << "3)End" << endl;
		cout << "Your choice certainly is :";
		int mode = 0;
			cin.clear();
			cin >> mode;
			if (mode == 2)
			{
				string name;
				cout << "Please enter diary name. Format like：20200711.txt" << endl;
				cin >> name;
				otfile.open("namelist.txt", ios::app);//ios::app 防覆盖。
				otfile << name << endl;
				otfile.close();
				ofile.open(name);
				cout << "please enter words" << ", enter a single \"。\" to end.\n";
				while (input != "。")
				{
					getline(cin, input);
					if (input != "。")//单独的句号就不写入了。
						ofile << input << endl;
					cin.clear();
				}
				ofile.close();

			}
			else if (mode == 1)
			{
				string name;
				cout << "Here are diaries written before:" << endl;
				infile.open("namelist.txt");
				while (infile.good())
				{
					getline(infile, input);
					cout << input << endl;
				}
				infile.close();
				cout << "Please enter diary name. Format like：20200711.txt" << endl;
				cin >> name;
				ifile.open(name);
				while (ifile.good())//一直到 end of file 之前，持续读取文件内容
				{
					getline(ifile, input);
					cout << input << endl;
				}
				ifile.close();
			}
			else if (mode == 4)//A poem
			{
				cout << endl << endl << "姐姐，今夜我在德令哈，夜色笼罩" << endl;
				cout << "姐姐，我今夜只有戈壁" << endl << endl;
				cout << "草原尽头我两手空空" << endl;
				cout << "悲痛时握不住一颗泪滴" << endl;
				cout << "姐姐，今夜我在德令哈" << endl;
				cout << "这是雨水中一座荒凉的城" << endl << endl;
				cout << "除了那些路过的和居住的" << endl;
				cout << "德令哈┄┄今夜" << endl;
				cout << "这是唯一的，最后的，抒情。" << endl;
				cout << "这是唯一的，最后的，草原。" << endl;
				cout << "我把石头还给石头" << endl;
				cout << "让胜利的胜利" << endl;
				cout << "今夜青稞只属于她自己" << endl;
				cout << "一切都在生长" << endl;
				cout << "今夜我只有美丽的戈壁 空空" << endl;
				cout << "姐姐，今夜我不关心人类，我只想你" << endl << endl;
				cout << "                                 by  海子 " << endl;
			}
			else if (mode == 3)
			{
				return 0;
			}
			else
			{
				if (cin >> mode)
				{
					cout << "The mode " << mode << " is not available!" << endl;
				}
				else
				{
					cout << "The mode " << mode << " is not available!" << endl;
				}
			}
			continue;//不断循环显示菜单。
		}
		

	system("pause");
	return 0;
}
