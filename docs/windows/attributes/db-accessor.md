---
title: db_accessor (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_accessor
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
ms.openlocfilehash: 2a4c5475007cbc516f1a06c6bf858089ba24311f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503553"
---
# <a name="db_accessor"></a>db_accessor

Grupuje `db_column` atrybuty, które uczestniczą w `IAccessor` powiązaniu.

## <a name="syntax"></a>Składnia

```cpp
[ db_accessor(num, auto) ]
```

#### <a name="parameters"></a>Parametry

*numerowan*<br/>
Określa numer metody dostępu (indeks liczby całkowitej liczony od zera). Numery metod dostępu należy określić w kolejności rosnącej, przy użyciu liczb całkowitych lub zdefiniowanych wartości.

*Automatycznie*<br/>
Wartość logiczna określająca, czy metoda dostępu jest pobierana automatycznie (TRUE), czy nie jest pobierana (FALSE).

## <a name="remarks"></a>Uwagi

**db_accessor** definiuje podstawowe metody dostępu OLE DB dla kolejnych `db_column` i `db_param` atrybutów w tej samej klasie lub funkcji. **db_accessor** można używać na poziomie elementu członkowskiego i służy do grupowania `db_column` atrybutów, które uczestniczą w `IAccessor` powiązaniu opartym na OLE DB. Jest używany w połączeniu z `db_table` `db_command` atrybutami lub. Wywołanie tego atrybutu jest podobne do wywoływania [BEGIN_ACCESSOR](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md#begin_accessor) i [END_ACCESSOR](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md#end_accessor) makr.

**db_accessor** generuje zestaw wierszy i wiąże go z odpowiednimi mapami dostępu. Jeśli nie wywołasz **db_accessor**, metoda dostępu 0 zostanie wygenerowana automatycznie, a wszystkie powiązania kolumn zostaną zamapowane na ten blok dostępu.

**db_accessor** powiązań kolumn bazy danych w jeden lub więcej metod dostępu. Omówienie scenariuszy, w których należy użyć wielu metod dostępu, można znaleźć [w temacie Używanie wielu metod dostępu w zestawie wierszy](../../data/oledb/using-multiple-accessors-on-a-rowset.md). Zobacz również sekcję "Obsługa rekordu użytkownika dla wielu metod dostępu" w [rekordach użytkowników](../../data/oledb/user-records.md).

Gdy dostawca atrybutu konsumenta zastosuje ten atrybut do klasy, kompilator zmieni nazwę klasy na \_ *YourClassName*, gdzie *YourClassName* jest nazwą, która została nadana klasie, a kompilator utworzy również klasę o nazwie *YourClassName*, która pochodzi z \_ metody dostępu *YourClassName*.  W Widok klasy są wyświetlane obie klasy.

## <a name="example"></a>Przykład

Poniższy przykład używa **db_accessor** do grupowania kolumn w tabeli Orders z bazy danych Northwind do dwóch metod dostępu. Metoda dostępu 0 to metoda automatyczna, a metoda dostępu 1 to nie.

```cpp
// cpp_attr_ref_db_accessor.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include <atlbase.h>
#include <atldbcli.h>

[ db_command(L"SELECT LastName, FirstName FROM Orders") ]
class CEmployees {
public:
   [ db_accessor(0, TRUE) ];
   [ db_column("1") ] LONG m_OrderID;
   [ db_column("2") ] TCHAR m_CustomerID[6];
   [ db_column("4") ] DBTIMESTAMP m_OrderDate;

   [ db_accessor(1, FALSE) ];
   [ db_column("8") ] CURRENCY m_Freight;
};
```

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|Bloki atrybutów|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[OLE DB atrybuty konsumenta](ole-db-consumer-attributes.md)
