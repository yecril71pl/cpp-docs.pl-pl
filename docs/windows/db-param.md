---
title: db_param — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 2c7ce3c5b76dfa8602a46e947d1e8925ec2bf14c
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569446"
---
# <a name="dbparam"></a>db_param
Zmienna określonego elementu członkowskiego jest skojarzona z parametrów wejściowych lub wyjściowych, a rozgranicza zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ db_param(   
   ordinal,   
   paramtype="DBPARAMIO_INPUT",   
   dbtype,   
   precision,   
   scale,   
   status,   
   length  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *Liczba porządkowa*  
 Numer kolumny (liczba porządkowa DBCOLUMNINFO) odpowiadający pole w zestawie wierszy, do którego należy powiązać dane.  
  
 *paramtype* (opcjonalnie)  
 Typ, który można ustawić dla parametru. Dostawcy obsługują tylko typy operacji We/Wy parametrów, które są obsługiwane przez bazowe źródło danych. Typ składa się z co najmniej jedną wartość DBPARAMIOENUM:  
  
-   DBPARAMIO_INPUT parametr wejściowy.  
  
-   DBPARAMIO_OUTPUT parametru wyjściowego.  
  
-   DBPARAMIO_NOTPARAM akcesor nie ma parametrów. Ustawienie `eParamIO` tej wartości w wierszu Akcesory przypomina o tym użytkownika, parametry są ignorowane.  
  
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
 **db_param —** definiuje parametry użycia w poleceniach; w związku z tym możesz go użyć za pomocą `db_command`. Na przykład, można użyć **db_param —** by powiązać parametry zapytania SQL lub procedur składowanych. Parametry w procedurze składowanej są wskazywane przez znaki zapytania (?) i elementy członkowskie danych powinna być powiązana, w kolejności, w jakiej są wyświetlane parametry.  
  
 **db_param —** rozgranicza dane elementu członkowskiego, które mogą uczestniczyć w OLE DB `ICommandWithParameters`— na podstawie powiązania. Ustawia typ parametru (dane wejściowe lub wyjściowe), typ OLE DB, dokładności, skala, stan i długość określonego parametru. Ten atrybut wstawia makra konsumenta OLE DB BEGIN_PARAM_MAP... END_PARAM_MAP. Każdy element członkowski, oznacz za pomocą **db_param —** atrybut zajmie jednego wpisu na mapie w formie COLUMN_ENTRY.  
  
 **db_param —** jest używany w połączeniu z oboma [db_table —](../windows/db-table.md) lub [db_command —](../windows/db-command.md) atrybutów.  
  
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
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty konsumentów OLE DB](../windows/ole-db-consumer-attributes.md)   