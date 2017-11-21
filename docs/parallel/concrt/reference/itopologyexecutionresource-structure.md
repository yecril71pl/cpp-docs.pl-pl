---
title: "Itopologyexecutionresource — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
dev_langs: C++
helpviewer_keywords: ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9ffe0e2d8f4c26274a71082bec2cecaf19acb1af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource — Struktura
Interfejs do zasobu wykonywania zdefiniowanej przez Menedżera zasobów.  
  
## <a name="syntax"></a>Składnia  
  
```
struct ITopologyExecutionResource;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ITopologyExecutionResource::GetId](#getid)|Zwraca unikatowy identyfikator menedżera zasobów dla tego zasobu wykonywania.|  
|[ITopologyExecutionResource::GetNext](#getnext)|Zwraca interfejs do następnego zasobu wykonywania w kolejności wyliczenia.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest zwykle wykorzystywany do przeszukania topologię systemu sprawdzane przez Menedżera zasobów.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ITopologyExecutionResource`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="getid"></a>ITopologyExecutionResource::GetId — metoda  
 Zwraca unikatowy identyfikator menedżera zasobów dla tego zasobu wykonywania.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Menedżer zasobów Unikatowy identyfikator dla tego zasobu wykonywania.  
  
##  <a name="getnext"></a>ITopologyExecutionResource::GetNext — metoda  
 Zwraca interfejs do następnego zasobu wykonywania w kolejności wyliczenia.  
  
```
virtual ITopologyExecutionResource *GetNext() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Interfejs do następnego zasobu wykonywania w kolejności wyliczenia. Jeśli nie ma żadnych więcej węzłów w kolejności wyliczenia węzła, do której należy dany zasób wykonywania, ta metoda zwróci wartość `NULL`.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)
