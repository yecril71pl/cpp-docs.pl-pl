---
title: "Cmanualaccessor — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
dev_langs:
- C++
helpviewer_keywords:
- CManualAccessor class
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ecb9f31c862f62ddc2422f201aa824a959e961a0
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cmanualaccessor-class"></a>CManualAccessor — Klasa
Reprezentuje typ metody dostępu przeznaczony dla zaawansowanych.  
  
## <a name="syntax"></a>Składnia

```cpp
class CManualAccessor : public CAccessorBase  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md)|Dodaje wpis powiązanie kolumn danych wyjściowych.|  
|[AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)|Dodaje wpis parametru do akcesor parametru.|  
|[CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)|Przydziela pamięć dla kolumny struktury powiązania i inicjuje elementów członkowskich danych kolumny.|  
|[CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)|Przydziela pamięć dla parametru wiązania struktury i inicjuje elementy członkowskie danych parametru.|  
  
## <a name="remarks"></a>Uwagi  
 Przy użyciu `CManualAccessor`, należy określić parametr, a dane wyjściowe powiązanie kolumny według wywołania funkcji środowiska wykonawczego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [DBViewer](../../visual-cpp-samples.md)   
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor — klasa](../../data/oledb/caccessor-class.md)   
 [Cdynamicaccessor — klasa](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor, klasa](../../data/oledb/cdynamicparameteraccessor-class.md)