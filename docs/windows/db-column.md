---
title: db_column — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 20c651c6e671c7c4895fc7dba85d16fdeb998ad5
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570704"
---
# <a name="dbcolumn"></a>db_column
Wiąże określoną kolumnę do zmiennej w zestawie wierszy.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ db_column(   
   ordinal,   
   dbtype,   
   precision,   
   scale,   
   status,   
   length   
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *Liczba porządkowa*  
 Numeru porządkowego kolumny (`DBCOLUMNINFO` porządkowe) lub nazwą kolumny (ciąg ANSI lub Unicode) odpowiadający pole w zestawie wierszy, do którego należy powiązać dane. Jeśli używasz liczb, możesz pominąć kolejne liczby porządkowe (na przykład: 1, 2, 3, 5). Nazwa może zawierać spacji, jeśli dostawca OLE DB, którego używasz obsługuje tę funkcję. Na przykład można użyć jednej z następujących formatów:  
  
```  
[db_column("2")] TCHAR szCity[30];  
[db_column(L"city_name")] TCHAR szCity[30];  
```  
  
 *Atrybut DbType* (opcjonalnie)  
 OLE DB [wskaźnika typu](https://msdn.microsoft.com/library/ms711251.aspx) wpisu kolumny.  
  
 *dokładność* (opcjonalnie)  
 Dokładności, który ma być używany dla wpisu kolumny. Aby uzyskać szczegółowe informacje, zobacz opis `bPrecision` elementu [DBBINDING struktury](https://msdn.microsoft.com/library/ms716845.aspx)  
  
 *Skala* (opcjonalnie)  
 Skala, który ma być używany dla wpisu kolumny. Aby uzyskać szczegółowe informacje, zobacz opis `bScale` elementu [DBBINDING struktury](https://msdn.microsoft.com/library/ms716845.aspx)  
  
 *Stan* (opcjonalnie)  
 Zmienną członkowską, używane do przechowywania stanu dla tej kolumny. Stan wskazuje, czy wartość kolumny jest wartość danych lub innej wartości, takie jak wartości NULL. Możliwe wartości, zobacz [stan](https://msdn.microsoft.com/library/ms722617.aspx) w *OLE DB Podręcznik programisty*.  
  
 *długość* (opcjonalnie)  
 Zmienną członkowską, używane do przechowywania rozmiar kolumny w bajtach.  
  
## <a name="remarks"></a>Uwagi  
 **db_column —** wiąże kolumna tabeli określonej w zmiennej w zestawie wierszy. Rozgranicza on dane elementu członkowskiego, które mogą uczestniczyć w OLE DB `IAccessor`— na podstawie powiązania. Ten atrybut ustawia mapy kolumny, zwykle definiowany przy użyciu makr konsumenta OLE DB [BEGIN_COLUMN_MAP](../data/oledb/begin-column-map.md), [END_COLUMN_MAP](../data/oledb/end-column-map.md), i [COLUMN_ENTRY](../data/oledb/column-entry.md). Te manipulowania OLE DB [struktury DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) powiązać określonej kolumny. Każdy element członkowski, oznacz za pomocą **db_column —** atrybut zajmie jedną pozycję w mapowaniu kolumn w formie wpisu kolumny. W związku z tym możesz wywołać ten atrybut gdzie możesz umieścić mapy kolumny, oznacza to, w klasie polecenia lub tabeli.  
  
 Użyj **db_column —** w połączeniu z oboma [db_table —](../windows/db-table.md) lub [db_command —](../windows/db-command.md) atrybutów.  
  
 Gdy dostawca atrybucie odbiorcy dotyczy ten atrybut do klasy, kompilator spowoduje zmianę nazwy klasy, która ma \_ *YourClassName*dostępu, których *YourClassName* jest nazwa nadana klasy i kompilator utworzy klasę o nazwie *YourClassName*, która jest pochodną \_ *YourClassName*metody dostępu.  W widoku klas pojawi się, obie klasy.  
  
 Przykłady tego atrybutu, używane w aplikacji, zobacz przykłady [AtlAgent](http://msdn.microsoft.com/52bef5da-c1a0-4223-b4e6-9e464b6db409), i [MultiRead](http://msdn.microsoft.com/5a2a915a-77dc-492f-94b2-1b809995dd5e).  
  
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
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty konsumentów OLE DB](../windows/ole-db-consumer-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   