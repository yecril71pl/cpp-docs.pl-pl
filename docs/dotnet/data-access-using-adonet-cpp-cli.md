---
title: Dostęp do danych za pomocą ADO.NET (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- ADO.NET [C++]
- .NET Framework [C++], data access
- databases [C++], accessing in C++
- data access [C++], ADO.NET
- data [C++], ADO.NET
- native strings [C++]
- ADO.NET [C++], marshaling ANSI strings
- strings [C++], ADO.NET
- BSTRs, strings
- ADO.NET [C++], marshaling BSTR strings
- strings [C++], marshaling BSTR strings
- ADO.NET [C++], marshaling Unicode strings
- Unicode [C++], strings
- strings [C++], Unicode
- VARIANT, marshaling
- ADO.NET [C++], marshaling VARIANT types
- VARIANT
- SAFEARRAY, marshaling
- ADO.NET [C++], marshaling SAFEARRAY types
ms.assetid: b0cd987d-1ea7-4f76-ba01-cbd52503d06d
ms.openlocfilehash: 3f3980c98890382e77d9d89db2944bebf7b12319
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211063"
---
# <a name="data-access-using-adonet-ccli"></a>Dostęp do danych za pomocą ADO.NET (C++/CLI)

ADO.NET jest interfejsem API .NET Framework dostępu do danych i zapewnia możliwości i łatwość użycia niedopasowanych przez poprzednie rozwiązania dostępu do danych. W tej sekcji opisano niektóre problemy związane z ADO.NET, które są unikatowe dla Visual C++ użytkowników, takich jak kierowanie typów natywnych.

ADO.NET działa w środowisku uruchomieniowym języka wspólnego (CLR). W związku z tym wszystkie aplikacje, które współdziałają z ADO.NET, również muszą wskazywać na środowisko CLR. Nie oznacza to jednak, że natywne aplikacje nie mogą używać ADO.NET. Te przykłady pokazują, jak korzystać z bazy danych ADO.NET z kodu natywnego.

## <a name="marshal-ansi-strings-for-adonet"></a><a name="marshal_ansi"></a>Kierowanie ciągów ANSI dla ADO.NET

Pokazuje, jak dodać ciąg macierzysty ( `char *` ) do bazy danych i jak zorganizować obiekt <xref:System.String?displayProperty=fullName> z bazy danych do ciągu natywnego.

### <a name="example"></a>Przykład

W tym przykładzie Klasa DatabaseClass jest tworzona w celu współdziałania z <xref:System.Data.DataTable> obiektem ADO.NET. Należy zauważyć, że ta klasa jest natywnym C++ **`class`** (w porównaniu z **`ref class`** lub **`value class`** ). Jest to konieczne, ponieważ chcemy użyć tej klasy z kodu natywnego i nie można używać typów zarządzanych w kodzie natywnym. Ta klasa zostanie skompilowana pod kątem środowiska CLR, jak wskazano w `#pragma managed` dyrektywie poprzedzającej deklarację klasy. Aby uzyskać więcej informacji na temat tej dyrektywy, zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md).

Zanotuj prywatną składową klasy DatabaseClass: `gcroot<DataTable ^> table` . Ponieważ typy natywne nie mogą zawierać typów zarządzanych, `gcroot` słowo kluczowe jest niezbędne. Aby uzyskać więcej informacji na temat `gcroot` , zobacz [How to: DECLARE dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).

Resztą kodu w tym przykładzie jest natywny kod języka C++, zgodnie z `#pragma unmanaged` poprzednią dyrektywą `main` . W tym przykładzie tworzymy nowe wystąpienie elementu DatabaseClass i wywołujemy jego metody w celu utworzenia tabeli i wypełnienia niektórych wierszy w tabeli. Należy zauważyć, że natywne ciągi C++ są przesyłane jako wartości dla kolumny bazy danych StringCol. Wewnątrz DatabaseClass te ciągi są przekazywane do zarządzanych parametrów przy użyciu funkcji organizowania znalezionych w <xref:System.Runtime.InteropServices?displayProperty=fullName> przestrzeni nazw. Metoda <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> jest używana w celu skierowania `char *` do <xref:System.String> , a Metoda <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> jest używana do kierowania a <xref:System.String> do `char *` .

> [!NOTE]
> Przydział pamięci przydzielonej przez <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> musi być cofnięty przez wywołanie albo <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> lub `GlobalFree` .

