---
title: "Porady: kierowanie ciągów ANSI dla ADO.NET (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- native strings [C++]
- ADO.NET [C++], marshaling ANSI strings
- strings [C++], ADO.NET
ms.assetid: 6759d5a2-515f-4079-856b-73b1c1e68f2d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 91d97658436e2d5563c70765da5c3c98e1cbeed5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-ansi-strings-for-adonet-ccli"></a>Porady: przeprowadzanie marshalingu ciągów ANSI dla ADO.NET (C++/CLI)
Pokazuje, jak dodać ciąg natywnego (`char *`) do bazy danych i sposobu zorganizowania <xref:System.String?displayProperty=fullName> z bazy danych na ciąg macierzystego.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie klasa DatabaseClass jest tworzony na interakcję z ADO.NET <xref:System.Data.DataTable> obiektu. Należy pamiętać, że ta klasa natywnych języka C++ `class` (w porównaniu z `ref class` lub `value class`). Jest to konieczne, ponieważ chcemy użyć tej klasy z kodu natywnego i zarządzanego typu nie można użyć w kodzie natywnym. Ta klasa zostanie skompilowany, pod kątem CLR, wskazywany przez `#pragma managed` dyrektywy poprzedzających deklaracji klasy. Aby uzyskać więcej informacji w tej dyrektywie, zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md).  
  
 Należy pamiętać, prywatnego elementu członkowskiego klasy DatabaseClass: `gcroot<DataTable ^> table`. Ponieważ natywnych typów nie może zawierać typy zarządzane `gcroot` — słowo kluczowe jest konieczne. Aby uzyskać więcej informacji na temat `gcroot`, zobacz [porady: deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Pozostałej części kodu, w tym przykładzie jest natywny kod C++, wskazywany przez `#pragma unmanaged` dyrektywy poprzedzających `main`. W tym przykładzie wiemy Tworzenie nowego wystąpienia DatabaseClass i wywołanie jego metody do tworzenia tabeli i wypełnienia niektórych wierszy w tabeli. Należy pamiętać, że ciągi natywne C++ jest przekazywany jako wartości w kolumnie StringCol bazy danych. Wewnątrz DatabaseClass, te parametry są przekazywane do ciągów zarządzanych za pomocą kierowania funkcje <xref:System.Runtime.InteropServices?displayProperty=fullName> przestrzeni nazw. W szczególności — metoda <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> jest używany do organizowania `char *` do <xref:System.String>, a także metoda <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> jest używany do organizowania <xref:System.String> do `char *`.  
  
> [!NOTE]
>  Pamięci przydzielonej przez <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> musi alokację wywołując jedną <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> lub `GlobalFree`.  
  
```  
// adonet_marshal_string_native.cpp  
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
  
    void AddRow(char *stringColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["StringCol"] = Marshal::PtrToStringAnsi(  
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
  
    int GetValuesForColumn(char *dataColumn, char **values,  
        int valuesLength)  
    {  
        // Marshal the name of the column to a managed  
        // String.  
        String ^columnStr = Marshal::PtrToStringAnsi(  
                (IntPtr)dataColumn);  
  
        // Get all rows in the table.  
        array<DataRow ^> ^rows = table->Select();  
        int len = rows->Length;  
        len = (len > valuesLength) ? valuesLength : len;  
        for (int i = 0; i < len; i++)  
        {  
            // Marshal each column value from a managed string  
            // to a char *.  
            values[i] = (char *)Marshal::StringToHGlobalAnsi(  
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
    db->AddRow("This is string 1.");  
    db->AddRow("This is string 2.");  
  
    // Now retrieve the rows and display their contents.  
    char *values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        "StringCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        cout << "StringCol: " << values[i] << endl;  
  
        // Deallocate the memory allocated using  
        // Marshal::StringToHGlobalAnsi.  
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
  
-   Aby skompilować kod w wierszu polecenia, Zapisz przykładowy kod w pliku o nazwie adonet_marshal_string_native.cpp, a następnie wprowadź następująca instrukcja:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp  
    ```  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby uzyskać informacje na problemy z zabezpieczeniami dotyczące ADO.NET, zobacz [zabezpieczania aplikacji ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices>   
 [Dostęp do danych za pomocą ADO.NET (C + +/ CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](/dotnet/framework/data/adonet/index)   
 [Współdziałanie](http://msdn.microsoft.com/en-us/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)