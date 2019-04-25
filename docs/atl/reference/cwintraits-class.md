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
ms.openlocfilehash: 840433ffb325a4f181848371306607b62373e75a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276786"
---
# <a name="cwintraits-class"></a>Klasa CWinTraits

Ta klasa dostarcza metody do standaryzacji stylów używanych podczas tworzenia obiektu okna.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```

#### <a name="parameters"></a>Parametry

*t_dwStyle*<br/>
Domyślne style standardowego okna.

*t_dwExStyle*<br/>
Domyślnie rozszerzone Style okna.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinTraits::GetWndExStyle](#getwndexstyle)|(Statyczny) Pobiera rozszerzone style `CWinTraits` obiektu.|
|[CWinTraits::GetWndStyle](#getwndstyle)|(Statyczny) Pobiera standardowe style dla `CWinTraits` obiektu.|

## <a name="remarks"></a>Uwagi

To [cech okna](../../atl/understanding-window-traits.md) klasa udostępnia prostą metodę standaryzacji stylów używany do tworzenia obiektu ATL okna. Użyj specjalizacji tej klasy jako parametr szablonu [CWindowImpl](../../atl/reference/cwindowimpl-class.md) lub innej klasy okien ATL, aby określić wartości domyślnej standardowe i rozszerzone stylów używanych dla wystąpień tej klasy okna.

Użyj tego szablonu, które chcesz udostępnić domyślne style okna, które będą używane tylko wtedy, gdy nie inne style są określone w wywołaniu [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create).

ATL zawiera trzy wstępnie zdefiniowane specjalizacje szablonu dla często używanych kombinacji Style okna ramowego:

- `CControlWinTraits`

   Zaprojektowana na potrzeby okna formantu standardowego. Używane są następujące standardowe style: WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN i WS_CLIPSIBLINGS. Nie istnieją żadne rozszerzone style.

- `CFrameWinTraits`

   Zaprojektowana na potrzeby standardowych ramki okna. Standardowe style używane obejmują: WS_OVERLAPPEDWINDOW WS_CLIPCHILDREN i WS_CLIPSIBLINGS. Rozszerzone style używane obejmują: WS_EX_APPWINDOW i WS_EX_WINDOWEDGE.

- `CMDIChildWinTraits`

   Zaprojektowana na potrzeby standardowe okno podrzędne MDI. Standardowe style używane obejmują: WS_OVERLAPPEDWINDOW WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN i WS_CLIPSIBLINGS. Rozszerzone style używane obejmują: WS_EX_MDICHILD.

Jeśli chcesz upewnić się, że określone style są ustawione dla wszystkich wystąpień klasy okna, umożliwiając innymi stylami należy ustawić na podstawie poszczególnych wystąpień [CWinTraitsOR](../../atl/reference/cwintraitsor-class.md) zamiast tego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="getwndstyle"></a>  CWinTraits::GetWndStyle

Wywołaj tę funkcję, aby pobrać standardowa style `CWinTraits` obiektu.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Standardowe style służy do tworzenia okna. Jeśli *dwStyle* ma wartość 0, wartości styl szablonu (`t_dwStyle`) są zwracane. Jeśli *dwStyle* jest różna od zera, *dwStyle* jest zwracana.

### <a name="return-value"></a>Wartość zwracana

Style okna standardowego obiektu.

##  <a name="getwndexstyle"></a>  CWinTraits::GetWndExStyle

Wywołaj tę funkcję, aby pobrać rozszerzone style `CWinTraits` obiektu.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Parametry

*dwExStyle*<br/>
Rozszerzone style służy do tworzenia okna. Jeśli *dwExStyle* ma wartość 0, wartości styl szablonu (`t_dwExStyle`) są zwracane. Jeśli *dwExStyle* jest różna od zera, *dwExStyle* jest zwracana.

### <a name="return-value"></a>Wartość zwracana

Rozszerzone Style okna obiektu.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Opis cech okna](../../atl/understanding-window-traits.md)
