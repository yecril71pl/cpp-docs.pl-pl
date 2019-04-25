---
title: _U_MENUorID Class
ms.date: 11/04/2016
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
ms.openlocfilehash: d02d00e3c56fc253e8f89eec9815e01d60c6e2aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196987"
---
# <a name="umenuorid-class"></a>_U_MENUorID Class

Ta klasa udostępnia otokę dla `CreateWindow` i `CreateWindowEx`.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|Dojście do menu.|

## <a name="remarks"></a>Uwagi

Ta klasa adaptera argument umożliwia identyfikatorów (UINTs) lub menu dojścia (HMENUs), który zostanie przekazany do funkcji bez konieczności jawnego rzutowania przez obiekt wywołujący.

Ta klasa jest przeznaczona dla implementacji otoki do interfejsu API Windows, szczególnie [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) i [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) funkcje, które akceptują argument HMENU, które mogą być okna podrzędnego Identyfikator (UINT) zamiast uchwyt menu. Na przykład zostanie wyświetlony jako parametr do tej klasy w użyciu [CWindowImpl::Create](cwindowimpl-class.md#create).

Klasa definiuje dwa przeciążenia konstruktora: przyjmuje jeden UINT argument, a druga akceptuje HMENU argument. UINT argument tylko jest rzutowany na HMENU konstruktora i wyników, przechowywane w składowej danych jednego klasy, [m_hMenu](#_u_menuorid__m_hmenu). Argument Pro Konstruktor HMENU są przechowywane bezpośrednio, bez konwersji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="_u_menuorid__m_hmenu"></a>  _U_MENUorID::m_hMenu

Klasa przechowuje wartość przekazana do jednej z jego konstruktorów jako publicznej składowej danych HMENU.

```
HMENU m_hMenu;
```

##  <a name="_u_menuorid___u_menuorid"></a>  _U_MENUorID::_U_MENUorID

UINT argument tylko jest rzutowany na HMENU konstruktora i wyników, przechowywane w składowej danych jednego klasy, [m_hMenu](#_u_menuorid__m_hmenu).

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator okna podrzędnego.

*hMenu*<br/>
Uchwyt menu.

### <a name="remarks"></a>Uwagi

Argument Pro Konstruktor HMENU są przechowywane bezpośrednio, bez konwersji.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
