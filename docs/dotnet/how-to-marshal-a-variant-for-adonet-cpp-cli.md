---
title: 'Porady: kierowanie obiektu VARIANT dla ADO.NET (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- VARIANT, marshaling
- ADO.NET [C++], marshaling VARIANT types
- VARIANT
ms.assetid: 67a180a7-5691-48ab-8d85-7f75a68dde91
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 166116f54882048f3cd763b2f61e6b4fd56e5357
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-marshal-a-variant-for-adonet-ccli"></a>Porady: przeprowadzanie marshalingu obiektu VARIANT dla ADO.NET (C++/CLI)
Pokazuje, jak dodać natywny `VARIANT` bazę danych i sposobu zorganizowania <xref:System.Object?displayProperty=fullName> z bazy danych do natywny `VARIANT`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie klasa DatabaseClass jest tworzony na interakcję z ADO.NET <xref:System.Data.DataTable> obiektu. Należy pamiętać, że ta klasa natywnych języka C++ `class` (w porównaniu z `ref class` lub `value class`). Jest to konieczne, ponieważ chcemy użyć tej klasy z kodu natywnego i zarządzanego typu nie można użyć w kodzie natywnym. Ta klasa zostanie skompilowany, pod kątem CLR, wskazywany przez `#pragma managed` dyrektywy poprzedzających deklaracji klasy. Aby uzyskać więcej informacji w tej dyrektywie, zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md).  
  
 Należy pamiętać, prywatnego elementu członkowskiego klasy DatabaseClass: `gcroot<DataTable ^> table`. Ponieważ natywnych typów nie może zawierać typy zarządzane `gcroot` — słowo kluczowe jest konieczne. Aby uzyskać więcej informacji na temat `gcroot`, zobacz [porady: deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Pozostałej części kodu, w tym przykładzie jest natywny kod C++, wskazywany przez `#pragma unmanaged` dyrektywy poprzedzających `main`. W tym przykładzie wiemy Tworzenie nowego wystąpienia DatabaseClass i wywołanie jego metody do tworzenia tabeli i wypełnienia niektórych wierszy w tabeli. Należy pamiętać, że native `VARIANT` typów jest przekazywany jako wartości w kolumnie ObjectCol bazy danych. Wewnątrz DatabaseClass te `VARIANT` typy są przekazywane do obiektów zarządzanych za pomocą kierowania funkcje <xref:System.Runtime.InteropServices?displayProperty=fullName> przestrzeni nazw. W szczególności — metoda <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> jest używany do organizowania `VARIANT` do <xref:System.Object>, a także metoda <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> jest używany do organizowania <xref:System.Object> do `VARIANT`.  
  
```  
// adonet_marshal_variant.cpp  
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
  
    void AddRow(VARIANT *objectColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["ObjectCol"] = Marshal::GetObjectForNativeVariant(  
            IntPtr(objectColValue));  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("ObjectCol",  
            Type::GetType("System.Object"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, VARIANT *values,  
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
            // Marshal each column value from a managed object  
            // to a VARIANT.  
            Marshal::GetNativeVariantForObject(  
                rows[i][columnStr], IntPtr(&values[i]));  
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
  
    BSTR bstr1 = SysAllocString(L"This is a BSTR in a VARIANT.");  
    VARIANT v1;  
    v1.vt = VT_BSTR;  
    v1.bstrVal = bstr1;  
    db->AddRow(&v1);  
  
    int i = 42;  
    VARIANT v2;  
    v2.vt = VT_I4;  
    v2.lVal = i;  
    db->AddRow(&v2);  
  
    // Now retrieve the rows and display their contents.  
    VARIANT values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"ObjectCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        switch (values[i].vt)  
        {  
            case VT_BSTR:  
                wcout << L"ObjectCol: " << values[i].bstrVal << endl;  
                break;  
            case VT_I4:  
                cout << "ObjectCol: " << values[i].lVal << endl;  
                break;  
            default:  
                break;  
        }  
  
    }  
  
    SysFreeString(bstr1);  
    delete db;  
  
    return 0;  
}  
```  
  
```Output  
ObjectCol: This is a BSTR in a VARIANT.  
ObjectCol: 42  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby skompilować kod w wierszu polecenia, Zapisz przykładowy kod w pliku o nazwie adonet_marshal_variant.cpp, a następnie wprowadź następująca instrukcja:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp  
    ```  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby uzyskać informacje na problemy z zabezpieczeniami dotyczące ADO.NET, zobacz [zabezpieczania aplikacji ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices>   
 [Dostęp do danych za pomocą ADO.NET (C + +/ CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](/dotnet/framework/data/adonet/index)   
 [Współdziałanie](http://msdn.microsoft.com/en-us/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [Macierzysty i współdziałaniu .NET](../dotnet/native-and-dotnet-interoperability.md)