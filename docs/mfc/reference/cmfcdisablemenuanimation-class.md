---
title: Klasa CMFCDisableMenuAnimation
ms.date: 11/04/2016
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
ms.openlocfilehash: 97a93e000b3e12d8ec4824100059581216b1b8d9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840768"
---
# <a name="cmfcdisablemenuanimation-class"></a>Klasa CMFCDisableMenuAnimation

Wyłącza animację menu podręcznego.

## <a name="syntax"></a>Składnia

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|-|-|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Konstruuje `CMFCDisableMenuAnimation` obiekt.|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|-|-|
|[CMFCDisableMenuAnimation:: Restore](#restore)|Przywraca poprzednią animację, która jest używana do wyświetlania menu podręcznego.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|-|-|
|`CMFCDisableMenuAnimation::m_animType`|Zapisuje poprzedni typ animacji menu podręcznego.|

### <a name="remarks"></a>Uwagi

Użyj tej klasy pomocnika, aby tymczasowo wyłączyć animację menu podręcznego (na przykład podczas przetwarzania poleceń myszy lub klawiatury).

`CMFCDisableMenuAnimation`Obiekt wyłącza animację menu podręcznego w trakcie jego okresu istnienia. Konstruktor przechowuje bieżący typ animacji menu podręcznego w `m_animType` polu i ustawia bieżący typ animacji na `CMFCPopupMenu::NO_ANIMATION` . Destruktor Przywraca poprzedni typ animacji.

Można utworzyć `CMFCDisableMenuAnimation` obiekt na stosie, aby wyłączyć animację menu podręcznego w ramach jednej funkcji. Jeśli chcesz wyłączyć animację menu podręcznego między funkcjami, Utwórz `CMFCDisableMenuAnimation` obiekt na stercie, a następnie usuń go, gdy chcesz przywrócić animację menu podręcznego.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać stosu do tymczasowego wyłączania animacji menu.

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpopupmenu. h

## <a name="cmfcdisablemenuanimationrestore"></a><a name="restore"></a> CMFCDisableMenuAnimation:: Restore

Przywraca poprzednią animację, która jest używana do wyświetlania menu podręcznego.

```cpp
void Restore ();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez `CMFCDisableMenuAnimation` destruktor, aby przywrócić poprzednią animację, która jest używana przez strukturę do wyświetlania menu wyskakującego.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)
