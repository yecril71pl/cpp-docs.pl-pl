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
ms.openlocfilehash: b258e574b912b1c32e5ffae7ba29cfc5f9903685
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209095"
---
# <a name="data-access-using-adonet-ccli"></a>Dostęp do danych za pomocą ADO.NET (C++/CLI)

ADO.NET jest interfejsem API programu .NET Framework, aby uzyskać dostęp do danych i udostępnia możliwości i łatwość użycia niedopasowane przez poprzednie rozwiązania dostępu do danych. W tej sekcji opisano niektóre problemy obejmujące ADO.NET, które są unikatowe dla użytkowników programu Visual C++, takie jak organizowanie natywnych typów.

ADO.NET jest uruchamiany w ramach środowiska uruchomieniowego języka wspólnego (CLR). W związku z tym każda aplikacja, która wchodzi w interakcję z ADO.NET muszą również wskazywać środowiska CLR. Jednak, nie oznacza, że aplikacje natywne nie mogą używać ADO.NET. Te przykłady pokazują, jak korzystać z bazy danych programu ADO.NET, z kodu natywnego.

## <a name="marshal_ansi"></a> Przeprowadzanie marshalingu ciągów ANSI dla ADO.NET

Pokazuje, jak dodać parametry natywnych (`char *`) do bazy danych oraz sposób organizowania <xref:System.String?displayProperty=fullName> z bazy danych na ciąg natywnych.

### <a name="example"></a>Przykład

W tym przykładzie klasa DatabaseClass służy do interakcji z ADO.NET <xref:System.Data.DataTable> obiektu. Należy pamiętać, że ta klasa jest natywnym kodzie C++ `class` (w porównaniu z `ref class` lub `value class`). Jest to konieczne, ponieważ chcemy użyć tej klasy z kodu natywnego, a nie można używać typów zarządzanych w kodzie natywnym. Ta klasa zostanie skompilowany pod kątem środowiska CLR, wskazane przez `#pragma managed` dyrektywy przed deklaracją klasy. Aby uzyskać więcej informacji na temat tej dyrektywy, zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md).

Należy pamiętać, prywatny element członkowski klasy DatabaseClass: `gcroot<DataTable ^> table`. Ponieważ typy natywne nie może zawierać typy zarządzane `gcroot` — słowo kluczowe jest konieczne. Aby uzyskać więcej informacji na temat `gcroot`, zobacz [jak: Deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).

Pozostała część kodu, w tym przykładzie jest macierzystego kodu C++, wskazane przez `#pragma unmanaged` dyrektywy poprzedzających `main`. W tym przykładzie jesteśmy tworzenia nowego wystąpienia DatabaseClass i wywoływania jego metody, aby utworzyć tabelę i wypełnić kilka wierszy w tabeli. Należy pamiętać, że ciągi natywne C++ są przekazywanej jako wartości kolumny StringCol bazy danych. Wewnątrz DatabaseClass, te ciągi są organizowane ciągi zarządzane przy użyciu funkcji kierowania, znajdujących się w <xref:System.Runtime.InteropServices?displayProperty=fullName> przestrzeni nazw. Ściślej mówiąc, Metoda <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> służy do organizowania `char *` do <xref:System.String>, a także metoda <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> służy do organizowania <xref:System.String> do `char *`.

> [!NOTE]
>  Ilość pamięci przydzielonej przez <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> należy cofnąć przydział, wywołując jedną <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> lub `GlobalFree`.

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

- Aby skompilować kod w wierszu polecenia, Zapisz przykładowy kod w pliku o nazwie adonet_marshal_string_native.cpp i wprowadź następującą instrukcję:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal_bstr"></a> Przeprowadzanie marshalingu ciągów BSTR dla ADO.NET

Pokazuje, jak dodać parametry COM (`BSTR`) do bazy danych oraz sposób organizowania <xref:System.String?displayProperty=fullName> z bazy danych do `BSTR`.

### <a name="example"></a>Przykład

W tym przykładzie klasa DatabaseClass służy do interakcji z ADO.NET <xref:System.Data.DataTable> obiektu. Należy pamiętać, że ta klasa jest natywnym kodzie C++ `class` (w porównaniu z `ref class` lub `value class`). Jest to konieczne, ponieważ chcemy użyć tej klasy z kodu natywnego, a nie można używać typów zarządzanych w kodzie natywnym. Ta klasa zostanie skompilowany pod kątem środowiska CLR, wskazane przez `#pragma managed` dyrektywy przed deklaracją klasy. Aby uzyskać więcej informacji na temat tej dyrektywy, zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md).

Należy pamiętać, prywatny element członkowski klasy DatabaseClass: `gcroot<DataTable ^> table`. Ponieważ typy natywne nie może zawierać typy zarządzane `gcroot` — słowo kluczowe jest konieczne. Aby uzyskać więcej informacji na temat `gcroot`, zobacz [jak: Deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).

