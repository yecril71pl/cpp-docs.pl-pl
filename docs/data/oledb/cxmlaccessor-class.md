---
title: Klasa CXMLAccessor | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CXMLAccessor
- CXMLAccessor
- ATL.CXMLAccessor
dev_langs: C++
helpviewer_keywords: CXMLAccessor class
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 102dee928d1a6b8bbfcde80c46f097d67cf76a42
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cxmlaccessor-class"></a>Klasa CXMLAccessor
Umożliwia dostęp do źródeł danych jako ciągu dane podczas nie znają schematu magazynu danych (struktury).  
  
## <a name="syntax"></a>Składnia  
  
```  
class CXMLAccessor : public CDynamicStringAccessorW  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md)|Pobiera informacji o kolumnie.|  
|[GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md)|Pobiera całą zawartość tabeli według wierszy.|  
  
## <a name="remarks"></a>Uwagi  
 Jednak `CXMLAccessor` różni się od `CDynamicStringAccessorW` w tym konwertuje wszystkie dane uzyskiwane ze źródła danych jako dane (oznakowany) w formacie XML. Jest to szczególnie przydatne dla danych wyjściowych do stron sieci Web obsługującym kod XML. Nazwy tagów XML będzie odpowiadała możliwie nazwy kolumn w magazynie danych.  
  
 Użyj `CDynamicAccessor` metod, aby uzyskać informacje dotyczące kolumn. Informacje te kolumny umożliwia tworzenie akcesor dynamicznie w czasie wykonywania.  
  
 Informacji o kolumnie znajduje się w buforze tworzone i zarządzane przez tę klasę. Uzyskaj informacje przy użyciu kolumny [GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) lub uzyskać danych kolumny w wiersze, używając [GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md).  
  
## <a name="example"></a>Przykład  
 [!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek**: atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor — klasa](../../data/oledb/caccessor-class.md)   
 [Cdynamicaccessor — klasa](../../data/oledb/cdynamicaccessor-class.md)   
 [Cdynamicparameteraccessor — klasa](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [Cdynamicstringaccessor — klasa](../../data/oledb/cdynamicstringaccessor-class.md)   
 [Cdynamicstringaccessora — klasa](../../data/oledb/cdynamicstringaccessora-class.md)   
 [Cdynamicstringaccessorw — klasa](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [Cmanualaccessor — klasa](../../data/oledb/cmanualaccessor-class.md)