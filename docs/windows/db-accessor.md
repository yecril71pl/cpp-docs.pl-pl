---
title: db_accessor — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_accessor
dev_langs:
- C++
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 61c20647d96a66cf4b50e6f0b031cc04353553e5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410653"
---
# <a name="dbaccessor"></a>db_accessor

Grupy `db_column` atrybuty, które uczestniczą w `IAccessor`— na podstawie powiązania.

## <a name="syntax"></a>Składnia

```cpp
[ db_accessor(
   num,
   auto
) ]
```

#### <a name="parameters"></a>Parametry

*num*<br/>
Określa numer metody dostępu (indeks nieujemną liczbę całkowitą). Należy określić metody dostępu w rosnącej kolejności liczb całkowitych lub zdefiniowane wartości.

*auto*<br/>
Wartość logiczna określająca, czy akcesor jest automatycznie pobierany (TRUE) czy nie są pobierane (FALSE).

## <a name="remarks"></a>Uwagi

**db_accessor —** definiuje bazowego akcesora OLE DB dla kolejnych `db_column` i `db_param` atrybutów w obrębie tej samej klasy lub funkcji. **db_accessor —** można używać na poziomie elementu członkowskiego i są używane do grupy `db_column` atrybuty, które uczestniczą w OLE DB `IAccessor`— na podstawie powiązania. Jest używana w połączeniu z oboma `db_table` lub `db_command` atrybutów. Wywołanie tego atrybutu jest podobny do wywoływania [BEGIN_ACCESSOR](../data/oledb/begin-accessor.md) i [END_ACCESSOR](../data/oledb/end-accessor.md) makra.

**db_accessor —** generuje zestawu wierszy i wiąże go do odpowiedniego map metody dostępu. Jeśli nie zostanie wywołana **db_accessor —** akcesor 0 będą automatycznie generowane i wszystkie powiązania kolumny zostaną zmapowane do tego bloku metody dostępu.

**db_accessor —** grupy bazy danych powiązania kolumny w jedną lub więcej metod dostępu. Aby uzyskać omówienie scenariuszy, w których należy użyć wielu metod dostępu, zobacz [przy użyciu wielu metod dostępu w zestawie wierszy](../data/oledb/using-multiple-accessors-on-a-rowset.md). Zobacz też "Użytkownik rekordu pomocy technicznej dla wielu metod dostępu" w [rekordów użytkowników](../data/oledb/user-records.md).

Gdy dostawca atrybucie odbiorcy dotyczy ten atrybut do klasy, kompilator spowoduje zmianę nazwy klasy, która ma \_ *YourClassName*dostępu, których *YourClassName* jest nazwa nadana klasy i kompilator utworzy klasę o nazwie *YourClassName*, która jest pochodną \_ *YourClassName*metody dostępu.  W widoku klas pojawi się, obie klasy.

## <a name="example"></a>Przykład

W poniższym przykładzie użyto **db_accessor —** do grupy kolumn w tabeli zamówienia z bazy danych Northwind, do dwóch metod dostępu. Akcesor 0 jest automatyczne metody dostępu i metody dostępu 1 nie jest.

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
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty konsumentów OLE DB](../windows/ole-db-consumer-attributes.md)  