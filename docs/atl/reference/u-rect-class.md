---
title: Klasa _U_RECT
ms.date: 11/04/2016
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
ms.openlocfilehash: 306092a00a1e119263f4563eea181d7d3ee2b4b2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326377"
---
# <a name="urect-class"></a>Klasa _U_RECT

Ta klasa adaptera argument umożliwia albo `RECT` wskaźników lub odwołań, które zostaną przekazane do funkcji, która jest zaimplementowana w zakresie wskaźników.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class _U_RECT
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[_U_RECT::_U_RECT](#_u_rect___u_rect)|Konstruktor.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[_U_RECT::m_lpRect](#_u_rect__m_lprect)|Wskaźnik do `RECT`.|

## <a name="remarks"></a>Uwagi

Klasa definiuje dwa przeciążenia konstruktora: jeden akceptuje **Prostokąt &** argument, a druga akceptuje `LPRECT` argumentu. Pierwszy Konstruktor przechowuje adres argument odwołania w tej klasy danych jednego członka, [m_lpRect](#_u_rect__m_lprect). Argument Pro Konstruktor wskaźnik myszy znajduje się bezpośrednio, bez konwersji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="_u_rect__m_lprect"></a>  _U_RECT::m_lpRect

Klasa przechowuje wartość przekazana do jednej z jego konstruktorów jako publiczny `LPRECT` element członkowski danych.

```
LPRECT m_lpRect;
```

##  <a name="_u_rect___u_rect"></a>  _U_RECT::_U_RECT

Adres argument odwołania są przechowywane w składowej danych jednego klasy, [m_lpRect](#_u_rect__m_lprect).

```
_U_RECT(RECT& rc);
_U_RECT(LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*rc*<br/>
A `RECT` odwołania.

*lpRect*<br/>
A `RECT` wskaźnika.

### <a name="remarks"></a>Uwagi

Argument Pro Konstruktor wskaźnik myszy znajduje się bezpośrednio, bez konwersji.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
