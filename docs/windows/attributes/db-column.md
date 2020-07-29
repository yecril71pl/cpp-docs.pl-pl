---
title: db_column (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_column
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
ms.openlocfilehash: b78fb081895b7a3e8f0e266810cd19d1b2792240
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222150"
---
# <a name="db_column"></a>db_column

Tworzy powiązanie określonej kolumny ze zmienną w zestawie wierszy.

## <a name="syntax"></a>Składnia

```cpp
[ db_column(ordinal, dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>Parametry

*liczbą*<br/>
Numer kolumny porządkowej ( `DBCOLUMNINFO` porządkowej) lub nazwa kolumny (ciąg ANSI lub Unicode) odpowiadające polu w zestawie wierszy, do którego mają być powiązane dane. Jeśli używasz liczb, możesz pominąć kolejne liczby porządkowe (na przykład: 1, 2, 3, 5). Nazwa może zawierać spacje, jeśli używany dostawca OLE DB obsługuje tę funkcję. Można na przykład użyć jednego z następujących formatów:

```cpp
[db_column("2")] TCHAR szCity[30];
[db_column(L"city_name")] TCHAR szCity[30];
```

*DbType*<br/>
Obowiązkowe [Wskaźnik typu](/previous-versions/windows/desktop/ms711251(v=vs.85)) OLE DB dla wpisu kolumny.

*dokładne*<br/>
Obowiązkowe Precyzja, która ma być używana dla wpisu kolumny. Aby uzyskać szczegółowe informacje, zobacz Opis `bPrecision` elementu [struktury DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))

*zasięgu*<br/>
Obowiązkowe Skala, która ma być używana dla wpisu kolumny. Aby uzyskać szczegółowe informacje, zobacz Opis `bScale` elementu [struktury DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))

*Stany*<br/>
Obowiązkowe Zmienna członkowska używana do przechowywania stanu tej kolumny. Stan wskazuje, czy wartość kolumny jest wartością danych, czy inną wartością, taką jak NULL. Aby uzyskać możliwe wartości, zobacz [status](/previous-versions/windows/desktop/ms722617(v=vs.85)) w *dokumentacji programisty OLE DB*.

*Długość*<br/>
Obowiązkowe Zmienna członkowska używana do przechowywania rozmiaru kolumny w bajtach.

## <a name="remarks"></a>Uwagi

**Db_column** wiąże określoną kolumnę tabeli ze zmienną w zestawie wierszy. Ogranicza dane elementów członkowskich, które mogą uczestniczyć w `IAccessor` powiązaniu opartym na OLE DB. Ten atrybut służy do ustawiania mapy kolumn zwykle zdefiniowanej przy użyciu OLE DB makr [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md), [END_COLUMN_MAP](../../data/oledb/end-column-map.md)i [COLUMN_ENTRY](../../data/oledb/column-entry.md). Umożliwiają one manipulowanie OLE DB [strukturą DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) , aby powiązać określoną kolumnę. Każdy element członkowski, który jest oznaczony za pomocą atrybutu **Db_column** , będzie zajmował jeden wpis w mapie kolumn w postaci wpisu kolumny. W związku z tym należy wywołać ten atrybut, w którym można umieścić mapę kolumn, czyli w klasie polecenia lub tabeli.

Użyj **Db_column** w połączeniu z atrybutami [DB_Table](db-table.md) lub [db_command](db-command.md) .

Gdy dostawca atrybutu konsumenta zastosuje ten atrybut do klasy, kompilator zmieni nazwę klasy na \_ *YourClassName*, gdzie *YourClassName* jest nazwą, która została nadana klasie, a kompilator utworzy również klasę o nazwie *YourClassName*, która pochodzi z \_ metody dostępu *YourClassName*.  W Widok klasy są wyświetlane obie klasy.

Aby zapoznać się z przykładem tego atrybutu używanym w aplikacji, zobacz [Odczytaj](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer).

## <a name="example"></a>Przykład

Ten przykład tworzy powiązanie kolumny w tabeli z **`long`** elementem członkowskim danych i określa pola stanu i długości.

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

Ten przykład wiąże cztery kolumny z **`long`** , ciągiem znaków, sygnaturą czasową i `DB_NUMERIC` liczbą całkowitą w tej kolejności.

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
|**Dotyczy**|**`class`**, **`struct`** , członek, Metoda|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[OLE DB atrybuty konsumenta](ole-db-consumer-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)
