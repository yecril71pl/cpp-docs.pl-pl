---
title: "db_column — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.db_column
dev_langs:
- C++
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5fe2d3c5edb4b90676c3880ae422c1fb507cd164
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dbcolumn"></a>db_column
Wiąże określonej kolumny do zmiennej w zestawie wierszy.  
  
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
 `ordinal`  
 Liczby porządkowej kolumny (**DBCOLUMNINFO** porządkowej) lub nazwę kolumny (ciągu ANSI lub Unicode) odpowiadającego pola w zestawie wierszy, z którym chcesz powiązać dane. Używaj liczb, można pominąć kolejne porządkowe (na przykład: 1, 2, 3, 5). Nazwa może zawierać spacji, jeśli obsługuje dostawcy OLE DB, którego używasz. Na przykład można użyć jednej z następujących formatów:  
  
```  
[db_column("2")] TCHAR szCity[30];  
[db_column(L"city_name")] TCHAR szCity[30];  
```  
  
 *wartość DbType* (opcjonalnie)  
 OLE DB [wskaźnika typu](https://msdn.microsoft.com/en-us/library/ms711251.aspx) wpisu kolumny.  
  
 *dokładność* (opcjonalnie)  
 Precyzja służący do wpisu kolumny. Aby uzyskać więcej informacji, zobacz opis `bPrecision` elementu [DBBINDING — struktura](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *Skala* (opcjonalnie)  
 Skala służący do wpisu kolumny. Aby uzyskać więcej informacji, zobacz opis `bScale` elementu [DBBINDING — struktura](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *Stan* (opcjonalnie)  
 Zmiennej członkowskiej używanym do przechowywania stanu dla tej kolumny. Stan wskazuje, czy wartość kolumny jest wartość danych lub inne wartości, takich jak **NULL**. Możliwe wartości, zobacz [stan](https://msdn.microsoft.com/en-us/library/ms722617.aspx) w *OLE DB Podręcznik programisty*.  
  
 *długość* (opcjonalnie)  
 Zmiennej członkowskiej używanym do przechowywania w bajtach rozmiar kolumny.  
  
## <a name="remarks"></a>Uwagi  
 **db_column —** wiąże określonej kolumny tabeli do zmiennej w zestawie wierszy. Go rozgranicza danych elementów członkowskich, które mogą uczestniczyć w bazie danych OLE DB `IAccessor`— na podstawie powiązania. Ten atrybut ustawia mapowania kolumn zwykle zdefiniowane przy użyciu makra konsumenta OLE DB [BEGIN_COLUMN_MAP](../data/oledb/begin-column-map.md), [END_COLUMN_MAP](../data/oledb/end-column-map.md), i [column_entry —](../data/oledb/column-entry.md). Te manipulowania OLE DB [struktury DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) powiązać określonej kolumny. Każdy element członkowski oznaczyć z **db_column —** atrybutu zajmie jeden wpis w mapie kolumn w formie wpis w kolumnie. W związku z tym wywołać ten atrybut gdzie przełączyć mapowania kolumn, to znaczy w klasie polecenia lub tabeli.  
  
 Użyj **db_column —** w połączeniu z albo [db_table —](../windows/db-table.md) lub [db_command —](../windows/db-command.md) atrybutów.  
  
 Gdy dostawca atrybutu konsumenta stosuje ten atrybut do klasy, kompilator spowoduje zmianę nazwy klasy, która ma \_ *YourClassName*dostępu, gdzie *YourClassName* jest nazwa nadana klasy i kompilator utworzy klasy o nazwie *YourClassName*, co wynika ze \_ *YourClassName*metody dostępu.  W widoku klasy zostanie wyświetlona zarówno klasy.  
  
 Przykłady tego atrybutu używane w aplikacji, można znaleźć przykłady [AtlAgent](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409), i [MultiRead](http://msdn.microsoft.com/en-us/5a2a915a-77dc-492f-94b2-1b809995dd5e).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wiąże kolumny w tabeli, aby **długi** element członkowski danych i umożliwia określenie stanu i długość pola.  
  
```  
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
 W tym przykładzie wiąże cztery kolumny w celu **długi**, ciąg znaków, timestamp, a **DB_NUMERIC** integer, w tej kolejności.  
  
```  
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
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, `struct`, elementu członkowskiego, metoda|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty konsumentów OLE DB](../windows/ole-db-consumer-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
