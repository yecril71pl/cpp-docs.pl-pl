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
ms.openlocfilehash: 990f41d2dfa6491d246797322ee275c9648d52a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367568"
---
# <a name="cmfcdisablemenuanimation-class"></a>Klasa CMFCDisableMenuAnimation

Wyłącza animację menu podręcznego.

## <a name="syntax"></a>Składnia

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Konstruuje `CMFCDisableMenuAnimation` obiekt.|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCDisableMenuAnimation::Przywróć](#restore)|Przywraca poprzednią animację, która jest używana przez strukturę do wyświetlania menu podręcznego.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|Nazwa|Opis|
|`CMFCDisableMenuAnimation::m_animType`|Przechowuje poprzedni typ animacji menu podręcznego.|

### <a name="remarks"></a>Uwagi

Ta klasa pomocnika służy do tymczasowego wyłączania animacji menu podręcznego (na przykład podczas przetwarzania poleceń myszy lub klawiatury).

Obiekt `CMFCDisableMenuAnimation` wyłącza animację menu podręcznego w okresie jego istnienia. Konstruktor przechowuje bieżący typ animacji `m_animType` menu podręcznego w `CMFCPopupMenu::NO_ANIMATION`polu i ustawia bieżący typ animacji na . Destruktor przywraca poprzedni typ animacji.

Można utworzyć `CMFCDisableMenuAnimation` obiekt na stosie, aby wyłączyć animację menu podręcznego w jednej funkcji. Jeśli chcesz wyłączyć animację menu podręcznego `CMFCDisableMenuAnimation` między funkcjami, utwórz obiekt na stercie, a następnie usuń go, gdy chcesz przywrócić animację menu podręcznego.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak za pomocą stosu tymczasowo wyłączyć animację menu.

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpopupmenu.h

## <a name="cmfcdisablemenuanimationrestore"></a><a name="restore"></a>CMFCDisableMenuAnimation::Przywróć

Przywraca poprzednią animację, która jest używana przez strukturę do wyświetlania menu podręcznego.

```
void Restore ();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest `CMFCDisableMenuAnimation` wywoływana przez destruktora, aby przywrócić poprzednią animację, która jest używana do wyświetlania menu podręcznego.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)
