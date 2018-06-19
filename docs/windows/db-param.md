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
ms.openlocfilehash: ce7cf5c8e92e7fd6e6e10d7bef0519b1ced4cf62
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880721"
---
# <a name="dbparam"></a>db_param
Kojarzy zmiennej określonego elementu członkowskiego z parametrem wejściowych lub wyjściowych i rozgranicza zmiennej.  
  
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
 `ordinal`  
 Numer kolumny (**DBCOLUMNINFO** porządkowej) odpowiadającego pola w zestawie wierszy, z którym chcesz powiązać dane.  
  
 *paramtype* (opcjonalnie)  
 Typ dla parametru. Dostawcy obsługują tylko typy operacji We/Wy parametrów, które są obsługiwane w źródle danych. Typ jest kombinacją co najmniej jeden **DBPARAMIOENUM** wartości:  
  
-   **DBPARAMIO_INPUT** parametru wejściowego.  
  
-   **DBPARAMIO_OUTPUT** parametru wyjściowego.  
  
-   **DBPARAMIO_NOTPARAM** metodzie dostępu nie ma parametrów. Ustawienie **eParamIO** tej wartości w wierszu metody dostępu przypomina użytkownika, że parametry są ignorowane.  
  
 *wartość DbType* (opcjonalnie)  
 OLE DB [wskaźnika typu](https://msdn.microsoft.com/en-us/library/ms711251.aspx) wpisu kolumny.  
  
 *dokładność* (opcjonalnie)  
 Precyzja służący do wpisu kolumny. Aby uzyskać więcej informacji, zobacz opis **bPrecision** elementu [DBBINDING — struktura](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *Skala* (opcjonalnie)  
 Skala służący do wpisu kolumny. Aby uzyskać więcej informacji, zobacz opis **bScale** elementu [DBBINDING — struktura](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *Stan* (opcjonalnie)  
 Zmiennej członkowskiej używanym do przechowywania stanu dla tej kolumny. Stan wskazuje, czy wartość kolumny jest wartość danych lub inne wartości, takich jak **NULL**. Możliwe wartości, zobacz [stan](https://msdn.microsoft.com/en-us/library/ms722617.aspx) w *OLE DB Podręcznik programisty*.  
  
 *długość* (opcjonalnie)  
 Zmiennej członkowskiej używanym do przechowywania w bajtach rozmiar kolumny.  
  
## <a name="remarks"></a>Uwagi  
 **db_param —** definiuje parametry czy użyć poleceń; w związku z tym korzystasz z **db_command —**. Na przykład można użyć **db_param —** by powiązać parametry zapytania SQL lub procedur składowanych. Parametry w procedurze składowanej są wskazywane przez znaki zapytania (?), a w kolejności, w którym są wyświetlane parametry muszą być powiązane elementy członkowskie danych.  
  
 **db_param —** rozgranicza danych elementów członkowskich, które mogą uczestniczyć w bazie danych OLE DB `ICommandWithParameters`— na podstawie powiązania. Ustawia typ parametru (wejściowych lub wyjściowych), typ OLE DB, dokładność, skalę, stanu i długość określonego parametru. Ten atrybut wstawia makra konsumenta OLE DB BEGIN_PARAM_MAP... END_PARAM_MAP. Każdy element członkowski oznaczyć z **db_param —** atrybutu zajmie jeden wpis w mapie w formie column_entry —.  
  
 **db_param —** jest używany w połączeniu z albo [db_table —](../windows/db-table.md) lub [db_command —](../windows/db-command.md) atrybutów.  
  
 Gdy dostawca atrybutu konsumenta stosuje ten atrybut do klasy, kompilator spowoduje zmianę nazwy klasy, która ma \_ *YourClassName*dostępu, gdzie *YourClassName* jest nazwa nadana klasy i kompilator utworzy klasy o nazwie *YourClassName*, co wynika ze \_ *YourClassName*metody dostępu.  W widoku klasy zostanie wyświetlona zarówno klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy klasę polecenia oparte na procedurę SalesbyYear przechowywane w bazie danych Northwind. Kojarzy pierwszy parametr w procedurze składowanej z `m_RETURN_VALUE` zmienną i definiuje ją jako parametr wyjściowy. Kojarzy ostatnich dwóch parametrów (wejścia) z `m_Beginning_Date` i `m_Ending_Date`.  
  
 W poniższym przykładzie `nOutput` zmiennej z parametru wyjściowego.  
  
```  
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
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, `struct`, elementu członkowskiego, metoda, lokalnego|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty konsumentów OLE DB](../windows/ole-db-consumer-attributes.md)   
