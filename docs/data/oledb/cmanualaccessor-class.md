---
title: Cmanualaccessor — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7b8efc46971b1aa72f8c5e572aa540bfed250d2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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