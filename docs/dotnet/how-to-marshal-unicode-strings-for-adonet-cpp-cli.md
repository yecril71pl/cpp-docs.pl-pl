---
title: 'Porady: kierowanie ciągów Unicode dla ADO.NET (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO.NET [C++], marshaling Unicode strings
- Unicode [C++], strings
- strings [C++], Unicode
ms.assetid: 1da090ff-6b53-40be-841f-dc79dfe8ba10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 15cf9e9806c0820ea5a410a93419016c2f678c65
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-marshal-unicode-strings-for-adonet-ccli"></a>Porady: przeprowadzanie marshalingu ciągów Unicode dla ADO.NET (C++/CLI)
Pokazuje, jak dodać ciąg Unicode natywnego (`wchar_t *`) do bazy danych i sposobu zorganizowania <xref:System.String?displayProperty=fullName> z bazy danych na ciąg Unicode macierzystego.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie klasa DatabaseClass jest tworzony na interakcję z ADO.NET <xref:System.Data.DataTable> obiektu. Należy pamiętać, że ta klasa natywnych języka C++ `class` (w porównaniu z `ref class` lub `value class`). Jest to konieczne, ponieważ chcemy użyć tej klasy z kodu natywnego i zarządzanego typu nie można użyć w kodzie natywnym. Ta klasa zostanie skompilowany, pod kątem CLR, wskazywany przez `#pragma managed` dyrektywy poprzedzających deklaracji klasy. Aby uzyskać więcej informacji w tej dyrektywie, zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md).  
  
 Należy pamiętać, prywatnego elementu członkowskiego klasy DatabaseClass: `gcroot<DataTable ^> table`. Ponieważ natywnych typów nie może zawierać typy zarządzane `gcroot` — słowo kluczowe jest konieczne. Aby uzyskać więcej informacji na temat `gcroot`, zobacz [porady: deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Pozostałej części kodu, w tym przykładzie jest natywny kod C++, wskazywany przez `#pragma unmanaged` dyrektywy poprzedzających `main`. W tym przykładzie wiemy Tworzenie nowego wystąpienia DatabaseClass i wywołanie jego metody do tworzenia tabeli i wypełnienia niektórych wierszy w tabeli. Należy pamiętać, że ciągów Unicode C++ jest przekazywany jako wartości w kolumnie StringCol bazy danych. Wewnątrz DatabaseClass, te parametry są przekazywane do ciągów zarządzanych za pomocą kierowania funkcje <xref:System.Runtime.InteropServices?displayProperty=fullName> przestrzeni nazw. W szczególności — metoda <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> jest używany do organizowania `wchar_t *` do <xref:System.String>, a także metoda <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> jest używany do organizowania <xref:System.String> do `wchar_t *`.  
  
> [!NOTE]
>  Pamięci przydzielonej przez <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> musi alokację wywołując jedną <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> lub `GlobalFree`.  
  
```  
// adonet_marshal_string_wide.cpp  
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
  
    void AddRow(wchar_t *stringColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["StringCol"] = Marshal::PtrToStringUni(  
            (IntPtr)stringColValue);  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("StringCol",  
            Type::GetType("System.String"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, wchar_t **values,  
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
            // Marshal each column value from a managed string  
            // to a wchar_t *.  
            values[i] = (wchar_t *)Marshal::StringToHGlobalUni(  
                (String ^)rows[i][columnStr]).ToPointer();  
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
    db->AddRow(L"This is string 1.");  
    db->AddRow(L"This is string 2.");  
  
    // Now retrieve the rows and display their contents.  
    wchar_t *values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"StringCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        wcout << "StringCol: " << values[i] << endl;  
  
        // Deallocate the memory allocated using  
        // Marshal::StringToHGlobalUni.  
        GlobalFree(values[i]);  
    }  
  
    delete db;  
  
    return 0;  
}  
```  
  
```Output  
StringCol: This is string 1.  
StringCol: This is string 2.  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby skompilować kod w wierszu polecenia, Zapisz przykładowy kod w pliku o nazwie adonet_marshal_string_wide.cpp, a następnie wprowadź następująca instrukcja:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp  
    ```  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby uzyskać informacje na problemy z zabezpieczeniami dotyczące ADO.NET, zobacz [zabezpieczania aplikacji ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices>   
 [Dostęp do danych za pomocą ADO.NET (C + +/ CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](/dotnet/framework/data/adonet/index)   
 [Współdziałanie](http://msdn.microsoft.com/en-us/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)