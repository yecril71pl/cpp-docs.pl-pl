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
ms.openlocfilehash: 60a0097aded73e3e0251d38daf5da71197668d3a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383795"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource — Struktura

Interfejs z zasobem wykonywania, zgodnie z definicją przez Menedżera zasobów.

## <a name="syntax"></a>Składnia

```
struct ITopologyExecutionResource;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Itopologyexecutionresource::getid —](#getid)|Zwraca unikatowy identyfikator dla tego zasobu wykonywania, Menedżer zasobów.|
|[Itopologyexecutionresource::GETNEXT —](#getnext)|Zwraca interfejs do następnego wykonania zasobu w kolejności wyliczenia.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest zazwyczaj wykorzystywana przeprowadzenie topologię systemu obserwowanych przez Menedżera zasobów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ITopologyExecutionResource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Namespace:** współbieżności

##  <a name="getid"></a>  Itopologyexecutionresource::getid — metoda

Zwraca unikatowy identyfikator dla tego zasobu wykonywania, Menedżer zasobów.

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Menedżer zasobów Unikatowy identyfikator dla tego zasobu wykonywania.

##  <a name="getnext"></a>  Itopologyexecutionresource::GETNEXT — metoda

Zwraca interfejs do następnego wykonania zasobu w kolejności wyliczenia.

```
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Interfejs do następnego wykonania zasobu w kolejności wyliczenia. Jeśli nie ma żadnych więcej węzłów w kolejności wyliczenia węzła, do której należy dany zasób wykonywania, ta metoda zwróci wartość `NULL`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
