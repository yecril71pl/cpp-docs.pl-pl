---
title: db_source (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_source
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
ms.openlocfilehash: f17a4ea183a24f7bf4e88137f4536ca082efdf85
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831388"
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
Obowiązkowe W przypadku używania **db_source** w klasie, *name* jest wystąpieniem obiektu źródła danych, do którego zastosowano atrybut **db_source** (Zobacz przykład 1). W przypadku używania **db_source** wbudowanej w implementacji metody *name* jest zmienną (lokalną dla metody), która może być używana do uzyskiwania dostępu do źródła danych (Zobacz przykład 2). Ta *Nazwa* jest przekazywany do *source_name* parametru, `db_command` Aby skojarzyć źródło danych z poleceniem.

*wynik*<br/>
Obowiązkowe Identyfikuje zmienną, która będzie otrzymywać wartość HRESULT tego polecenia bazy danych. Jeśli zmienna nie istnieje, zostanie automatycznie wprowadzona przez atrybut.

## <a name="remarks"></a>Uwagi

**db_source** tworzy obiekt [CDataSource](../../data/oledb/cdatasource-class.md) i [CSession](../../data/oledb/csession-class.md) , który razem reprezentuje połączenie ze źródłem danych odbiorcy OLE DB.

Gdy używasz **db_source** w klasie, `CSession` obiekt zostaje członkiem klasy.

W przypadku używania **db_source** w metodzie wstrzykiwany kod zostanie wykonany w zakresie metody, a `CSession` obiekt jest tworzony jako zmienna lokalna.

**db_source** dodaje właściwości źródła danych do klasy lub w ramach metody. Jest on używany w połączeniu z `db_command` (który przyjmuje parametr *db_source* *name* jako parametr *source_name* ).

Gdy dostawca atrybutu konsumenta zastosuje ten atrybut do klasy, kompilator zmieni nazwę klasy na \_ *YourClassName*, gdzie *YourClassName* jest nazwą, która została nadana klasie, a kompilator utworzy również klasę o nazwie *YourClassName*, która pochodzi z \_ metody dostępu *YourClassName*.  W Widok klasy są wyświetlane obie klasy.

Aby zapoznać się z przykładem tego atrybutu używanym w aplikacji, zobacz [Odczytaj](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer).

## <a name="example"></a>Przykład

Ten przykład wywołuje **db_source** na klasie w celu utworzenia połączenia ze źródłem danych `ds` przy użyciu bazy danych Northwind. `ds` jest dojściem do źródła danych, które może być używane wewnętrznie w `CMyCommand` klasie.

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

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|**`class`**, **`struct`** , członek, metoda, lokalna|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[OLE DB atrybuty konsumenta](ole-db-consumer-attributes.md)
