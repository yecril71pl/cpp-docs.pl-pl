---
title: Klasa CAtlFileMapping
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: 7516349e4ec54d8cb90fa6ff23b0ded954aa043b
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168127"
---
# <a name="catlfilemapping-class"></a>Klasa CAtlFileMapping

Ta klasa reprezentuje plik mapowany w pamięci, dodając operator rzutowania do metod [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```cpp
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych używanych dla operatora rzutowania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlFileMapping:: operator T *](#operator_t_star)|Zezwala na niejawną konwersję `CAtlFileMapping` obiektów do. `T*`|

## <a name="remarks"></a>Uwagi

Ta klasa dodaje pojedynczy operator rzutowania, aby umożliwić niejawną konwersję `CAtlFileMapping` obiektów do. `T*` Inne składowe są dostarczane przez klasę bazową, [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlfile. h

## <a name="catlfilemappingoperator-t"></a><a name="operator_t_star"></a>CAtlFileMapping:: operator T *

Zezwala na niejawną konwersję `CAtlFileMapping` obiektów do. `T*`

```cpp
operator T*() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `T*` wskaźnik do początku pliku mapowanego na pamięć.

### <a name="remarks"></a>Uwagi

Wywołuje [CAtlFileMappingBase:: GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) i ponownie interpretuje zwrócony wskaźnik jako `T*` gdzie *T* jest typem używanym jako parametr szablonu tej klasy.

## <a name="see-also"></a>Zobacz także

[Klasa CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
