---
title: Używanie dynamicznych metod dostępu
ms.date: 10/18/2018
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
ms.openlocfilehash: 4539247894c3980464e744c76cea450324372382
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649725"
---
# <a name="using-dynamic-accessors"></a>Używanie dynamicznych metod dostępu

Dynamicznych metod dostępu zezwala na dostęp do źródła danych, gdy masz nie znajomości schematu bazy danych (wewnętrzna struktura). Biblioteka szablonów OLE DB dostarcza kilka klas, które ułatwią Ci.

[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) przykład pokazuje, jak używać klas dynamicznej metody dostępu, aby uzyskać informacje o kolumnach i dynamiczne tworzenie metod dostępu.

## <a name="using-cdynamicaccessor"></a>Za pomocą cdynamicaccessor —

[Cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md) umożliwia dostęp do źródła danych, gdy masz nie znajomości schematu bazy danych (wewnętrzna struktura bazy danych). `CDynamicAccessor` metody pobrać informacji o kolumnie, takich jak nazwy kolumn, liczba i typ danych. Informacje o kolumnie umożliwia dynamiczne tworzenie metody dostępu w czasie wykonywania. Informacje o kolumnach są przechowywane w buforu, który jest tworzony i zarządzany przez tę klasę. Pobieranie danych z bufora przy użyciu [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md) metody.

## <a name="example"></a>Przykład

```cpp
// Using_Dynamic_Accessors.cpp
// compile with: /c /EHsc
#include <stdio.h>
#include <objbase.h>
#include <atldbcli.h>

int main(int argc, char* argv[] )
{
    HRESULT hr = CoInitialize(NULL );

    CDataSource ds;
    CSession ss;

    CTable<CDynamicAccessor> rs;

    // The following is an example initialization string:
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"
      L"Integrated Security=SSPI;Persist Security Info=False;"
      L"Initial Catalog=Loginname;Data Source=your_data_source;"
      L"Use Procedure for Prepare=1;Auto Translate=True;"
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"
      L"Use Encryption for Data=False;"
      L"Tag with column collation when possible=False");

    hr = ss.Open(ds );
    hr = rs.Open(ss, "Shippers" );

    hr = rs.MoveFirst();
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )
    {
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )
        {
            DBTYPE type;
            rs.GetColumnType(i, &type );
            printf_s( "Column %d [%S] is of type %d\n",
                      i, rs.GetColumnName(i ), type );

            switch(type )
            {
                case DBTYPE_WSTR:
                    printf_s( "value is %S\n",
                              (WCHAR*)rs.GetValue(i ) );
                break;
                case DBTYPE_STR:
                    printf_s( "value is %s\n",
                              (CHAR*)rs.GetValue(i ) );
                default:
                    printf_s( "value is %d\n",
                              *(long*)rs.GetValue(i ) );
            }
        }
        hr = rs.MoveNext();
    }

    rs.Close();
    ss.Close();
    ds.Close();
    CoUninitialize();

    return 0;
}
```

## <a name="using-cdynamicstringaccessor"></a>Za pomocą cdynamicstringaccessor —

[Cdynamicstringaccessor —](../../data/oledb/cdynamicstringaccessor-class.md) działa jak [cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md), z wyjątkiem składowych w jednym ze sposobów ważne. Gdy `CDynamicAccessor` żąda danych w formacie natywnym zgłoszony przez dostawcę `CDynamicStringAccessor` żądań, że dostawca pobrać wszystkie dane używane z magazynu danych jako dane ciągu. Proces jest szczególnie przydatne w przypadku prostych zadań, które nie wymagają obliczenia wartości w magazynie danych, takich jak wyświetlanie lub drukowanie zawartość magazynu danych.

Użyj `CDynamicStringAccessor` metody w celu uzyskania informacji o kolumnie. Informacje o kolumnie umożliwia dynamiczne tworzenie metody dostępu w czasie wykonywania. Informacje o kolumnach są przechowywane w buforze tworzone i zarządzane przez tę klasę. Pobieranie danych z bufora przy użyciu [CDynamicStringAccessor::GetString](../../data/oledb/cdynamicstringaccessor-getstring.md) czy zapisać je przy użyciu buforu [CDynamicStringAccessor::SetString](../../data/oledb/cdynamicstringaccessor-setstring.md).

## <a name="example"></a>Przykład

```cpp
// Using_Dynamic_Accessors_b.cpp
// compile with: /c /EHsc
#include <stdio.h>
#include <objbase.h>
#include <atldbcli.h>

int main(int argc, char* argv[] )
{
    HRESULT hr = CoInitialize(NULL );
    if (hr != S_OK)
    {
        exit (-1);
    }

    CDataSource ds;
    CSession ss;

    CTable<CDynamicStringAccessor> rs;

    // The following is an example initialization string:
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"
      L"Integrated Security=SSPI;Persist Security Info=False;"
      L"Initial Catalog=Loginname;Data Source=your_data_source;"
      L"Use Procedure for Prepare=1;Auto Translate=True;"
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"
      L"Use Encryption for Data=False;"
      L"Tag with column collation when possible=False");

    hr = ss.Open(ds );
    hr = rs.Open(ss, "Shippers" );

    hr = rs.MoveFirst();
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )
    {
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )
        {
            printf_s( "column %d value is %s\n",
                      i, rs.GetString(i ) );
        }
        hr = rs.MoveNext();
    }

    rs.Close();
    ss.Close();
    ds.Close();
    CoUninitialize();

   return 0;
}
```

## <a name="using-cdynamicparameteraccessor"></a>Za pomocą cdynamicparameteraccessor —

[Cdynamicparameteraccessor —](../../data/oledb/cdynamicparameteraccessor-class.md) przypomina [cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md), chyba że `CDynamicParameterAccessor` pobiera informacje o parametrach określonych przez wywołanie [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) interfejsu. Dostawca musi obsługiwać `ICommandWithParameters` dla użytkownika użyć tej klasy.

Informacje o parametrach znajduje się w buforze tworzone i zarządzane przez tę klasę. Pobierz dane parametru z buforu przy użyciu [CDynamicParameterAccessor::GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) i [CDynamicParameterAccessor::GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).

Aby uzyskać przykład pokazująca, jak wykonać procedurę programu SQL Server oraz uzyskać wartości parametrów wyjściowych za pomocą tej klasy, zobacz [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) przykładowy kod przedstawiony w [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) repozytorium w witrynie GitHub.

## <a name="see-also"></a>Zobacz także

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)<br/>
[CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor, klasa](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicParameterAccessor, klasa](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[Przykładowe DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)
