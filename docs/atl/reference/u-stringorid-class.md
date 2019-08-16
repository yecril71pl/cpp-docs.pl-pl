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
ms.openlocfilehash: 57363dbe2a1e7166b8da401900c3a7f913e63a9d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495112"
---
# <a name="_u_stringorid-class"></a>Klasa _U_STRINGorID

Ta klasa adaptera argumentu umożliwia przekazywanie nazw zasobów (LPCTSTRs) lub identyfikatorów zasobów (UINTs) do funkcji bez konieczności, aby obiekt wywołujący przekonwertował identyfikator na ciąg za pomocą makra MAKEINTRESOURCE.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

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

Ta klasa jest przeznaczona do implementowania otok do interfejsu API zarządzania zasobami systemu Windows, takich jak funkcje [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcew), [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)i [LoadMenu](/windows/win32/api/winuser/nf-winuser-loadmenuw) , które akceptują argument LPCTSTR, który może być nazwą zasobu lub jego identyfikatorem.

Klasa definiuje dwa przeciążenia konstruktorów: jeden akceptuje argument LPCTSTR, a drugi akceptuje argument UINT. Argument UINT jest konwertowany na typ zasobów zgodny z funkcjami zarządzania zasobami systemu Windows przy użyciu makra MAKEINTRESOURCE i wyniku przechowywanego w jednej składowej danych klasy, [m_lpstr](#_u_stringorid__m_lpstr). Argument konstruktora LPCTSTR jest przechowywany bezpośrednio bez konwersji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

##  <a name="_u_stringorid__m_lpstr"></a>_U_STRINGorID::m_lpstr

Klasa przechowuje wartość przekazaną do jednego z jego konstruktorów jako element członkowski danych LPCTSTR Public.

```
LPCTSTR m_lpstr;
```

##  <a name="_u_stringorid___u_stringorid"></a>  _U_STRINGorID::_U_STRINGorID

Konstruktor UINT konwertuje swój argument na typ zasobu zgodny z funkcjami zarządzania zasobami systemu Windows przy użyciu makra MAKEINTRESOURCE, a wynik jest przechowywany w pojedynczym elemencie członkowskim danych klasy, [m_lpstr](#_u_stringorid__m_lpstr).

```
_U_STRINGorID(UINT nID);
_U_STRINGorID(LPCTSTR lpString);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator zasobu.

*lpString*<br/>
Nazwa zasobu.

### <a name="remarks"></a>Uwagi

Argument konstruktora LPCTSTR jest przechowywany bezpośrednio bez konwersji.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
