---
title: Itopologyexecutionresource — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
dev_langs:
- C++
helpviewer_keywords:
- ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: adb456315b2c6d15b7a3696df9a6845a2bd2b899
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
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
  
##  <a name="getid"></a>  ITopologyExecutionResource::GetId — metoda  
 Zwraca unikatowy identyfikator menedżera zasobów dla tego zasobu wykonywania.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Menedżer zasobów Unikatowy identyfikator dla tego zasobu wykonywania.  
  
##  <a name="getnext"></a>  ITopologyExecutionResource::GetNext — metoda  
 Zwraca interfejs do następnego zasobu wykonywania w kolejności wyliczenia.  
  
```
virtual ITopologyExecutionResource *GetNext() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Interfejs do następnego zasobu wykonywania w kolejności wyliczenia. Jeśli nie ma żadnych więcej węzłów w kolejności wyliczenia węzła, do której należy dany zasób wykonywania, ta metoda zwróci wartość `NULL`.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
