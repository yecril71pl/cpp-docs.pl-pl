---
title: Klasa CWinTraitsOR
ms.date: 11/04/2016
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
ms.openlocfilehash: 825f79190c6f68cd1372154e4e02f430f545aa48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330283"
---
# <a name="cwintraitsor-class"></a>Klasa CWinTraitsOR

Ta klasa zawiera metodę standaryzacji stylów używanych podczas tworzenia obiektu okna.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0,
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```

#### <a name="parameters"></a>Parametry

*t_dwStyle*<br/>
Domyślne style okien.

*t_dwExStyle*<br/>
Domyślne style rozszerzonego okna.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|Pobiera rozszerzone style `CWinTraitsOR` obiektu.|
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|Pobiera standardowe style `CWinTraitsOR` obiektu.|

## <a name="remarks"></a>Uwagi

Ta klasa [cech okna](../../atl/understanding-window-traits.md) zapewnia prostą metodę standaryzacji stylów używanych do tworzenia obiektu okna ATL. Użyj specjalizacji tej klasy jako parametru szablonu [do CWindowImpl](../../atl/reference/cwindowimpl-class.md) lub innej klasy okna ATL, aby określić minimalny zestaw stylów standardowych i rozszerzonych, które mają być używane dla wystąpień tej klasy okna.

Użyj specjalizacji tego szablonu, jeśli chcesz upewnić się, że niektóre style są ustawione dla wszystkich wystąpień klasy okna, zezwalając na inne style, które mają być ustawione na podstawie wystąpienia w wywołaniu [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create).

Jeśli chcesz podać domyślne style okien, które będą używane tylko wtedy, gdy żadne inne style nie są określone w wywołaniu , `CWindowImpl::Create`użyj [CWinTraits](../../atl/reference/cwintraits-class.md) zamiast.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="cwintraitsorgetwndstyle"></a><a name="getwndstyle"></a>CWinTraitsOR::GetWndStyle

Wywołanie tej funkcji w celu pobrania kombinacji (przy użyciu operatora `CWinTraits` logicznego OR) standardowych stylów obiektu i domyślnych stylów określonych przez *t_dwStyle*.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Style używane do tworzenia okna.

### <a name="return-value"></a>Wartość zwracana

Kombinacja stylów, które są przekazywane w *dwStyle* i domyślne te określone przez `t_dwStyle`, przy użyciu operatora logicznego OR.

## <a name="cwintraitsorgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraitsOR::GetWndExStyle

Wywołanie tej funkcji w celu pobrania kombinacji (przy użyciu operatora `CWinTraits` logicznego OR) rozszerzonych stylów obiektu i domyślnych stylów określonych przez `t_dwStyle`program .

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Parametry

*Dwexstyle*<br/>
Rozszerzone style używane do tworzenia okna.

### <a name="return-value"></a>Wartość zwracana

Kombinacja rozszerzonych stylów przekazywanych w *dwExStyle* i domyślnych określonych przez `t_dwExStyle`operatora OR przy użyciu operatora logicznego OR

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Opis cech okna](../../atl/understanding-window-traits.md)
