---
title: Klasa CAtlFileMapping
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: ca46ccdacf5ea24f1de26cdc75bf808c4ecfaa40
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318956"
---
# <a name="catlfilemapping-class"></a>Klasa CAtlFileMapping

Ta klasa reprezentuje plik mapowany w pamięci, dodając operator rzutowania do metod [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych używanych dla operatora rzutu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlFileMapping::operator T*](#operator_t_star)|Umożliwia niejawną `CAtlFileMapping` `T*`konwersję obiektów do .|

## <a name="remarks"></a>Uwagi

Ta klasa dodaje pojedynczy operator rzutowania, aby umożliwić niejawną konwersję `CAtlFileMapping` obiektów do `T*`. Inne elementy członkowskie są dostarczane przez klasę podstawową [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Baza danych CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlfile.h

## <a name="catlfilemappingoperator-t"></a><a name="operator_t_star"></a>CAtlFileMapping::operator T*

Umożliwia niejawną `CAtlFileMapping` `T*`konwersję obiektów do .

```
operator T*() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `T*` wskaźnik do początku pliku mapowane w pamięci.

### <a name="remarks"></a>Uwagi

Wywołuje [CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) i reinterpretuje zwrócony wskaźnik jako gdzie `T*` *T* jest typem używanym jako parametr szablonu tej klasy.

## <a name="see-also"></a>Zobacz też

[Klasa CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
