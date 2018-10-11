---
title: db_column — (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_column
dev_langs:
- C++
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 42545b24bff14daf66f719a78ba414f1ae86c5c0
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789747"
---
# <a name="dbcolumn"></a>db_column

Wiąże określoną kolumnę do zmiennej w zestawie wierszy.

## <a name="syntax"></a>Składnia

```cpp
[ db_column(ordinal, dbtype, precision, scale, status, length) ]
```

#### <a name="parameters"></a>Parametry

*Liczba porządkowa*<br/>
Numeru porządkowego kolumny (`DBCOLUMNINFO` porządkowe) lub nazwą kolumny (ciąg ANSI lub Unicode) odpowiadający pole w zestawie wierszy, do którego należy powiązać dane. Jeśli używasz liczb, możesz pominąć kolejne liczby porządkowe (na przykład: 1, 2, 3, 5). Nazwa może zawierać spacji, jeśli dostawca OLE DB, którego używasz obsługuje tę funkcję. Na przykład można użyć jednej z następujących formatów:

```cpp
[db_column("2")] TCHAR szCity[30];
[db_column(L"city_name")] TCHAR szCity[30];
```

*Atrybut DbType*<br/>
(Opcjonalnie) OLE DB [wskaźnika typu](/previous-versions/windows/desktop/ms711251\(v=vs.85\)) wpisu kolumny.

*Precyzja*<br/>
(Opcjonalnie) Dokładności, który ma być używany dla wpisu kolumny. Aby uzyskać szczegółowe informacje, zobacz opis `bPrecision` elementu [DBBINDING struktury](/previous-versions/windows/desktop/ms716845\(v=vs.85\))

*Skala*<br/>
(Opcjonalnie) Skala, który ma być używany dla wpisu kolumny. Aby uzyskać szczegółowe informacje, zobacz opis `bScale` elementu [DBBINDING struktury](/previous-versions/windows/desktop/ms716845\(v=vs.85\))

*status*<br/>
(Opcjonalnie) Zmienną członkowską, używane do przechowywania stanu dla tej kolumny. Stan wskazuje, czy wartość kolumny jest wartość danych lub innej wartości, takie jak wartości NULL. Możliwe wartości, zobacz [stan](/previous-versions/windows/desktop/ms722617\(v=vs.85\)) w *OLE DB Podręcznik programisty*.

*Długość*<br/>
(Opcjonalnie) Zmienną członkowską, używane do przechowywania rozmiar kolumny w bajtach.

## <a name="remarks"></a>Uwagi

**db_column —** wiąże kolumna tabeli określonej w zmiennej w zestawie wierszy. Rozgranicza on dane elementu członkowskiego, które mogą uczestniczyć w OLE DB `IAccessor`— na podstawie powiązania. Ten atrybut ustawia mapy kolumny, zwykle definiowany przy użyciu makr konsumenta OLE DB [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md), [END_COLUMN_MAP](../../data/oledb/end-column-map.md), i [COLUMN_ENTRY](../../data/oledb/column-entry.md). Te manipulowania OLE DB [struktury DBBINDING](/previous-versions/windows/desktop/ms716845\(v=vs.85\)) powiązać określonej kolumny. Każdy element członkowski, oznacz za pomocą **db_column —** atrybut zajmie jedną pozycję w mapowaniu kolumn w formie wpisu kolumny. W związku z tym możesz wywołać ten atrybut gdzie możesz umieścić mapy kolumny, oznacza to, w klasie polecenia lub tabeli.

Użyj **db_column —** w połączeniu z oboma [db_table —](db-table.md) lub [db_command —](db-command.md) atrybutów.

Gdy dostawca atrybucie odbiorcy dotyczy ten atrybut do klasy, kompilator spowoduje zmianę nazwy klasy, która ma \_ *YourClassName*dostępu, których *YourClassName* jest nazwa nadana klasy i kompilator utworzy klasę o nazwie *YourClassName*, która jest pochodną \_ *YourClassName*metody dostępu.  W widoku klas pojawi się, obie klasy.

Przykłady tego atrybutu, używane w aplikacji, zobacz przykłady [AtlAgent](https://github.com/Microsoft/VCSamples), i [MultiRead](https://github.com/Microsoft/VCSamples).

## <a name="example"></a>Przykład

W tym przykładzie tworzy powiązanie kolumny w tabeli, aby **długie** element członkowski danych i umożliwia określenie pól Stan i długości.

```cpp
// db_column_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   DBSTATUS m_dwProductIDStatus;
   DBLENGTH m_dwProductIDLength;

   [ db_column("1", status="m_dwProductIDStatus", length="m_dwProductIDLength") ] LONG m_ProductID;
};
```

## <a name="example"></a>Przykład

W tym przykładzie wiąże cztery kolumny w celu **długie**, ciąg znaków, sygnaturę czasową i `DB_NUMERIC` liczba całkowita, w tej kolejności.

```cpp
// db_column_2.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   [db_column("1")] LONG m_OrderID;
   [db_column("2")] TCHAR m_CustomerID[6];
   [db_column("4")] DB_NUMERIC m_OrderDate;
   [db_column("7", dbtype="DBTYPE_NUMERIC")] DB_NUMERIC m_ShipVia;
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **struktury**, elementu członkowskiego, metoda|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty konsumentów OLE DB](ole-db-consumer-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)  