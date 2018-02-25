---
title: "Cdynamicaccessor — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicAccessor class
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1f07ceae02c9c243f59f37ea49e77ef3113b5a54
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor — Klasa
Umożliwia dostęp do źródła danych, gdy użytkownik nie korzystają z nie schematu bazy danych (wewnętrzna struktura bazy danych).  
  
## <a name="syntax"></a>Składnia

```cpp
class CDynamicAccessor : public CAccessorBase  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AddBindEntry](../../data/oledb/cdynamicaccessor-addbindentry.md)|Dodaje wpis powiązanie kolumn danych wyjściowych podczas zastępowania domyślnego akcesora.|  
|[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)|Tworzy i inicjuje `CDynamicAccessor` obiektu.|  
|[Zamknij](../../data/oledb/cdynamicaccessor-close.md)|Usuwa powiązanie wszystkie kolumny, zwalnia pamięć przydzielone i zwalnia [IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx) wskaźnika interfejsu w klasie.|  
|[GetBookmark](../../data/oledb/cdynamicaccessor-getbookmark.md)|Pobiera zakładki dla bieżącego wiersza.|  
|[GetBlobHandling](../../data/oledb/cdynamicaccessor-getblobhandling.md)|Pobiera BLOB obsługi wartość dla bieżącego wiersza.|  
|[GetBlobSizeLimit](../../data/oledb/cdynamicaccessor-getblobsizelimit.md)|Pobiera maksymalny rozmiar obiektu BLOB w bajtach.|  
|[GetColumnCount](../../data/oledb/cdynamicaccessor-getcolumncount.md)|Pobiera liczbę kolumn w zestawie wierszy.|  
|[GetColumnFlags](../../data/oledb/cdynamicaccessor-getcolumnflags.md)|Pobiera właściwości kolumny.|  
|[GetColumnInfo](../../data/oledb/cdynamicaccessor-getcolumninfo.md)|Pobiera metadane kolumny.|  
|[GetColumnName](../../data/oledb/cdynamicaccessor-getcolumnname.md)|Pobiera nazwę określonej kolumny.|  
|[GetColumnType](../../data/oledb/cdynamicaccessor-getcolumntype.md)|Pobiera typ danych określonej kolumny.|  
|[GetLength](../../data/oledb/cdynamicaccessor-getlength.md)|Pobiera maksymalną długość możliwe kolumny w bajtach.|  
|[GetOrdinal](../../data/oledb/cdynamicaccessor-getordinal.md)|Pobiera nazwę kolumny danego indeksu kolumny.|  
|[GetStatus](../../data/oledb/cdynamicaccessor-getstatus.md)|Pobiera stan określonej kolumny.|  
|[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)|Pobiera dane z bufora.|  
|[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)|Ustawia BLOB obsługi wartość dla bieżącego wiersza.|  
|[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)|Ustawia maksymalny rozmiar obiektu BLOB w bajtach.|  
|[Wartość SetLength](../../data/oledb/cdynamicaccessor-setlength.md)|Ustawia długość kolumny w bajtach.|  
|[SetStatus](../../data/oledb/cdynamicaccessor-setstatus.md)|Ustawia stan określonej kolumny.|  
|[SetValue](../../data/oledb/cdynamicaccessor-setvalue.md)|Przechowuje dane w buforze.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `CDynamicAccessor` metod, aby uzyskać informacje dotyczące kolumn, takich jak nazwy kolumn, liczba kolumn, typ danych i tak dalej. Te informacje kolumny jest następnie służą do tworzenia metody dostępu dynamicznie w czasie wykonywania.  
  
 Informacji o kolumnie znajduje się w buforze, który jest tworzony i zarządzany przez tę klasę. Uzyskiwanie danych z bufora przy użyciu [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md).  
  
 Omówienie i przykłady przy użyciu klasy dynamicznej metody dostępu, zobacz [przy użyciu dynamicznych metod dostępu](../../data/oledb/using-dynamic-accessors.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek**: atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor — klasa](../../data/oledb/caccessor-class.md)   
 [Cdynamicparameteraccessor — klasa](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor, klasa](../../data/oledb/cmanualaccessor-class.md)