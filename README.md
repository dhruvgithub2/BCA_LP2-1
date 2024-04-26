# BCA_LP2
include <iostream>
using namespace std;

#define rows 3
#define cols 3

class demo {
private:
    int A[rows][cols];

public:
    void get_data() {
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                cin >> A[i][j];
            }
        }
    }

    void show_data() {
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                cout << A[i][j] << "\t";
            }
            cout << endl;
        }
    }

    // Operator overloading for matrix multiplication
    demo operator*(const demo& obj) const {
        demo result;
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                result.A[i][j] = 0;
                for (int k = 0; k < cols; k++) {
                    result.A[i][j] += A[i][k] * obj.A[k][j];
                }
            }
        }
        return result;
    }
};

int main() {
    demo d1, d2, d3;
    cout << "Enter data for first matrix:" << endl;
    d1.get_data();
    cout << "Enter data for second matrix:" << endl;
    d2.get_data();
    
    cout << "First matrix:" << endl;
    d1.show_data();
    cout << "Second matrix:" << endl;
    d2.show_data();
    
    d3 = d1 * d2; // Perform matrix multiplication
    cout << "Product of the matrices:" << endl;
    d3.show_data();
    
    return 0;
}
