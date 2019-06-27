**隐式转换：** 使用explicit关键字避免隐式转换
```
class MyData
{
public:
	MyData() : A(0), X(0), id()
	{}
	/*explicit*/ MyData(int) : A(97), X(CV_PI), id("mydata1234")
	{
		cout << __FUNCTION__ << __LINE__ << endl;
	}
	MyData(string str) : id(str)
	{
		cout << __FUNCTION__ << __LINE__ << endl;
	}

	void write(FileStorage& fs) const
	{
		fs << "{" << "A" << A << "X" << X << "id" << id << "}";
	}
	void read(const FileNode& node)
	{
		A = (int)node["A"];
		X = (double)node["X"];
		id = (string)node["id"];
	}
public:
	int A;
	double X;
	string id;
};
int main(int ac, char** av)
{
	MyData m = 'a';
}
```
**读写自定义数据结构：** 在类的内部和外部添加读取和写入函数

**读写OpenCV数据结构：** 

**读写map/vectors/arrays：** 
