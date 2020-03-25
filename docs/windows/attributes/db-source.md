---
title: db_source (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_source
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
ms.openlocfilehash: 6346a8d6f60313dc17bbcbad062aa888857f0b67
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167280"
---
# <a name="db_source"></a>db_source

Tworzy połączenie ze źródłem danych.

## <a name="syntax"></a>Składnia

```cpp
[ db_source(db_source, name, hresult) ]
```

### <a name="parameters"></a>Parametry

*db_source*<br/>
Parametry połączenia używane do nawiązywania połączenia ze źródłem danych. Aby uzyskać format parametrów połączenia, zobacz [parametry połączeń i linki do danych](/previous-versions/windows/desktop/ms718376(v=vs.85)) w zestawie SDK składników Microsoft Data Access Components (MDAC).

*Nazwij*<br/>
Obowiązkowe W przypadku używania **db_source** w klasie, *name* jest wystąpieniem obiektu źródła danych, do którego zastosowano atrybut **db_source** (Zobacz przykład 1). W przypadku używania **db_source** wbudowanej w implementacji metody *name* jest zmienną (lokalną dla metody), która może być używana do uzyskiwania dostępu do źródła danych (Zobacz przykład 2). Ta *Nazwa* jest przekazywany do *source_name* parametru `db_command` w celu skojarzenia źródła danych z poleceniem.

*wynik*<br/>
Obowiązkowe Identyfikuje zmienną, która będzie otrzymywać wartość HRESULT tego polecenia bazy danych. Jeśli zmienna nie istnieje, zostanie automatycznie wprowadzona przez atrybut.

## <a name="remarks"></a>Uwagi

**db_source** tworzy obiekt [CDataSource](../../data/oledb/cdatasource-class.md) i [CSession](../../data/oledb/csession-class.md) , który razem reprezentuje połączenie ze źródłem danych odbiorcy OLE DB.

Gdy używasz **db_source** w klasie, obiekt `CSession` zostanie członkiem klasy.

Gdy używasz **db_source** w metodzie, wprowadzony kod zostanie wykonany w zakresie metody, a obiekt `CSession` zostanie utworzony jako zmienna lokalna.

**db_source** dodaje właściwości źródła danych do klasy lub w ramach metody. Jest on używany w połączeniu z `db_command` (który przyjmuje parametr *db_source* *name* db_source jako parametr *source_name* ).

Gdy dostawca atrybutu odbiorcy zastosuje ten atrybut do klasy, kompilator zmieni nazwę klasy na \_akcesor *YourClassName*, gdzie *YourClassName* jest nazwą, którą nadano klasy, a kompilator utworzy również klasę o nazwie *YourClassName*, która pochodzi od metody dostępu \_*YourClassName*.  W Widok klasy są wyświetlane obie klasy.

Aby zapoznać się z przykładem tego atrybutu używanym w aplikacji, zobacz [Odczytaj](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer).

## <a name="example"></a>Przykład

Ten przykład wywołuje **db_source** na klasie w celu utworzenia połączenia ze źródłem danych `ds` przy użyciu bazy danych Northwind. `ds` jest dojściem do źródła danych, które może być używane wewnętrznie do klasy `CMyCommand`.

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
|**Dotyczy**|**Klasa**, **Struktura**, element członkowski, metoda, lokalna|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|None|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty konsumentów OLE DB](ole-db-consumer-attributes.md)
