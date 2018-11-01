---
title: ITopologyExecutionResource — Struktura
ms.date: 11/04/2016
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
helpviewer_keywords:
- ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
ms.openlocfilehash: fa4d8978cbdb5cab36367138ffb607a722b6b91a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631078"
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
