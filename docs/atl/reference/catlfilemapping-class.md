---
title: Klasa CAtlFileMapping | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
dev_langs:
- C++
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ccbf3221bddf39c8069e20636c2f2a1deb597866
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116467"
---
# <a name="catlfilemapping-class"></a>Klasa CAtlFileMapping

Ta klasa reprezentuje plik mapowany w pamięci, dodanie operatora rzutowania do metod [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych użyte dla operatora rzutowania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlFileMapping::operator T *](#operator_t_star)|Umożliwia niejawną konwersję `CAtlFileMapping` obiekty do `T*`.|

## <a name="remarks"></a>Uwagi

Ta klasa dodaje operatora rzutowania pojedynczej umożliwia niejawną konwersję `CAtlFileMapping` obiekty do `T*`. Inni członkowie są dostarczane przez klasę bazową [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlfile.h

##  <a name="operator_t_star"></a>  CAtlFileMapping::operator T *

Umożliwia niejawną konwersję `CAtlFileMapping` obiekty do `T*`.

```
operator T*() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `T*` wskaźnik do początku plików mapowanych na pamięć.

### <a name="remarks"></a>Uwagi

Wywołania [CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) i reinterpretuje obiekt zwrócony wskaźnik jako `T*` gdzie *T* jest typ używany jako parametr szablonu tej klasy.

## <a name="see-also"></a>Zobacz też

[Klasa CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