```cpp
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

### <a name="compiling-the-code"></a>Kompilowanie kodu

- Aby skompilować kod z wiersza polecenia, Zapisz przykładowy kod w pliku o nazwie adonet_marshal_string_native. cpp i wprowadź następującą instrukcję:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-bstr-strings-for-adonet"></a><a name="marshal_bstr"></a>Kierowanie ciągów BSTR dla ADO.NET

Pokazuje, jak dodać ciąg COM ( `BSTR` ) do bazy danych i jak skierować obiekt <xref:System.String?displayProperty=fullName> z bazy danych do programu `BSTR` .

### <a name="example"></a>Przykład

W tym przykładzie Klasa DatabaseClass jest tworzona w celu współdziałania z <xref:System.Data.DataTable> obiektem ADO.NET. Należy zauważyć, że ta klasa jest natywnym C++ **`class`** (w porównaniu z **`ref class`** lub **`value class`** ). Jest to konieczne, ponieważ chcemy użyć tej klasy z kodu natywnego i nie można używać typów zarządzanych w kodzie natywnym. Ta klasa zostanie skompilowana pod kątem środowiska CLR, jak wskazano w `#pragma managed` dyrektywie poprzedzającej deklarację klasy. Aby uzyskać więcej informacji na temat tej dyrektywy, zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md).

Zanotuj prywatną składową klasy DatabaseClass: `gcroot<DataTable ^> table` . Ponieważ typy natywne nie mogą zawierać typów zarządzanych, `gcroot` słowo kluczowe jest niezbędne. Aby uzyskać więcej informacji na temat `gcroot` , zobacz [How to: DECLARE dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).

Resztą kodu w tym przykładzie jest natywny kod języka C++, zgodnie z `#pragma unmanaged` poprzednią dyrektywą `main` . W tym przykładzie tworzymy nowe wystąpienie elementu DatabaseClass i wywołujemy jego metody w celu utworzenia tabeli i wypełnienia niektórych wierszy w tabeli. Zwróć uwagę, że ciągi COM są przesyłane jako wartości dla kolumny bazy danych StringCol. Wewnątrz DatabaseClass te ciągi są przekazywane do zarządzanych parametrów przy użyciu funkcji organizowania znalezionych w <xref:System.Runtime.InteropServices?displayProperty=fullName> przestrzeni nazw. Metoda <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> jest używana w celu skierowania `BSTR` do <xref:System.String> , a Metoda <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> jest używana do kierowania a <xref:System.String> do `BSTR` .

> [!NOTE]
> Przydział pamięci przydzielonej przez <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> musi być cofnięty przez wywołanie albo <xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A> lub `SysFreeString` .

``` cpp
// adonet_marshal_string_bstr.cpp
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

    void AddRow(BSTR stringColValue)
    {
        // Add a row to the table.
        DataRow ^row = table->NewRow();
        row["StringCol"] = Marshal::PtrToStringBSTR(
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

    int GetValuesForColumn(BSTR dataColumn, BSTR *values,
        int valuesLength)
    {
        // Marshal the name of the column to a managed
        // String.
        String ^columnStr = Marshal::PtrToStringBSTR(
                (IntPtr)dataColumn);

        // Get all rows in the table.
        array<DataRow ^> ^rows = table->Select();
        int len = rows->Length;
        len = (len > valuesLength) ? valuesLength : len;
        for (int i = 0; i < len; i++)
        {
            // Marshal each column value from a managed string
            // to a BSTR.
            values[i] = (BSTR)Marshal::StringToBSTR(
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

    BSTR str1 = SysAllocString(L"This is string 1.");
    db->AddRow(str1);

    BSTR str2 = SysAllocString(L"This is string 2.");
    db->AddRow(str2);

    // Now retrieve the rows and display their contents.
    BSTR values[MAXCOLS];
    BSTR str3 = SysAllocString(L"StringCol");
    int len = db->GetValuesForColumn(
        str3, values, MAXCOLS);
    for (int i = 0; i < len; i++)
    {
        wcout << "StringCol: " << values[i] << endl;

        // Deallocate the memory allocated using
        // Marshal::StringToBSTR.
        SysFreeString(values[i]);
    }

    SysFreeString(str1);
    SysFreeString(str2);
    SysFreeString(str3);
    delete db;

    return 0;
}
```

```Output
StringCol: This is string 1.
StringCol: This is string 2.
```

### <a name="compiling-the-code"></a>Kompilowanie kodu

