---
title: db_table (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_table
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
ms.openlocfilehash: 9e05a980764b8b97f6c774165fdddd5428a0c989
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215286"
---
# <a name="db_table"></a>db_table

Otwiera tabelę OLE DB.

## <a name="syntax"></a>Składnia

```cpp
[ db_table(db_table, name, source_name, hresult) ]
```

### <a name="parameters"></a>Parametry

*db_table*<br/>
Ciąg określający nazwę tabeli bazy danych (na przykład "produkty").

*Nazwij*<br/>
Obowiązkowe Nazwa dojścia używanego do pracy z tabelą. Należy określić ten parametr, jeśli chcesz zwrócić więcej niż jeden wiersz wyników. **DB_Table** generuje zmienną o określonej *nazwie* , która może służyć do przechodzenia w zestawie wierszy lub wykonywania wielu zapytań akcji.

*source_name*<br/>
Obowiązkowe `CSession`Zmienna lub wystąpienie klasy, `db_source` do której zastosowano polecenie. Zobacz [db_source](db-source.md).

*wynik*<br/>
Obowiązkowe Identyfikuje zmienną, która będzie otrzymywać wartość HRESULT tego polecenia bazy danych. Jeśli zmienna nie istnieje, zostanie automatycznie wprowadzona przez atrybut.

## <a name="remarks"></a>Uwagi

**DB_Table** tworzy obiekt [CTable](../../data/oledb/ctable-class.md) , który jest używany przez konsumenta OLE DB do otwierania tabeli. Tego atrybutu można używać tylko na poziomie klasy; nie można użyć go jako wbudowanego. Użyj, `db_column` Aby powiązać kolumny tabeli z zmiennymi; Użyj `db_param` , aby rozdzielić (ustawić typ parametru itd.) parametrów.

Gdy dostawca atrybutu konsumenta zastosuje ten atrybut do klasy, kompilator zmieni nazwę klasy na \_ *YourClassName*, gdzie *YourClassName* jest nazwą, która została nadana klasie, a kompilator utworzy również klasę o nazwie *YourClassName*, która pochodzi z \_ metody dostępu *YourClassName*.  W Widok klasy są wyświetlane obie klasy.

## <a name="example"></a>Przykład

W poniższym przykładzie zostanie otwarta tabela Products (produkty) do użycia przez program `CProducts` .

```cpp
// db_table.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_table(L"dbo.Products") ]
class CProducts {
   [ db_column("1") ] LONG m_ProductID;
};
```

Aby zapoznać się z przykładem tego atrybutu używanym w aplikacji, zobacz [Odczytaj](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer).

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**`class`**, **`struct`**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[OLE DB atrybuty konsumenta](ole-db-consumer-attributes.md)
