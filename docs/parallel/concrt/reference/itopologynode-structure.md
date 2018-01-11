---
title: "Itopologynode — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ITopologyNode
- CONCRTRM/concurrency::ITopologyNode
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetExecutionResourceCount
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetFirstExecutionResource
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetId
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNext
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNumaNode
dev_langs: C++
helpviewer_keywords: ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9c2e989dca783e90d975bd46a6f5f44cdfa469ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="itopologynode-structure"></a>ITopologyNode — Struktura
Interfejs do węzła topologii, zgodnie z definicją przez Menedżera zasobów. Węzeł zawiera jeden lub więcej zasobów do wykonania.  
  
## <a name="syntax"></a>Składnia  
  
```
struct ITopologyNode;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ITopologyNode::GetExecutionResourceCount](#getexecutionresourcecount)|Zwraca liczbę zasobów wykonanie zgrupowane w tym węźle.|  
|[ITopologyNode::GetFirstExecutionResource](#getfirstexecutionresource)|Zwraca pierwszy zasób wykonywania zgrupowane w tym węźle, w kolejności wyliczenia.|  
|[ITopologyNode::GetId](#getid)|Zwraca unikatowy identyfikator menedżera zasobów dla tego węzła.|  
|[ITopologyNode::GetNext](#getnext)|Zwraca interfejs do następnego węzła topologii w kolejności wyliczenia.|  
|[ITopologyNode::GetNumaNode](#getnumanode)|Zwraca systemu Windows przypisany numer węzła NUMA, do której należy ten węzeł Maanger zasobów.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest zwykle wykorzystywany do przeszukania topologię systemu sprawdzane przez Menedżera zasobów.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ITopologyNode`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="getexecutionresourcecount"></a>ITopologyNode::GetExecutionResourceCount — metoda  
 Zwraca liczbę zasobów wykonanie zgrupowane w tym węźle.  
  
```
virtual unsigned int GetExecutionResourceCount() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba zasobów wykonanie zgrupowane w tym węźle.  
  
##  <a name="getfirstexecutionresource"></a>ITopologyNode::GetFirstExecutionResource — metoda  
 Zwraca pierwszy zasób wykonywania zgrupowane w tym węźle, w kolejności wyliczenia.  
  
```
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy zasób wykonywania zgrupowane w tym węźle, w kolejności wyliczenia.  
  
##  <a name="getid"></a>ITopologyNode::GetId — metoda  
 Zwraca unikatowy identyfikator menedżera zasobów dla tego węzła.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Menedżer zasobów Unikatowy identyfikator dla tego węzła.  
  
### <a name="remarks"></a>Uwagi  
 Współbieżność środowiska wykonawczego reprezentuje wątków sprzętu w systemie w grupach węzłów procesora. Węzły są zazwyczaj uzyskiwane z topologii sprzętu systemu. Na przykład wszystkie procesory w określonych gniazda lub określonego węzła NUMA może należeć do tego samego węzła procesora. Menedżer zasobów przypisuje unikatowych identyfikatorów dla tych węzłów, począwszy od `0` włącznie `nodeCount - 1`, gdzie `nodeCount` reprezentuje łączna liczba węzłów procesora w systemie.  
  
 Liczba węzłów, można je uzyskać z funkcji [getprocessornodecount —](concurrency-namespace-functions.md).  
  
##  <a name="getnext"></a>ITopologyNode::GetNext — metoda  
 Zwraca interfejs do następnego węzła topologii w kolejności wyliczenia.  
  
```
virtual ITopologyNode *GetNext() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Interfejs do następnego węzła w kolejności wyliczenia. Jeśli nie ma żadnych więcej węzłów w kolejności wyliczenia topologii systemu, ta metoda zwróci wartość `NULL`.  
  
##  <a name="getnumanode"></a>ITopologyNode::GetNumaNode — metoda  
 Zwraca systemu Windows przypisany numer węzła NUMA, do której należy ten węzeł Maanger zasobów.  
  
```
virtual unsigned long GetNumaNode() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Systemu Windows przypisany numer węzła NUMA, do której należy ten węzeł Menedżera zasobów.  
  
### <a name="remarks"></a>Uwagi  
 Serwer proxy wątku uruchomiona na głównym procesorów wirtualnych należących do tego węzła ma koligacji co najmniej poziom węzeł NUMA dla węzła NUMA, zwracane przez tę metodę.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
