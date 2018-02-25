---
title: "Używanie dynamicznych metod dostępu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/14/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ce2763749537a77664f2971adac65b17e4bde28b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="using-dynamic-accessors"></a>Używanie dynamicznych metod dostępu

Dynamiczne metody dostępu zezwalają na dostęp do źródła danych, gdy użytkownik nie korzystają z nie schematu bazy danych (struktury). Biblioteka szablonów OLE DB zawiera kilka klas, aby to zrobić.

[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) przykładowych pokazano, jak używać klas dynamicznej metody dostępu, aby uzyskać informacje dotyczące kolumn i dynamicznie utworzyć metody dostępu.

## <a name="using-cdynamicaccessor"></a>Przy użyciu cdynamicaccessor —

[Cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md) umożliwia dostęp do źródła danych, gdy użytkownik nie korzystają z nie schematu bazy danych (wewnętrzna struktura bazy danych). `CDynamicAccessor` metody uzyskiwania informacji o kolumnie, takich jak nazwy kolumn, liczba i typ danych. Informacje te kolumny umożliwia tworzenie akcesor dynamicznie w czasie wykonywania. Informacji o kolumnie znajduje się w buforze, który jest tworzony i zarządzany przez tę klasę. Uzyskiwanie danych z bufora przy użyciu [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md) metody.

## <a name="example"></a>Przykład

### <a name="code"></a>Kod

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

## <a name="using-cdynamicstringaccessor"></a>Using CDynamicStringAccessor

[Cdynamicstringaccessor —](../../data/oledb/cdynamicstringaccessor-class.md) działa, takich jak [cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md), z wyjątkiem w jednym ze sposobów ważne. Gdy `CDynamicAccessor` żąda danych w formacie native zgłoszone przez dostawcę `CDynamicStringAccessor` żądań, że dostawca pobrać wszystkie dane uzyskiwane ze źródła danych jako dane ciągu. Jest to szczególnie przydatne w przypadku prostych zadań, które nie wymagają obliczenia wartości w magazynie danych, takie jak wyświetlanie lub drukowanie zawartość magazynu danych.

Użyj `CDynamicStringAccessor` metod, aby uzyskać informacje dotyczące kolumn. Informacje te kolumny umożliwia tworzenie akcesor dynamicznie w czasie wykonywania. Informacji o kolumnie znajduje się w buforze tworzone i zarządzane przez tę klasę. Uzyskiwanie danych z bufora przy użyciu [CDynamicStringAccessor::GetString](../../data/oledb/cdynamicstringaccessor-getstring.md) lub Przechowaj ją przy użyciu buforu [CDynamicStringAccessor::SetString](../../data/oledb/cdynamicstringaccessor-setstring.md).

## <a name="example"></a>Przykład

### <a name="code"></a>Kod

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

## <a name="using-cdynamicparameteraccessor"></a>Using CDynamicParameterAccessor

[Cdynamicparameteraccessor —](../../data/oledb/cdynamicparameteraccessor-class.md) jest podobny do [cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md), ale `CDynamicParameterAccessor` uzyskuje informacje o parametrach określonych przez wywołanie [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) interfejs. Dostawca musi obsługiwać `ICommandWithParameters` dla konsumentów użyć tej klasy.

Informacje o parametrach znajduje się w buforze tworzone i zarządzane przez tę klasę. Uzyskaj parametr danych z bufora za pomocą [CDynamicParameterAccessor::GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) i [CDynamicParameterAccessor::GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).

Na przykład pokazuje sposób użycia tej klasy wykonywanie procedury składowane programu SQL Server w celu uzyskania wartości parametrów wyjściowych, zobacz [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) przykładowy kod przedstawiony w [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) repozytorium w witrynie GitHub.

## <a name="see-also"></a>Zobacz także

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)  
[CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)  
[CDynamicStringAccessor, klasa](../../data/oledb/cdynamicstringaccessor-class.md)  
[CDynamicParameterAccessor, klasa](../../data/oledb/cdynamicparameteraccessor-class.md)  
[Przykładowe DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)  
