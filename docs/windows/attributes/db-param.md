---
title: db_param — (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_param
dev_langs:
- C++
helpviewer_keywords:
- db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dda702a9c9df9662dc6ca3c38143853e8a407f43
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789608"
---
# <a name="dbparam"></a>db_param

Zmienna określonego elementu członkowskiego jest skojarzona z parametrów wejściowych lub wyjściowych, a rozgranicza zmiennej.

## <a name="syntax"></a>Składnia

```cpp
[ db_param(ordinal, paramtype="DBPARAMIO_INPUT", dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>Parametry

*Liczba porządkowa*<br/>
Numer kolumny (liczba porządkowa DBCOLUMNINFO) odpowiadający pole w zestawie wierszy, do którego należy powiązać dane.

*paramtype*<br/>
(Opcjonalnie) Typ, który można ustawić dla parametru. Dostawcy obsługują tylko typy operacji We/Wy parametrów, które są obsługiwane przez bazowe źródło danych. Typ składa się z co najmniej jedną wartość DBPARAMIOENUM:

- DBPARAMIO_INPUT parametr wejściowy.

- DBPARAMIO_OUTPUT parametru wyjściowego.

- DBPARAMIO_NOTPARAM akcesor nie ma parametrów. Ustawienie `eParamIO` tej wartości w wierszu Akcesory przypomina o tym użytkownika, parametry są ignorowane.

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

**db_param —** definiuje parametry użycia w poleceniach; w związku z tym możesz go użyć za pomocą `db_command`. Na przykład, można użyć **db_param —** by powiązać parametry zapytania SQL lub procedur składowanych. Parametry w procedurze składowanej są wskazywane przez znaki zapytania (?) i elementy członkowskie danych powinna być powiązana, w kolejności, w jakiej są wyświetlane parametry.

**db_param —** rozgranicza dane elementu członkowskiego, które mogą uczestniczyć w OLE DB `ICommandWithParameters`— na podstawie powiązania. Ustawia typ parametru (dane wejściowe lub wyjściowe), typ OLE DB, dokładności, skala, stan i długość określonego parametru. Ten atrybut wstawia makra konsumenta OLE DB BEGIN_PARAM_MAP... END_PARAM_MAP. Każdy element członkowski, oznacz za pomocą **db_param —** atrybut zajmie jednego wpisu na mapie w formie COLUMN_ENTRY.

**db_param —** jest używany w połączeniu z oboma [db_table —](db-table.md) lub [db_command —](db-command.md) atrybutów.

Gdy dostawca atrybucie odbiorcy dotyczy ten atrybut do klasy, kompilator spowoduje zmianę nazwy klasy, która ma \_ *YourClassName*dostępu, których *YourClassName* jest nazwa nadana klasy i kompilator utworzy klasę o nazwie *YourClassName*, która jest pochodną \_ *YourClassName*metody dostępu.  W widoku klas pojawi się, obie klasy.

## <a name="example"></a>Przykład

Poniższy przykład tworzy klasę polecenia, w zależności od procedury SalesbyYear przechowywane w bazie danych Northwind. Kojarzy pierwszy parametr w procedurze składowanej za pomocą `m_RETURN_VALUE` zmienną i definiuje ją jako parametr wyjściowy. Kojarzy ostatnie dwa parametry (wejścia) za pomocą `m_Beginning_Date` i `m_Ending_Date`.

W poniższym przykładzie `nOutput` zmiennej za pomocą parametru wyjściowego.

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

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **struktury**, elementu członkowskiego, metoda, lokalne|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty konsumentów OLE DB](ole-db-consumer-attributes.md)  
