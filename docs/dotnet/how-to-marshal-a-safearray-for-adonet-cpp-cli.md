---
title: 'Porady: kierowanie obiektu SAFEARRAY dla ADO.NET (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SAFEARRAY, marshaling
- ADO.NET [C++], marshaling SAFEARRAY types
ms.assetid: 1034b9d7-ecf1-40f7-a9ee-53180e87a58c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ddd6250fac293fef58ccc21894661ddf32e3fa61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137422"
---
# <a name="how-to-marshal-a-safearray-for-adonet-ccli"></a>Porady: przeprowadzanie marshalingu obiektu SAFEARRAY dla ADO.NET (C++/CLI)
Pokazuje, jak dodać natywny `SAFEARRAY` bazę danych i sposobu zorganizowania tablicy z bazy danych do natywny `SAFEARRAY`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie klasa DatabaseClass jest tworzony na interakcję z ADO.NET <xref:System.Data.DataTable> obiektu. Należy pamiętać, że ta klasa natywnych języka C++ `class` (w porównaniu z `ref class` lub `value class`). Jest to konieczne, ponieważ chcemy użyć tej klasy z kodu natywnego i zarządzanego typu nie można użyć w kodzie natywnym. Ta klasa zostanie skompilowany, pod kątem CLR, wskazywany przez `#pragma managed` dyrektywy poprzedzających deklaracji klasy. Aby uzyskać więcej informacji w tej dyrektywie, zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md).  
  
 Należy pamiętać, prywatnego elementu członkowskiego klasy DatabaseClass: `gcroot<DataTable ^> table`. Ponieważ natywnych typów nie może zawierać typy zarządzane `gcroot` — słowo kluczowe jest konieczne. Aby uzyskać więcej informacji na temat `gcroot`, zobacz [porady: deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Pozostałej części kodu, w tym przykładzie jest natywny kod C++, wskazywany przez `#pragma unmanaged` dyrektywy poprzedzających `main`. W tym przykładzie wiemy Tworzenie nowego wystąpienia DatabaseClass i wywołanie jego metody do tworzenia tabeli i wypełnienia niektórych wierszy w tabeli. Należy pamiętać, że native `SAFEARRAY` typów jest przekazywany jako wartości w kolumnie ArrayIntsCol bazy danych. Wewnątrz DatabaseClass te `SAFEARRAY` typy są przekazywane do obiektów zarządzanych za pomocą kierowania funkcje <xref:System.Runtime.InteropServices?displayProperty=fullName> przestrzeni nazw. W szczególności metody <xref:System.Runtime.InteropServices.Marshal.Copy%2A> jest używany do organizowania `SAFEARRAY` do tablicy zarządzanej liczb całkowitych i metody <xref:System.Runtime.InteropServices.Marshal.Copy%2A> jest używany do organizowania zarządzanych tablica liczb całkowitych na `SAFEARRAY`.  
  
```  
// adonet_marshal_safearray.cpp  
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll  
#include <comdef.h>  
#include <gcroot.h>  
#include <iostream>  
using namespace std;  
  
#using <System.Data.dll>  
using namespace System;  
using namespace System::Data;  
using namespace System::Runtime::InteropServices;  
  
#define MAXCOLS 100  
  
#pragma managed  
class DatabaseClass  
{  
public:  
    DatabaseClass() : table(nullptr) { }  
  
    void AddRow(SAFEARRAY *arrayIntsColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        int len = arrayIntsColValue->rgsabound[0].cElements;  
        array<int> ^arr = gcnew array<int>(len);  
  
        int *pData;  
        SafeArrayAccessData(arrayIntsColValue, (void **)&pData);  
        Marshal::Copy(IntPtr(pData), arr, 0, len);  
        SafeArrayUnaccessData(arrayIntsColValue);  
  
        row["ArrayIntsCol"] = arr;  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("ArrayIntsCol",  
            Type::GetType("System.Int32[]"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, SAFEARRAY **values,  
        int valuesLength)  
    {  
        // Marshal the name of the column to a managed  
        // String.  
        String ^columnStr = Marshal::PtrToStringUni(  
                (IntPtr)dataColumn);  
  
        // Get all rows in the table.  
        array<DataRow ^> ^rows = table->Select();  
        int len = rows->Length;  
        len = (len > valuesLength) ? valuesLength : len;  
        for (int i = 0; i < len; i++)  
        {  
            // Marshal each column value from a managed array  
            // of Int32s to a SAFEARRAY of type VT_I4.  
            values[i] = SafeArrayCreateVector(VT_I4, 0, 10);  
            int *pData;  
            SafeArrayAccessData(values[i], (void **)&pData);  
            Marshal::Copy((array<int> ^)rows[i][columnStr], 0,  
                IntPtr(pData), 10);  
            SafeArrayUnaccessData(values[i]);  
        }  
  
        return len;  
    }  
  
private:  
    // Using gcroot, you can use a managed type in  
    // a native class.  
    gcroot<DataTable ^> table;  
};  
  
#pragma unmanaged  
int main()  
{  
    // Create a table and add a few rows to it.  
    DatabaseClass *db = new DatabaseClass();  
    db->CreateAndPopulateTable();  
  
    // Create a standard array.  
    int originalArray[] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
  
    // Create a SAFEARRAY.  
    SAFEARRAY *psa;  
    psa = SafeArrayCreateVector(VT_I4, 0, 10);  
  
    // Copy the data from the original array to the SAFEARRAY.  
    int *pData;  
    HRESULT hr = SafeArrayAccessData(psa, (void **)&pData);  
    memcpy(pData, &originalArray, 40);  
    SafeArrayUnaccessData(psa);  
    db->AddRow(psa);  
  
    // Now retrieve the rows and display their contents.  
    SAFEARRAY *values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"ArrayIntsCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        int *pData;  
        SafeArrayAccessData(values[i], (void **)&pData);  
        for (int j = 0; j < 10; j++)  
        {  
            cout << pData[j] << " ";  
        }  
        cout << endl;  
        SafeArrayUnaccessData(values[i]);  
  
        // Deallocate the memory allocated using  
        // SafeArrayCreateVector.  
        SafeArrayDestroy(values[i]);  
    }  
  
    SafeArrayDestroy(psa);  
    delete db;  
  
    return 0;  
}  
```  
  
```Output  
0 1 2 3 4 5 6 7 8 9   
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby skompilować kod w wierszu polecenia, Zapisz przykładowy kod w pliku o nazwie adonet_marshal_safearray.cpp, a następnie wprowadź następująca instrukcja:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp  
    ```  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby uzyskać informacje na problemy z zabezpieczeniami dotyczące ADO.NET, zobacz [zabezpieczania aplikacji ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices>   
 [Dostęp do danych za pomocą ADO.NET (C + +/ CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](/dotnet/framework/data/adonet/index)   
 [Współdziałanie](http://msdn.microsoft.com/en-us/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)