---
title: db_table — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_table
dev_langs:
- C++
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ab2dd3b359806aa6b5d54e476ec3581f7bb31d02
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201782"
---
# <a name="dbtable"></a>db_table

Zostanie otwarty tabeli OLE DB.

## <a name="syntax"></a>Składnia

```cpp
[ db_table(
   db_table,
   name,
   source_name,
   hresult
) ]
```

#### <a name="parameters"></a>Parametry

*db_table*  
Ciąg określający nazwę tabeli bazy danych (na przykład "produkty").

*Nazwa* (opcjonalnie)  
Nazwa uchwyt, używanej do pracy z tabeli. Należy określić ten parametr, aby zwrócić więcej niż jeden wiersz wyników. **db_table —** generuje zmienna o określonej *nazwa* który może służyć do przechodzenia zestawu wierszy lub wykonywać wiele zapytań akcji.

*source_name* (opcjonalnie)  
`CSession` Zmiennej lub wystąpienia klasy, która ma `db_source` zastosowany do niego, w którym polecenie zostanie wykonane. Zobacz [db_source —](../windows/db-source.md).

*HRESULT* (opcjonalnie)  
Identyfikuje zmienna, która otrzyma wartość HRESULT dla tego polecenia bazy danych. Jeśli zmienna nie istnieje, jego zostanie automatycznie dodany przez atrybut.

## <a name="remarks"></a>Uwagi

**db_table —** tworzy [CTable](../data/oledb/ctable-class.md) obiektu, który jest używany przez konsumenta OLE DB, aby otworzyć tabeli. Można użyć tego atrybutu tylko na poziomie klasy; Nie można używać go wbudowanego. Użyj `db_column` powiązać kolumny tabeli zmiennych; użyj `db_param` do ograniczania (nastavit typ parametru, a tym samym) parametrów.

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
|**Dotyczy**|**Klasa**, **— struktura**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty konsumentów OLE DB](../windows/ole-db-consumer-attributes.md)  