Pozostała część kodu, w tym przykładzie jest macierzystego kodu C++, wskazane przez `#pragma unmanaged` dyrektywy poprzedzających `main`. W tym przykładzie jesteśmy tworzenia nowego wystąpienia DatabaseClass i wywoływania jego metody, aby utworzyć tabelę i wypełnić kilka wierszy w tabeli. Należy pamiętać, że ciągów COM jest przekazywany jako wartości dla kolumny bazy danych StringCol. Wewnątrz DatabaseClass, te ciągi są organizowane ciągi zarządzane przy użyciu funkcji kierowania, znajdujących się w <xref:System.Runtime.InteropServices?displayProperty=fullName> przestrzeni nazw. Ściślej mówiąc, Metoda <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> służy do organizowania `BSTR` do <xref:System.String>, a także metoda <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> służy do organizowania <xref:System.String> do `BSTR`.

> [!NOTE]
>  Ilość pamięci przydzielonej przez <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> należy cofnąć przydział, wywołując jedną <xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A> lub `SysFreeString`.

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

- Aby skompilować kod w wierszu polecenia, Zapisz przykładowy kod w pliku o nazwie adonet_marshal_string_native.cpp i wprowadź następującą instrukcję:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal_unicode"></a> Przeprowadzanie marshalingu ciągów Unicode dla ADO.NET

Przedstawiono sposób dodawania natywnych ciąg Unicode (`wchar_t *`) do bazy danych oraz sposób organizowania <xref:System.String?displayProperty=fullName> z bazy danych do natywnego ciąg Unicode.

### <a name="example"></a>Przykład

W tym przykładzie klasa DatabaseClass służy do interakcji z ADO.NET <xref:System.Data.DataTable> obiektu. Należy pamiętać, że ta klasa jest natywnym kodzie C++ `class` (w porównaniu z `ref class` lub `value class`). Jest to konieczne, ponieważ chcemy użyć tej klasy z kodu natywnego, a nie można używać typów zarządzanych w kodzie natywnym. Ta klasa zostanie skompilowany pod kątem środowiska CLR, wskazane przez `#pragma managed` dyrektywy przed deklaracją klasy. Aby uzyskać więcej informacji na temat tej dyrektywy, zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md).

Należy pamiętać, prywatny element członkowski klasy DatabaseClass: `gcroot<DataTable ^> table`. Ponieważ typy natywne nie może zawierać typy zarządzane `gcroot` — słowo kluczowe jest konieczne. Aby uzyskać więcej informacji na temat `gcroot`, zobacz [jak: Deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).

Pozostała część kodu, w tym przykładzie jest macierzystego kodu C++, wskazane przez `#pragma unmanaged` dyrektywy poprzedzających `main`. W tym przykładzie jesteśmy tworzenia nowego wystąpienia DatabaseClass i wywoływania jego metody, aby utworzyć tabelę i wypełnić kilka wierszy w tabeli. Należy pamiętać, że ciągi Unicode C++ są przekazywanej jako wartości kolumny StringCol bazy danych. Wewnątrz DatabaseClass, te ciągi są organizowane ciągi zarządzane przy użyciu funkcji kierowania, znajdujących się w <xref:System.Runtime.InteropServices?displayProperty=fullName> przestrzeni nazw. Ściślej mówiąc, Metoda <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> służy do organizowania `wchar_t *` do <xref:System.String>, a także metoda <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> służy do organizowania <xref:System.String> do `wchar_t *`.

> [!NOTE]
>  Ilość pamięci przydzielonej przez <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> należy cofnąć przydział, wywołując jedną <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> lub `GlobalFree`.

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

- Aby skompilować kod w wierszu polecenia, Zapisz przykładowy kod w pliku o nazwie adonet_marshal_string_wide.cpp i wprowadź następującą instrukcję:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp
    ```

## <a name="marshal_variant"></a> Przeprowadzanie marshalingu obiektu VARIANT dla ADO.NET

Przedstawiono sposób dodawania macierzystej `VARIANT` bazę danych i sposobu organizowania <xref:System.Object?displayProperty=fullName> z bazy danych do macierzystej `VARIANT`.

### <a name="example"></a>Przykład

W tym przykładzie klasa DatabaseClass służy do interakcji z ADO.NET <xref:System.Data.DataTable> obiektu. Należy pamiętać, że ta klasa jest natywnym kodzie C++ `class` (w porównaniu z `ref class` lub `value class`). Jest to konieczne, ponieważ chcemy użyć tej klasy z kodu natywnego, a nie można używać typów zarządzanych w kodzie natywnym. Ta klasa zostanie skompilowany pod kątem środowiska CLR, wskazane przez `#pragma managed` dyrektywy przed deklaracją klasy. Aby uzyskać więcej informacji na temat tej dyrektywy, zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md).

