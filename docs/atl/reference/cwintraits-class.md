---
title: Klasa CWinTraits
ms.date: 11/04/2016
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
ms.openlocfilehash: fd73f733e4eff21da92937d1e1b0cce21552a48c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330310"
---
# <a name="cwintraits-class"></a>Klasa CWinTraits

Ta klasa zawiera metodę standaryzacji stylów używanych podczas tworzenia obiektu okna.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```

#### <a name="parameters"></a>Parametry

*t_dwStyle*<br/>
Domyślne standardowe style okien.

*t_dwExStyle*<br/>
Domyślne style rozszerzonego okna.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinTraits::GetWndExStyle](#getwndexstyle)|(Statyczne) Pobiera rozszerzone style `CWinTraits` obiektu.|
|[CWinTraits::GetWndStyle](#getwndstyle)|(Statyczne) Pobiera standardowe style `CWinTraits` obiektu.|

## <a name="remarks"></a>Uwagi

Ta klasa [cech okna](../../atl/understanding-window-traits.md) zapewnia prostą metodę standaryzacji stylów używanych do tworzenia obiektu okna ATL. Użyj specjalizacji tej klasy jako parametru szablonu [do CWindowImpl](../../atl/reference/cwindowimpl-class.md) lub innej klasy okna ATL, aby określić domyślne standardowe i rozszerzone style używane dla wystąpień tej klasy okna.

Użyj tego szablonu, jeśli chcesz zapewnić domyślne style okien, które będą używane tylko wtedy, gdy żadne inne style nie są określone w wywołaniu [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create).

ATL udostępnia trzy wstępnie zdefiniowane specjalizacje tego szablonu dla często używanych kombinacji stylów okien:

- `CControlWinTraits`

   Zaprojektowany dla standardowego okna sterującego. Używane są następujące style standardowe: WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN i WS_CLIPSIBLINGS. Nie ma rozszerzonych stylów.

- `CFrameWinTraits`

   Zaprojektowany dla standardowego okna ramy. Używane style standardowe obejmują: WS_OVERLAPPEDWINDOW, WS_CLIPCHILDREN i WS_CLIPSIBLINGS. Używane rozszerzone style obejmują: WS_EX_APPWINDOW i WS_EX_WINDOWEDGE.

- `CMDIChildWinTraits`

   Zaprojektowany dla standardowego okna podrzędnego MDI. Używane style standardowe obejmują: WS_OVERLAPPEDWINDOW, WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN i WS_CLIPSIBLINGS. Używane rozszerzone style obejmują: WS_EX_MDICHILD.

Jeśli chcesz upewnić się, że niektóre style są ustawione dla wszystkich wystąpień klasy okna, zezwalając na inne style, które mają być ustawione na podstawie wystąpienia, należy użyć [CWinTraitsOR](../../atl/reference/cwintraitsor-class.md) zamiast tego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="cwintraitsgetwndstyle"></a><a name="getwndstyle"></a>CWinTraits::GetWndStyle

Wywołanie tej funkcji, aby pobrać `CWinTraits` standardowe style obiektu.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Standardowe style używane do tworzenia okna. Jeśli *dwStyle* wynosi 0, zwracane są wartości stylu szablonu (`t_dwStyle`). Jeśli *dwStyle* jest niezerowy, *dwStyle* jest zwracany.

### <a name="return-value"></a>Wartość zwracana

Standardowe style okien obiektu.

## <a name="cwintraitsgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraits::GetWndExStyle

Wywołanie tej funkcji, aby pobrać `CWinTraits` rozszerzone style obiektu.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Parametry

*Dwexstyle*<br/>
Rozszerzone style używane do tworzenia okna. Jeśli *dwExStyle* jest 0, wartości`t_dwExStyle`stylu szablonu ( ) są zwracane. Jeśli *dwExStyle* jest niezerowy, *dwExStyle* jest zwracany.

### <a name="return-value"></a>Wartość zwracana

Rozszerzone style okien obiektu.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Opis cech okna](../../atl/understanding-window-traits.md)
