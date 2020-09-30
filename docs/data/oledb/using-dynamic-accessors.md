---
title: Używanie dynamicznych metod dostępu
ms.date: 10/18/2018
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
ms.openlocfilehash: eea1c6199fed5a4e6e331c1c76f34b96090b709a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509421"
---
# <a name="using-dynamic-accessors"></a>Używanie dynamicznych metod dostępu

Dynamiczne metody dostępu umożliwiają dostęp do źródła danych, gdy nie ma informacji o schemacie bazy danych (struktura bazowa). Biblioteka szablonów OLE DB zawiera kilka klas, które ułatwią Ci.

Przykład [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) pokazuje, jak używać dynamicznych klas dostępu do uzyskiwania informacji o kolumnach i dynamicznego tworzenia metod dostępu.

## <a name="using-cdynamicaccessor"></a>Korzystanie z CDynamicAccessor

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) umożliwia dostęp do źródła danych, gdy nie ma żadnej znajomości schematu bazy danych (struktury podstawowej bazy danych). `CDynamicAccessor` Metody pobierają informacje o kolumnie, takie jak nazwy kolumn, liczba i typ danych. Te informacje o kolumnie służą do dynamicznego tworzenia akcesora w czasie wykonywania. Informacje o kolumnie są przechowywane w buforze, który jest tworzony i zarządzany przez tę klasę. Pobierz dane z buforu przy użyciu metody [GetValue](./cdynamicaccessor-class.md#getvalue) .

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

## <a name="using-cdynamicstringaccessor"></a>Korzystanie z CDynamicStringAccessor

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md) działa jak [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), z tą różnicą, chyba że w jednym z nich. Podczas `CDynamicAccessor` żądania danych w formacie natywnym zgłoszonym przez dostawcę `CDynamicStringAccessor` żądania pobierają wszystkie dane, do których uzyskiwany jest dostęp z magazynu danych jako dane ciągu. Ten proces jest szczególnie przydatny w przypadku prostych zadań, które nie wymagają obliczenia wartości w magazynie danych, na przykład wyświetlania lub drukowania zawartości magazynu danych.

Użyj `CDynamicStringAccessor` metod, aby uzyskać informacje o kolumnie. Te informacje o kolumnie służą do dynamicznego tworzenia akcesora w czasie wykonywania. Informacje o kolumnie są przechowywane w buforze utworzonym i zarządzanym przez tę klasę. Pobierz dane z buforu przy użyciu [CDynamicStringAccessor:: GetString](./cdynamicstringaccessor-class.md#getstring) lub Zapisz go w buforze przy użyciu [CDynamicStringAccessor:: SetString](./cdynamicstringaccessor-class.md#setstring).

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

## <a name="using-cdynamicparameteraccessor"></a>Korzystanie z CDynamicParameterAccessor

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) jest podobna do [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), z wyjątkiem tego, że `CDynamicParameterAccessor` Pobiera informacje o parametrach, które mają być ustawiane przez wywołanie interfejsu [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) . Dostawca musi obsługiwać `ICommandWithParameters` użycie tej klasy przez konsumenta.

Informacje o parametrach są przechowywane w buforze utworzonym i zarządzanym przez tę klasę. Pobierz dane parametrów z bufora przy użyciu [CDynamicParameterAccessor:: GetParam](./cdynamicparameteraccessor-class.md#getparam) i [CDynamicParameterAccessor:: GetParamType](./cdynamicparameteraccessor-class.md#getparamtype).

Aby zapoznać się z przykładem pokazującym, jak używać tej klasy do wykonywania SQL Server procedury składowanej i uzyskiwania wartości parametrów wyjściowych, zobacz przykładowy kod [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) w repozytorium [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) w witrynie GitHub.

## <a name="see-also"></a>Zobacz też

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)<br/>
[Klasa CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)<br/>
[Klasa CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[Klasa CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[Przykład DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)
