---
title: db_source — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_source
dev_langs:
- C++
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 509395daef16e06c915190a80dc1b9c1c5e6494f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598052"
---
# <a name="dbsource"></a>db_source

Tworzy połączenie ze źródłem danych.

## <a name="syntax"></a>Składnia

```cpp
[ db_source(
   db_source,
   name,
   hresult
) ]
```

### <a name="parameters"></a>Parametry

*db_source*  
Parametry połączenia używane do połączenia ze źródłem danych. Format parametrów połączenia, zobacz [parametrów połączeń i połączeń między danymi](/previous-versions/windows/desktop/ms718376\(v=vs.85\)) w Microsoft Data Access Components (MDAC) zestawu SDK.

*Nazwa* (opcjonalnie)  
Kiedy używasz **db_source —** w klasie, *nazwa* jest wystąpieniem obiektu źródła danych, który ma **db_source —** zastosować atrybut (Zobacz przykład 1). Zastosowania **db_source —** bezpośrednio w implementacji metody *nazwa* jest zmienną (lokalna do metody), który może służyć do uzyskania dostępu do danych źródła (Zobacz przykład 2). Możesz przekazać ten *nazwa* do *source_name* parametru `db_command` do skojarzenia ze źródłem danych za pomocą polecenia.

*HRESULT* (opcjonalnie)  
Identyfikuje zmienna, która otrzyma wartość HRESULT dla tego polecenia bazy danych. Jeśli zmienna nie istnieje, jego zostanie automatycznie dodany przez atrybut.

## <a name="remarks"></a>Uwagi

**db_source —** tworzy [CDataSource](../data/oledb/cdatasource-class.md) i [CSession](../data/oledb/csession-class.md) obiektu, który razem stanowią połączenie ze źródłem danych konsumentów OLE DB.

Kiedy używasz **db_source —** w klasie, `CSession` obiekt staje się składową klasy.

Kiedy używasz **db_source —** w metodzie, wprowadzony kod zostanie wykonany w zakresie metody i `CSession` obiekt zostanie utworzony jako zmienna lokalna.

**db_source —** dodaje właściwości źródła danych do klasy lub metody. Jest używana w połączeniu z `db_command` (który bierze *db_source —* *nazwa* jako parametr jego *source_name* parametru).

Gdy dostawca atrybucie odbiorcy dotyczy ten atrybut do klasy, kompilator spowoduje zmianę nazwy klasy, która ma \_ *YourClassName*dostępu, których *YourClassName* jest nazwa nadana klasy i kompilator utworzy klasę o nazwie *YourClassName*, która jest pochodną \_ *YourClassName*metody dostępu.  W widoku klas pojawi się, obie klasy.

Na przykład ten atrybut używany w aplikacji, zobacz przykłady [AtlAgent](http://msdn.microsoft.com/52bef5da-c1a0-4223-b4e6-9e464b6db409) i [MultiRead](http://msdn.microsoft.com/5a2a915a-77dc-492f-94b2-1b809995dd5e).

## <a name="example"></a>Przykład

Ten przykład wywołuje **db_source —** dla klasy, aby utworzyć połączenie ze źródłem danych `ds` przy użyciu bazy danych Northwind. `ds` jest to dojście dla źródła danych, który może być używany wewnętrznie do `CMyCommand` klasy.

```cpp
// db_source_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[
  db_source(L"my_connection_string", name="ds"),
  db_command(L"select * from Products")  
]
class CMyCommand {};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **struktury**, elementu członkowskiego, metoda, lokalne|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty konsumentów OLE DB](../windows/ole-db-consumer-attributes.md)  
