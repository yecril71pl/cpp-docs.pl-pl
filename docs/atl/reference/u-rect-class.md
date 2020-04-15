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
ms.openlocfilehash: 8a4d5b2a770b3f0ecfe10be0fbad22a702aa0531
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325807"
---
# <a name="_u_rect-class"></a>Klasa _U_RECT

Ta klasa karty argumentu umożliwia `RECT` wskaźniki lub odwołania mają być przekazywane do funkcji, która jest implementowana pod względem wskaźników.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

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
|[_U_RECT::m_lpRect](#_u_rect__m_lprect)|Wskaźnik do `RECT`pliku .|

## <a name="remarks"></a>Uwagi

Klasa definiuje dwa przeciążenia konstruktora: jeden akceptuje **RECT argument&,** `LPRECT` a drugi akceptuje argument. Pierwszy konstruktor przechowuje adres argumentu odwołania w pojedynczym elementów członkowskich klasy danych, [m_lpRect](#_u_rect__m_lprect). Argument do konstruktora wskaźnika jest przechowywany bezpośrednio bez konwersji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="_u_rectm_lprect"></a><a name="_u_rect__m_lprect"></a>_U_RECT::m_lpRect

Klasa przechowuje wartość przekazywana do jednego z `LPRECT` jego konstruktorów jako element członkowski danych publicznych.

```
LPRECT m_lpRect;
```

## <a name="_u_rect_u_rect"></a><a name="_u_rect___u_rect"></a>_U_RECT::_U_RECT

Adres argumentu odwołania jest przechowywany w pojedynczym elementów członkowskich danych klasy, [m_lpRect](#_u_rect__m_lprect).

```
_U_RECT(RECT& rc);
_U_RECT(LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*Rc*<br/>
Odwołanie. `RECT`

*Lprect*<br/>
Wskaźnik. `RECT`

### <a name="remarks"></a>Uwagi

Argument do konstruktora wskaźnika jest przechowywany bezpośrednio bez konwersji.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
