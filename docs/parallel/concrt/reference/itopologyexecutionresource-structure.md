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
ms.openlocfilehash: 2c9221cab1ac2d48bd099a769188e4bee797823c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368148"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource — Struktura

Interfejs do zasobu wykonywania zdefiniowane przez Menedżera zasobów.

## <a name="syntax"></a>Składnia

```cpp
struct ITopologyExecutionResource;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ITopologiaWynikreźródło::GetId](#getid)|Zwraca unikatowy identyfikator Menedżera zasobów dla tego zasobu wykonania.|
|[ITopologiaWynikreźródło::GetNext](#getnext)|Zwraca interfejs do następnego zasobu wykonywania w kolejności wyliczenia.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest zazwyczaj używany do chodzenia topologii systemu, zgodnie z obserwowanym przez Menedżera zasobów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ITopologyExecutionResource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Przestrzeń nazw:** współbieżność

## <a name="itopologyexecutionresourcegetid-method"></a><a name="getid"></a>ITopologiaExecutionResource::Metoda GetId

Zwraca unikatowy identyfikator Menedżera zasobów dla tego zasobu wykonania.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Unikatowy identyfikator Menedżera zasobów dla tego zasobu wykonywania.

## <a name="itopologyexecutionresourcegetnext-method"></a><a name="getnext"></a>ITopologiaExecutionResource::Metoda GetNext

Zwraca interfejs do następnego zasobu wykonywania w kolejności wyliczenia.

```cpp
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Interfejs do następnego zasobu wykonywania w kolejności wyliczenia. Jeśli nie ma więcej węzłów w kolejności wyliczenia węzła, do którego należy `NULL`ten zasób wykonywania, ta metoda zwróci wartość .

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)
