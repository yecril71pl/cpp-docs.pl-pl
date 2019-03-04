---
title: ITopologyNode — Struktura
ms.date: 11/04/2016
f1_keywords:
- ITopologyNode
- CONCRTRM/concurrency::ITopologyNode
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetExecutionResourceCount
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetFirstExecutionResource
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetId
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNext
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNumaNode
helpviewer_keywords:
- ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
ms.openlocfilehash: 867e0543d1b9f2810a3fe761f038947c4d88da4d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268632"
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
|[ITopologyNode::GetExecutionResourceCount](#getexecutionresourcecount)|Zwraca liczbę zasobów wykonywania zgrupowane razem w tym węźle.|
|[ITopologyNode::GetFirstExecutionResource](#getfirstexecutionresource)|Zwraca pierwszy zasób wykonywania pogrupowane w tym węźle, w kolejności wyliczenia.|
|[ITopologyNode::GetId](#getid)|Zwraca unikatowy identyfikator menedżera zasobów dla tego węzła.|
|[Itopologynode::GETNEXT —](#getnext)|Zwraca interfejs do kolejnego węzła topologii, w kolejności wyliczenia.|
|[Itopologynode::getnumanode —](#getnumanode)|Zwraca Windows przypisał numer węzła NUMA, do której należy ten węzeł Menedżera zasobów.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest zazwyczaj wykorzystywana przeprowadzenie topologię systemu obserwowanych przez Menedżera zasobów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ITopologyNode`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Namespace:** współbieżności

##  <a name="getexecutionresourcecount"></a>  Itopologynode::getexecutionresourcecount — metoda

Zwraca liczbę zasobów wykonywania zgrupowane razem w tym węźle.

```
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Liczba zasobów wykonywania zgrupowane razem w tym węźle.

##  <a name="getfirstexecutionresource"></a>  Itopologynode::getfirstexecutionresource — metoda

Zwraca pierwszy zasób wykonywania pogrupowane w tym węźle, w kolejności wyliczenia.

```
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy zasób wykonywania są grupowane w tym węźle, w kolejności wyliczenia.

##  <a name="getid"></a>  Itopologynode::getid — metoda

Zwraca unikatowy identyfikator menedżera zasobów dla tego węzła.

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Menedżer zasobów Unikatowy identyfikator dla tego węzła.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe współbieżności reprezentuje wątków sprzętu w systemie w grupy węzłów procesora. Węzły są zazwyczaj uzyskiwane z topologii sprzętu systemu. Na przykład wszystkie procesory w określonych gniazdo lub określonego węzła NUMA może należeć do tego samego węzła procesora. Menedżer zasobów przypisuje unikatowych identyfikatorów do tych węzłów, począwszy od `0` włącznie `nodeCount - 1`, gdzie `nodeCount` reprezentuje całkowita liczba węzłów procesora w systemie.

Liczba węzłów można uzyskać z funkcji [getprocessornodecount —](concurrency-namespace-functions.md).

##  <a name="getnext"></a>  Itopologynode::GETNEXT — metoda

Zwraca interfejs do kolejnego węzła topologii, w kolejności wyliczenia.

```
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Interfejs do kolejnego węzła w kolejności wyliczenia. Jeśli nie ma żadnych więcej węzłów w kolejności wyliczenia topologii systemu, ta metoda zwróci wartość `NULL`.

##  <a name="getnumanode"></a>  Itopologynode::getnumanode — metoda

Zwraca Windows przypisał numer węzła NUMA, do której należy ten węzeł Menedżera zasobów.

```
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Windows przypisał numer węzła NUMA, do której należy ten węzeł Menedżera zasobów.

### <a name="remarks"></a>Uwagi

Serwer proxy wątków, uruchomiony na należącym do tego węzła głównym procesorze wirtualnym, będzie miał koligacje do co najmniej poziomu węzła NUMA dla węzła NUMA zwracanego przez tę metodę.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
