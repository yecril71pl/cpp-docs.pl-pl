---
title: Klasa _U_STRINGorID
ms.date: 11/04/2016
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
ms.openlocfilehash: 4e46ceec077b8daf8ef2a76110d2fc19dd39ae26
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325821"
---
# <a name="_u_stringorid-class"></a>Klasa _U_STRINGorID

Ta klasa karty argumentów umożliwia przekazywanie nazw zasobów (LPCTS) lub identyfikatorów zasobów (UINTs) do funkcji bez konieczności konwertowania identyfikatora na ciąg przy użyciu makra MAKEINTRESOURCE.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class _U_STRINGorID
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|Konstruktor.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|Identyfikator zasobu.|

## <a name="remarks"></a>Uwagi

Ta klasa jest przeznaczona do implementowania otoki do interfejsu API zarządzania zasobami systemu Windows, takich jak [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea), [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)i [LoadMenu](/windows/win32/api/winuser/nf-winuser-loadmenuw) funkcje, które akceptują LPCTSTR argument, który może być nazwą zasobu lub jego identyfikator.

Klasa definiuje dwa przeciążenia konstruktora: jeden akceptuje argument LPCTSTR, a drugi akceptuje argument UINT. Argument UINT jest konwertowany na typ zasobu zgodny z funkcjami zarządzania zasobami systemu Windows przy użyciu makra MAKEINTRESOURCE i wyniku przechowywanego w pojedynczym członu danych klasy, [m_lpstr](#_u_stringorid__m_lpstr). Argument do konstruktora LPCTSTR jest przechowywany bezpośrednio bez konwersji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="_u_stringoridm_lpstr"></a><a name="_u_stringorid__m_lpstr"></a>_U_STRINGorID::m_lpstr

Klasa przechowuje wartość przekazywana do jednego z jego konstruktorów jako publiczny element członkowski danych LPCTSTR.

```
LPCTSTR m_lpstr;
```

## <a name="_u_stringorid_u_stringorid"></a><a name="_u_stringorid___u_stringorid"></a>_U_STRINGorID::_U_STRINGorID

Konstruktor UINT konwertuje swój argument na typ zasobu zgodny z funkcjami zarządzania zasobami systemu Windows przy użyciu makra MAKEINTRESOURCE, a wynik jest przechowywany w pojedynczym członu danych klasy, [m_lpstr](#_u_stringorid__m_lpstr).

```
_U_STRINGorID(UINT nID);
_U_STRINGorID(LPCTSTR lpString);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identyfikator zasobu.

*lpString (lpString)*<br/>
Nazwa zasobu.

### <a name="remarks"></a>Uwagi

Argument do konstruktora LPCTSTR jest przechowywany bezpośrednio bez konwersji.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
