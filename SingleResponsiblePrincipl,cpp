// Online C++ compiler to run C++ program online
#include <iostream>
#include <fstream>
#include <string>
#include <vector>
#include <boost/lexical_cast.hpp>

using namespace std;
using namespace boost;


class Jrl {
    string title;
    vector<string> data;
    
    friend class persistenceData;
    
    public:
        Jrl(string Title):title(Title) {}
            
        void add_entry(string ent) {
            static int count = 0;
            data.push_back(lexical_cast<string> (count++) + ":" + ent);
        }
        
        void display(void) {
            for (const string &s1: data) {
                cout << s1 << endl;
            }
        }
        
        void save(string fname) {
            ofstream fd(fname);
            fd << title << endl;
            for (const string &line: data) {
                fd << line << endl;
            }
            fd.close();
        }
};

class persistenceData {
    public:
    void backUp(string fname, Jrl data) {
        ofstream fd(fname);
        for (string &line: data.data) {
            fd << line << endl;
        }
        
        fd.close();
    }
};

int main() {
    
    Jrl myjrl{"Great comeback"};
    myjrl.add_entry("Tip: Don't over think");
    myjrl.add_entry("Tip: Do immedicately for 5mins");
    myjrl.save("output.txt");
    myjrl.display();
    
    persistenceData p1;
    p1.backUp("out2.txt", myjrl);
    
    ifstream fd2("out2.txt");
    char  data[1024];
    fd2 >> data;
    
    cout << data << endl;
    return 0;
}