Należy pamiętać, prywatny element członkowski klasy DatabaseClass: `gcroot<DataTable ^> table`. Ponieważ typy natywne nie może zawierać typy zarządzane `gcroot` — słowo kluczowe jest konieczne. Aby uzyskać więcej informacji na temat `gcroot`, zobacz [jak: Deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).

Pozostała część kodu, w tym przykładzie jest macierzystego kodu C++, wskazane przez `#pragma unmanaged` dyrektywy poprzedzających `main`. W tym przykładzie jesteśmy tworzenia nowego wystąpienia DatabaseClass i wywoływania jego metody, aby utworzyć tabelę i wypełnić kilka wierszy w tabeli. Należy pamiętać, że native `VARIANT` typy są przekazywanej jako wartości kolumny ObjectCol bazy danych. Wewnątrz DatabaseClass te `VARIANT` typy są przekazywane do obiektów zarządzanych przy użyciu funkcji kierowania, znajdujących się w <xref:System.Runtime.InteropServices?displayProperty=fullName> przestrzeni nazw. Ściślej mówiąc, Metoda <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> służy do organizowania `VARIANT` do <xref:System.Object>, a także metoda <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> służy do organizowania <xref:System.Object> do `VARIANT`.

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

- Aby skompilować kod w wierszu polecenia, Zapisz przykładowy kod w pliku o nazwie adonet_marshal_variant.cpp i wprowadź następującą instrukcję:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp
    ```

## <a name="marshal_safearray"></a> Przeprowadzanie marshalingu obiektu SAFEARRAY dla ADO.NET

Przedstawiono sposób dodawania macierzystej `SAFEARRAY` bazę danych i sposobu organizowania zarządzanych tablicy z bazy danych do macierzystej `SAFEARRAY`.

### <a name="example"></a>Przykład

W tym przykładzie klasa DatabaseClass służy do interakcji z ADO.NET <xref:System.Data.DataTable> obiektu. Należy pamiętać, że ta klasa jest natywnym kodzie C++ `class` (w porównaniu z `ref class` lub `value class`). Jest to konieczne, ponieważ chcemy użyć tej klasy z kodu natywnego, a nie można używać typów zarządzanych w kodzie natywnym. Ta klasa zostanie skompilowany pod kątem środowiska CLR, wskazane przez `#pragma managed` dyrektywy przed deklaracją klasy. Aby uzyskać więcej informacji na temat tej dyrektywy, zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md).

Należy pamiętać, prywatny element członkowski klasy DatabaseClass: `gcroot<DataTable ^> table`. Ponieważ typy natywne nie może zawierać typy zarządzane `gcroot` — słowo kluczowe jest konieczne. Aby uzyskać więcej informacji na temat `gcroot`, zobacz [jak: Deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).

Pozostała część kodu, w tym przykładzie jest macierzystego kodu C++, wskazane przez `#pragma unmanaged` dyrektywy poprzedzających `main`. W tym przykładzie jesteśmy tworzenia nowego wystąpienia DatabaseClass i wywoływania jego metody, aby utworzyć tabelę i wypełnić kilka wierszy w tabeli. Należy pamiętać, że native `SAFEARRAY` typy są przekazywanej jako wartości kolumny ArrayIntsCol bazy danych. Wewnątrz DatabaseClass te `SAFEARRAY` typy są przekazywane do obiektów zarządzanych przy użyciu funkcji kierowania, znajdujących się w <xref:System.Runtime.InteropServices?displayProperty=fullName> przestrzeni nazw. W szczególności metoda <xref:System.Runtime.InteropServices.Marshal.Copy%2A> służy do organizowania `SAFEARRAY` zarządzanej tablicy liczb całkowitych, a także metoda <xref:System.Runtime.InteropServices.Marshal.Copy%2A> służy do organizowania zarządzanych tablicę liczb całkowitych na `SAFEARRAY`.

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

- Aby skompilować kod w wierszu polecenia, Zapisz przykładowy kod w pliku o nazwie adonet_marshal_safearray.cpp i wprowadź następującą instrukcję:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp
    ```

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework

Aby uzyskać informacji na temat problemów z zabezpieczeniami, obejmujących ADO.NET, zobacz [zabezpieczanie aplikacji ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).

## <a name="related-sections"></a>Sekcje pokrewne

|Sekcja|Opis|
|-------------|-----------------|
|[ADO.NET](/dotnet/framework/data/adonet/index)|Omówienie ADO.NET, zestaw klas, które ujawniają usługi dostępu do danych do programisty .NET.|

## <a name="see-also"></a>Zobacz także

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

[Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)

<xref:System.Runtime.InteropServices>

[Współdziałanie](/dotnet/framework/interop/index)