- Aby skompilować kod z wiersza polecenia, Zapisz przykładowy kod w pliku o nazwie adonet_marshal_string_native. cpp i wprowadź następującą instrukcję:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-unicode-strings-for-adonet"></a><a name="marshal_unicode"></a>Kierowanie ciągów Unicode dla ADO.NET

Pokazuje, jak dodać natywny ciąg Unicode ( `wchar_t *` ) do bazy danych i jak zorganizować obiekt <xref:System.String?displayProperty=fullName> z bazy danych na natywny ciąg Unicode.

### <a name="example"></a>Przykład

W tym przykładzie Klasa DatabaseClass jest tworzona w celu współdziałania z <xref:System.Data.DataTable> obiektem ADO.NET. Należy zauważyć, że ta klasa jest natywnym C++ **`class`** (w porównaniu z **`ref class`** lub **`value class`** ). Jest to konieczne, ponieważ chcemy użyć tej klasy z kodu natywnego i nie można używać typów zarządzanych w kodzie natywnym. Ta klasa zostanie skompilowana pod kątem środowiska CLR, jak wskazano w `#pragma managed` dyrektywie poprzedzającej deklarację klasy. Aby uzyskać więcej informacji na temat tej dyrektywy, zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md).

Zanotuj prywatną składową klasy DatabaseClass: `gcroot<DataTable ^> table` . Ponieważ typy natywne nie mogą zawierać typów zarządzanych, `gcroot` słowo kluczowe jest niezbędne. Aby uzyskać więcej informacji na temat `gcroot` , zobacz [How to: DECLARE dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).

Resztą kodu w tym przykładzie jest natywny kod języka C++, zgodnie z `#pragma unmanaged` poprzednią dyrektywą `main` . W tym przykładzie tworzymy nowe wystąpienie elementu DatabaseClass i wywołujemy jego metody w celu utworzenia tabeli i wypełnienia niektórych wierszy w tabeli. Zwróć uwagę, że ciągi Unicode C++ są przesyłane jako wartości dla kolumny bazy danych StringCol. Wewnątrz DatabaseClass te ciągi są przekazywane do zarządzanych parametrów przy użyciu funkcji organizowania znalezionych w <xref:System.Runtime.InteropServices?displayProperty=fullName> przestrzeni nazw. Metoda <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> jest używana w celu skierowania `wchar_t *` do <xref:System.String> , a Metoda <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> jest używana do kierowania a <xref:System.String> do `wchar_t *` .

> [!NOTE]
> Przydział pamięci przydzielonej przez <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> musi być cofnięty przez wywołanie albo <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> lub `GlobalFree` .

```cpp
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

### <a name="compiling-the-code"></a>Kompilowanie kodu

- Aby skompilować kod z wiersza polecenia, Zapisz przykładowy kod w pliku o nazwie adonet_marshal_string_wide. cpp i wprowadź następującą instrukcję:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp
    ```

## <a name="marshal-a-variant-for-adonet"></a><a name="marshal_variant"></a>Kierowanie WARIANTu do ADO.NET

Pokazuje, jak dodać natywny `VARIANT` do bazy danych i jak zorganizować <xref:System.Object?displayProperty=fullName> bazę z bazy danych do natywnej `VARIANT` .

### <a name="example"></a>Przykład

W tym przykładzie Klasa DatabaseClass jest tworzona w celu współdziałania z <xref:System.Data.DataTable> obiektem ADO.NET. Należy zauważyć, że ta klasa jest natywnym C++ **`class`** (w porównaniu z **`ref class`** lub **`value class`** ). Jest to konieczne, ponieważ chcemy użyć tej klasy z kodu natywnego i nie można używać typów zarządzanych w kodzie natywnym. Ta klasa zostanie skompilowana pod kątem środowiska CLR, jak wskazano w `#pragma managed` dyrektywie poprzedzającej deklarację klasy. Aby uzyskać więcej informacji na temat tej dyrektywy, zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md).

Zanotuj prywatną składową klasy DatabaseClass: `gcroot<DataTable ^> table` . Ponieważ typy natywne nie mogą zawierać typów zarządzanych, `gcroot` słowo kluczowe jest niezbędne. Aby uzyskać więcej informacji na temat `gcroot` , zobacz [How to: DECLARE dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).

