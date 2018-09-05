---
title: Klasa _U_RECT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
dev_langs:
- C++
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1041141e9f31e59ab7a1884e976828972c0abd91
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767327"
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

*RC*  
A `RECT` odwołania.

*lprect —*  
A `RECT` wskaźnika.

### <a name="remarks"></a>Uwagi

Argument Pro Konstruktor wskaźnik myszy znajduje się bezpośrednio, bez konwersji.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
