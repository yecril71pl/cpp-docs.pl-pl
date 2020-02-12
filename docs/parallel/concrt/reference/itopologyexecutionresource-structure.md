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
ms.openlocfilehash: 82193a9b592cded96f3726cbabd6cf646eaa27c8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140069"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource — Struktura

Interfejs do zasobu wykonywania określony przez Menedżer zasobów.

## <a name="syntax"></a>Składnia

```cpp
struct ITopologyExecutionResource;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[ITopologyExecutionResource:: GetId —](#getid)|Zwraca unikatowy identyfikator Menedżer zasobów dla tego zasobu wykonania.|
|[ITopologyExecutionResource:: GetNext](#getnext)|Zwraca interfejs do następnego zasobu wykonania w kolejności wyliczania.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest zazwyczaj używany do przeszukiwania topologii systemu widzianych przez Menedżer zasobów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ITopologyExecutionResource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm. h

**Przestrzeń nazw:** współbieżność

## <a name="getid"></a>ITopologyExecutionResource:: GetId —, Metoda

Zwraca unikatowy identyfikator Menedżer zasobów dla tego zasobu wykonania.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Unikatowy identyfikator Menedżer zasobów dla tego zasobu wykonania.

## <a name="getnext"></a>ITopologyExecutionResource:: GetNext — Metoda

Zwraca interfejs do następnego zasobu wykonania w kolejności wyliczania.

```cpp
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Interfejs do następnego zasobu wykonywania w kolejności wyliczania. Jeśli nie ma więcej węzłów w kolejności wyliczania węzła, do którego należy ten zasób wykonania, ta metoda zwróci wartość `NULL`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