Resztą kodu w tym przykładzie jest natywny kod języka C++, zgodnie z `#pragma unmanaged` poprzednią dyrektywą `main` . W tym przykładzie tworzymy nowe wystąpienie elementu DatabaseClass i wywołujemy jego metody w celu utworzenia tabeli i wypełnienia niektórych wierszy w tabeli. Należy zauważyć, że typy natywne `VARIANT` są przesyłane jako wartości dla kolumny bazy danych ObjectCol. Wewnątrz DatabaseClass te `VARIANT` typy są przekazywane do zarządzanych obiektów przy użyciu funkcji organizowania dostępnych w <xref:System.Runtime.InteropServices?displayProperty=fullName> przestrzeni nazw. Metoda <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> jest używana w celu skierowania `VARIANT` do <xref:System.Object> , a Metoda <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> jest używana do skierowania <xref:System.Object> do `VARIANT` .

```cpp
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

### <a name="compiling-the-code"></a>Kompilowanie kodu

- Aby skompilować kod z wiersza polecenia, Zapisz przykładowy kod w pliku o nazwie adonet_marshal_variant. cpp i wprowadź następującą instrukcję:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp
    ```

## <a name="marshal-a-safearray-for-adonet"></a><a name="marshal_safearray"></a>Kierowanie elementu SAFEARRAY dla ADO.NET

Pokazuje, jak dodać natywny `SAFEARRAY` do bazy danych i jak skierować zarządzaną tablicę z bazy danych do natywnej `SAFEARRAY` .

### <a name="example"></a>Przykład

W tym przykładzie Klasa DatabaseClass jest tworzona w celu współdziałania z <xref:System.Data.DataTable> obiektem ADO.NET. Należy zauważyć, że ta klasa jest natywnym C++ **`class`** (w porównaniu z **`ref class`** lub **`value class`** ). Jest to konieczne, ponieważ chcemy użyć tej klasy z kodu natywnego i nie można używać typów zarządzanych w kodzie natywnym. Ta klasa zostanie skompilowana pod kątem środowiska CLR, jak wskazano w `#pragma managed` dyrektywie poprzedzającej deklarację klasy. Aby uzyskać więcej informacji na temat tej dyrektywy, zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md).

Zanotuj prywatną składową klasy DatabaseClass: `gcroot<DataTable ^> table` . Ponieważ typy natywne nie mogą zawierać typów zarządzanych, `gcroot` słowo kluczowe jest niezbędne. Aby uzyskać więcej informacji na temat `gcroot` , zobacz [How to: DECLARE dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).

Resztą kodu w tym przykładzie jest natywny kod języka C++, zgodnie z `#pragma unmanaged` poprzednią dyrektywą `main` . W tym przykładzie tworzymy nowe wystąpienie elementu DatabaseClass i wywołujemy jego metody w celu utworzenia tabeli i wypełnienia niektórych wierszy w tabeli. Należy zauważyć, że typy natywne `SAFEARRAY` są przesyłane jako wartości dla kolumny bazy danych ArrayIntsCol. Wewnątrz DatabaseClass te `SAFEARRAY` typy są przekazywane do zarządzanych obiektów przy użyciu funkcji organizowania dostępnych w <xref:System.Runtime.InteropServices?displayProperty=fullName> przestrzeni nazw. W <xref:System.Runtime.InteropServices.Marshal.Copy%2A> odróżnieniu od tej metody jest używana do kierowania `SAFEARRAY` tablicą liczb całkowitych, a Metoda <xref:System.Runtime.InteropServices.Marshal.Copy%2A> jest używana do organizowania zarządzanej tablicy liczb całkowitych na `SAFEARRAY` .

```cpp
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

### <a name="compiling-the-code"></a>Kompilowanie kodu

- Aby skompilować kod z wiersza polecenia, Zapisz przykładowy kod w pliku o nazwie adonet_marshal_safearray. cpp i wprowadź następującą instrukcję:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp
    ```

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework

Aby uzyskać informacje dotyczące problemów z zabezpieczeniami związanych z usługą ADO.NET, zobacz [Zabezpieczanie aplikacji ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).

## <a name="related-sections"></a>Sekcje pokrewne

|Sekcja|Opis|
|-------------|-----------------|
|[ADO.NET](/dotnet/framework/data/adonet/index)|Zawiera omówienie ADO.NET, zestaw klas, które uwidaczniają usługi dostępu do danych w programie .NET programmer's.|

## <a name="see-also"></a>Zobacz także

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

[Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)

<xref:System.Runtime.InteropServices>

[Współdziałanie](/dotnet/framework/interop/index)
