---
title: db_accessor (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_accessor
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
ms.openlocfilehash: 1e9725dad39974b828d87bd8b4cdeac623f4e12f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214867"
---
# <a name="db_accessor"></a>db_accessor

Grupuje `db_column` atrybuty, które uczestniczą w powiązaniu opartym na `IAccessor`.

## <a name="syntax"></a>Składnia

```cpp
[ db_accessor(num, auto) ]
```

#### <a name="parameters"></a>Parametry

*numerowan*<br/>
Określa numer metody dostępu (indeks liczby całkowitej liczony od zera). Numery metod dostępu należy określić w kolejności rosnącej, przy użyciu liczb całkowitych lub zdefiniowanych wartości.

*auto*<br/>
Wartość logiczna określająca, czy metoda dostępu jest pobierana automatycznie (TRUE), czy nie jest pobierana (FALSE).

## <a name="remarks"></a>Uwagi

**db_accessor** definiuje podstawowe metody dostępu OLE DB dla kolejnych atrybutów `db_column` i `db_param` w obrębie tej samej klasy lub funkcji. **db_accessor** można używać na poziomie elementu członkowskiego i służy do grupowania atrybutów `db_column`, które uczestniczą w OLE DB `IAccessor`. Jest on używany w połączeniu z atrybutami `db_table` lub `db_command`. Wywołanie tego atrybutu jest podobne do wywoływania [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) makr.

**db_accessor** generuje zestaw wierszy i wiąże go z odpowiednimi mapami dostępu. Jeśli nie wywołasz **db_accessor**, metoda dostępu 0 zostanie wygenerowana automatycznie, a wszystkie powiązania kolumn zostaną zamapowane na ten blok dostępu.

**db_accessor** powiązań kolumn bazy danych w jeden lub więcej metod dostępu. Omówienie scenariuszy, w których należy użyć wielu metod dostępu, można znaleźć [w temacie Używanie wielu metod dostępu w zestawie wierszy](../../data/oledb/using-multiple-accessors-on-a-rowset.md). Zobacz również sekcję "Obsługa rekordu użytkownika dla wielu metod dostępu" w [rekordach użytkowników](../../data/oledb/user-records.md).

Gdy dostawca atrybutu odbiorcy zastosuje ten atrybut do klasy, kompilator zmieni nazwę klasy na \_akcesor *YourClassName*, gdzie *YourClassName* jest nazwą, którą nadano klasy, a kompilator utworzy również klasę o nazwie *YourClassName*, która pochodzi od metody dostępu \_*YourClassName*.  W Widok klasy są wyświetlane obie klasy.

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

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Bloki atrybutów|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|None|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty konsumentów OLE DB](ole-db-consumer-attributes.md)
