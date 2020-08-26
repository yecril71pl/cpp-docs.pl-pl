---
title: db_param (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_param
helpviewer_keywords:
- db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
ms.openlocfilehash: 008a7f1ea07e6c23ad6d812ac4fbf3b30ef1da89
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833078"
---
# <a name="db_param"></a>db_param

Kojarzy określoną zmienną członkowską z parametrem wejściowym lub wyjściowym i ogranicza zmienną.

## <a name="syntax"></a>Składnia

```cpp
[ db_param(ordinal, paramtype="DBPARAMIO_INPUT", dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>Parametry

*liczbą*<br/>
Numer kolumny (DBCOLUMNINFO) odpowiadający polu w zestawie wierszy, do którego mają być powiązane dane.

*parametr ParamType*<br/>
Obowiązkowe Typ do ustawienia dla parametru. Dostawcy obsługują tylko typy we/wy parametrów, które są obsługiwane przez bazowe źródło danych. Typ jest kombinacją co najmniej jednej wartości DBPARAMIOENUM:

- DBPARAMIO_INPUT parametr wejściowy.

- DBPARAMIO_OUTPUT parametr wyjściowy.

- DBPARAMIO_NOTPARAM akcesor nie ma parametrów. Ustawienie `eParamIO` tej wartości w funkcjach dostępu do wierszy przypomina użytkownika, że parametry są ignorowane.

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

**db_param** definiuje parametry używane w poleceniach; w związku z tym jest używany z `db_command` . Na przykład można użyć **db_param** , aby powiązać parametry w zapytaniach SQL lub procedurach składowanych. Parametry w procedurze składowanej są oznaczane znakami zapytania (?) i należy powiązać składowe danych w kolejności, w której wyświetlane są parametry.

**db_param** ogranicza dane elementów członkowskich, które mogą uczestniczyć w `ICommandWithParameters` powiązaniu opartym na OLE DB. Ustawia typ parametru (dane wejściowe lub wyjściowe), typ OLE DB, precyzja, skalę, stan i długość dla określonego parametru. Ten atrybut wstawia OLE DB makra BEGIN_PARAM_MAP... END_PARAM_MAP. Każdy element członkowski, który jest oznaczony za pomocą atrybutu **db_param** , będzie zajmował jeden wpis w mapie w postaci COLUMN_ENTRY.

**db_param** jest używany w połączeniu z atrybutami [DB_Table](db-table.md) lub [db_command](db-command.md) .

Gdy dostawca atrybutu konsumenta zastosuje ten atrybut do klasy, kompilator zmieni nazwę klasy na \_ *YourClassName*, gdzie *YourClassName* jest nazwą, która została nadana klasie, a kompilator utworzy również klasę o nazwie *YourClassName*, która pochodzi z \_ metody dostępu *YourClassName*.  W Widok klasy są wyświetlane obie klasy.

## <a name="example"></a>Przykład

Poniższy przykład tworzy klasę poleceń na podstawie procedury składowanej SalesbyYear w bazie danych Northwind. Kojarzy pierwszy parametr w procedurze składowanej ze `m_RETURN_VALUE` zmienną i definiuje go jako parametr wyjściowy. Kojarzy ostatnie dwa (dane wejściowe) parametry z `m_Beginning_Date` i `m_Ending_Date` .

Poniższy przykład kojarzy `nOutput` zmienną z parametrem wyjściowym.

```cpp
// db_param.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_source(L"my_connection_string"),
  db_command(L"{ ? = CALL dbo.\"Sales by Year\"(?,?) }")
]
struct CSalesbyYear {
   DBSTATUS m_dwShippedDateStatus;
   DBSTATUS m_dwOrderIDStatus;
   DBSTATUS m_dwSubtotalStatus;
   DBSTATUS m_dwYearStatus;

   DBLENGTH m_dwShippedDateLength;
   DBLENGTH m_dwOrderIDLength;
   DBLENGTH m_dwSubtotalLength;
   DBLENGTH m_dwYearLength;

   // Bind columns
   [ db_column("1", status="m_dwShippedDateStatus", length="m_dwShippedDateLength") ] DBTIMESTAMP m_ShippedDate;
   [ db_column("2", status="m_dwOrderIDStatus", length="m_dwOrderIDLength") ] LONG m_OrderID;
   [ db_column("3", status="m_dwSubtotalStatus", length="m_dwSubtotalLength") ] CURRENCY m_Subtotal;
   [ db_column("4", status="m_dwYearStatus", length="m_dwYearLength") ] TCHAR m_Year[31];

   // Bind parameters
   [ db_param("1", paramtype="DBPARAMIO_OUTPUT") ] LONG m_RETURN_VALUE;
   [ db_param("2", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Beginning_Date;
   [ db_param("3", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Ending_Date;
};
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
