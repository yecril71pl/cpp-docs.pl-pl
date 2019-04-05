---
title: db_table — (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_table
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
ms.openlocfilehash: 3ab548261d6ebcb9d3d7f7e352c8afe3b33db06f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023870"
---
# <a name="dbtable"></a>db_table

Zostanie otwarty tabeli OLE DB.

## <a name="syntax"></a>Składnia

```cpp
[ db_table(db_table, name, source_name, hresult) ]
```

#### <a name="parameters"></a>Parametry

*db_table*<br/>
Ciąg określający nazwę tabeli bazy danych (na przykład "produkty").

*nazwa*<br/>
(Opcjonalnie) Nazwa uchwyt, używanej do pracy z tabeli. Należy określić ten parametr, aby zwrócić więcej niż jeden wiersz wyników. **db_table —** generuje zmienna o określonej *nazwa* który może służyć do przechodzenia zestawu wierszy lub wykonywać wiele zapytań akcji.

*source_name*<br/>
(Opcjonalnie) `CSession` Zmiennej lub wystąpienia klasy, która ma `db_source` zastosowany do niego, w którym polecenie zostanie wykonane. Zobacz [db_source —](db-source.md).

*wartość HRESULT*<br/>
(Opcjonalnie) Identyfikuje zmienna, która otrzyma wartość HRESULT dla tego polecenia bazy danych. Jeśli zmienna nie istnieje, jego zostanie automatycznie dodany przez atrybut.

## <a name="remarks"></a>Uwagi

**db_table —** tworzy [CTable](../../data/oledb/ctable-class.md) obiektu, który jest używany przez konsumenta OLE DB, aby otworzyć tabeli. Można użyć tego atrybutu tylko na poziomie klasy; Nie można używać go wbudowanego. Użyj `db_column` powiązać kolumny tabeli zmiennych; użyj `db_param` do ograniczania (nastavit typ parametru, a tym samym) parametrów.

Gdy dostawca atrybucie odbiorcy dotyczy ten atrybut do klasy, kompilator spowoduje zmianę nazwy klasy, która ma \_ *YourClassName*dostępu, których *YourClassName* jest nazwa nadana klasy i kompilator utworzy klasę o nazwie *YourClassName*, która jest pochodną \_ *YourClassName*metody dostępu.  W widoku klas pojawi się, obie klasy.

## <a name="example"></a>Przykład

W poniższym przykładzie otwierany tabeli Produkty do użytku przez `CProducts`.

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

Na przykład ten atrybut używany w aplikacji, zobacz przykłady [AtlAgent](https://github.com/Microsoft/VCSamples) i [MultiRead](https://github.com/Microsoft/VCSamples).

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Informacje zawarte w tym artykule dotyczą**|**Klasa**, **— struktura**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty konsumentów OLE DB](ole-db-consumer-attributes.md)
