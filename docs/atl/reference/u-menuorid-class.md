---
title: Klasa _U_MENUorID
ms.date: 11/04/2016
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
ms.openlocfilehash: 419c9e79178db12efe278838ec8630e04ac3c461
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325838"
---
# <a name="_u_menuorid-class"></a>Klasa _U_MENUorID

Ta klasa zawiera `CreateWindow` otoki dla i `CreateWindowEx`.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class _U_MENUorID
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|Konstruktor.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|Uchwyt do menu.|

## <a name="remarks"></a>Uwagi

Ta klasa karty argumentu umożliwia identyfikatory (UINTs) lub dojścia menu (HMENUs) mają być przekazywane do funkcji bez konieczności jawnego rzutowania ze strony wywołującego.

Ta klasa jest przeznaczona do implementowania otoki do interfejsu API systemu Windows, w szczególności [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) i [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) funkcje, z których oba akceptują argument HMENU, który może być identyfikator okna podrzędnego (UINT), a nie dojście do menu. Na przykład ta klasa jest używana jako parametr [CWindowImpl::Create](cwindowimpl-class.md#create).

Klasa definiuje dwa przeciążenia konstruktora: jeden akceptuje argument UINT, a drugi akceptuje argument HMENU. Argument UINT jest po prostu rzutowany na HMENU w konstruktorze i wynik przechowywany w pojedynczym weszłomie danych klasy, [m_hMenu](#_u_menuorid__m_hmenu). Argument do konstruktora HMENU jest przechowywany bezpośrednio bez konwersji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="_u_menuoridm_hmenu"></a><a name="_u_menuorid__m_hmenu"></a>_U_MENUorID::m_hMenu

Klasa przechowuje wartość przekazywana do jednego z jego konstruktorów jako publiczny element członkowski danych HMENU.

```
HMENU m_hMenu;
```

## <a name="_u_menuorid_u_menuorid"></a><a name="_u_menuorid___u_menuorid"></a>_U_MENUorID::_U_MENUorID

Argument UINT jest po prostu rzutowany na HMENU w konstruktorze i wynik przechowywany w pojedynczym weszłomie danych klasy, [m_hMenu](#_u_menuorid__m_hmenu).

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identyfikator okna podrzędnego.

*Hmenu*<br/>
Uchwyt menu.

### <a name="remarks"></a>Uwagi

Argument do konstruktora HMENU jest przechowywany bezpośrednio bez konwersji.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
