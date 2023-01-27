# Program-Perhitungan-Nilai-Akhir-Mahasiswa
Program ini dibuat untuk menunjang nilai UAS di mata kuliah  Pratikum Algoritma &amp; Struktur Data
#include <iostream>
#include <conio.h>
#define MAX 5

using namespace std;

struct DataMahasiswa
{
    char nama[30];
    char nim[15];
    char matakuliah[20];
    float nilaiakir;
    float nilaitugas;
    float uts;
    float uas;
    string status;
};
DataMahasiswa dm[MAX];

void Data()
{
    for (int i = 0; i < MAX; i++)
    {
        cout << "\nData Mahasiswa" << endl;
        cout << "Nama: ";
        cin.ignore();
        cin.getline(dm[i].nama, 30);
        cout << "NIM: ";
        cin >> dm[i].nim, 15;
        cout << "Mata Kuliah: ";
        cin.ignore();
        cin.getline(dm[i].matakuliah, 20);
        cout << "nilai tugas: ";
        cin >> dm[i].nilaitugas;
        cout << "nilai uts: ";
        cin >> dm[i].uts;
        cout << "nilai uas: ";
        cin >> dm[i].uas;
    }
}

void Hitung()
{   
    for (int i = 0; i < MAX; i++)
    {
        dm[i].nilaiakir = (dm[i].nilaitugas * 0.5) + (dm[i].uts * 0.2) + (dm[i].uas * 0.3);

        if (dm[i].nilaitugas < 40)
        {
            dm[i].status = "Tidak Lulus";
        } else if (dm[i].nilaitugas >=60 ||dm[i].nilaitugas <= 75)
        {
            dm[i].status = "Lulus";
        } else
        {
            dm[i].nilaiakir = dm[i].nilaitugas;
            dm[i].status = "Lulus";
        }
    }
}

void Display()
{
    system("cls");
    cout << "Hasil Nilai Akhir Mahasiswa\n";
    for (int i = 0; i < MAX; i++)
    {
        cout << "Data Mahasiswa ke " << i + 1 << endl;
        cout << "NIM              : " << dm[i].nim;
        cout << "\nNama             : " << dm[i].nama;
        cout << "\nNilai Tugas      : " << dm[i].nilaitugas;
        cout << "\nNilai UTS        : " << dm[i].uts;
        cout << "\nNilai UAS        : " << dm[i].uas;
        cout << "\nNilai Akhir      : " << dm[i].nilaiakir;
        cout << "\nStatus           : " << dm[i].status;
        cout << endl;
        cout << endl;
    }
}

int main()
{
    string user, user_new;
    string password, password_new;

    cout << "Buat akun" << endl;
    cout << "Buat user name: ";
    cin >> user;
    cout << "Buat password: ";
    cin >> password;
    system("cls");

    for (int x = 0; x <= MAX; x++)
    {    
        cout << "Login" << endl;
        login:
        cout << "Masukkan user name: ";
        cin >> user_new;
        cout << "Masukkan password: ";
        cin >> password_new;
        if (user == user_new || password == password_new)
        {
            break;
        } else 
        {
            cout << "User name / Password salah!" << endl;
            cout << "Masukkan ulang!" << endl;
            goto login;
        }

        if (x == 5)
        {
            cout << "Terlalu banyak salah";
        }
    }
    Data();
    Hitung();
    Display();
}
