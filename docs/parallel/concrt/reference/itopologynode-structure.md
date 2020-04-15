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
ms.openlocfilehash: 7cb815c4f7dc5ad09e8d352abc3f3375b8d9e205
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368107"
---
# <a name="itopologynode-structure"></a>ITopologyNode — Struktura

Interfejs do węzła topologii zdefiniowany przez Menedżera zasobów. Węzeł zawiera co najmniej jeden materiał wykonawczy.

## <a name="syntax"></a>Składnia

```cpp
struct ITopologyNode;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ITopologiaNode::GetExecutionResourceCount](#getexecutionresourcecount)|Zwraca liczbę zasobów wykonywania zgrupowanych w tym węźle.|
|[ITopologiaNode::GetFirstExecutionResource](#getfirstexecutionresource)|Zwraca pierwszy zasób wykonania zgrupowany w tym węźle w kolejności wyliczenia.|
|[ITopologiaNode::GetId](#getid)|Zwraca unikatowy identyfikator Menedżera zasobów dla tego węzła.|
|[ITopologiaNode::GetNext](#getnext)|Zwraca interfejs do następnego węzła topologii w kolejności wyliczenia.|
|[ITopologiaNode::GetNumaNode](#getnumanode)|Zwraca przypisany przez system Windows numer węzła NUMA, do którego należy ten węzeł Maanger zasobów.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest zazwyczaj używany do chodzenia topologii systemu, zgodnie z obserwowanym przez Menedżera zasobów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ITopologyNode`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Przestrzeń nazw:** współbieżność

## <a name="itopologynodegetexecutionresourcecount-method"></a><a name="getexecutionresourcecount"></a>ITopologiaNode::Metoda GetExecutionResourceCount

Zwraca liczbę zasobów wykonywania zgrupowanych w tym węźle.

```cpp
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Liczba zasobów wykonywania zgrupowanych w tym węźle.

## <a name="itopologynodegetfirstexecutionresource-method"></a><a name="getfirstexecutionresource"></a>ITopologiaNode::Metoda GetFirstExecutionResource

Zwraca pierwszy zasób wykonania zgrupowany w tym węźle w kolejności wyliczenia.

```cpp
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy zasób wykonywania zgrupowane w tym węźle w kolejności wyliczenia.

## <a name="itopologynodegetid-method"></a><a name="getid"></a>ITopologiaNode::Metoda GetId

Zwraca unikatowy identyfikator Menedżera zasobów dla tego węzła.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Unikatowy identyfikator Menedżera zasobów dla tego węzła.

### <a name="remarks"></a>Uwagi

Środowisko wykonawcze współbieżności reprezentuje wątki sprzętowe w systemie w grupach węzłów procesora. Węzły są zwykle pochodną topologii sprzętowej systemu. Na przykład wszystkie procesory w określonym gnieździe lub określonym węźle NUMA mogą należeć do tego samego węzła procesora. Menedżer zasobów przypisuje unikatowe identyfikatory do `0` tych węzłów, zaczynając od maksymalnie do momentu włącznie `nodeCount - 1`, gdzie `nodeCount` reprezentuje całkowitą liczbę węzłów procesora w systemie.

Liczbę węzłów można uzyskać z funkcji [GetProcessorNodeCount](concurrency-namespace-functions.md).

## <a name="itopologynodegetnext-method"></a><a name="getnext"></a>ITopologiaNode::Metoda GetNext

Zwraca interfejs do następnego węzła topologii w kolejności wyliczenia.

```cpp
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Interfejs do następnego węzła w kolejności wyliczenia. Jeśli nie ma więcej węzłów w kolejności wyliczenia topologii systemu, `NULL`ta metoda zwróci wartość .

## <a name="itopologynodegetnumanode-method"></a><a name="getnumanode"></a>ITopologiaNode::Metoda GetNumaNode

Zwraca przypisany przez system Windows numer węzła NUMA, do którego należy ten węzeł Maanger zasobów.

```cpp
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Numer węzła NUMA, do którego należy ten węzeł Menedżera zasobów.

### <a name="remarks"></a>Uwagi

Serwer proxy wątku uruchomiony w katalogu głównym procesora wirtualnego należącym do tego węzła będzie miał koligacji co najmniej do poziomu węzła NUMA dla węzła NUMA zwróconego przez tę metodę.

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)
