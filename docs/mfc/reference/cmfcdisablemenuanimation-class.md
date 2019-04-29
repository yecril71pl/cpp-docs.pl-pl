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
ms.openlocfilehash: bf8c598e9e105569e0a5676267e205b3d3939712
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345607"
---
# <a name="cmfcdisablemenuanimation-class"></a>Klasa CMFCDisableMenuAnimation

Wyłącza menu podręcznego animacji.

## <a name="syntax"></a>Składnia

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Konstruuje `CMFCDisableMenuAnimation` obiektu.|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCDisableMenuAnimation::Restore](#restore)|Przywraca poprzedniej animacji, używany w ramach do wyświetlenia menu podręcznego.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|Nazwa|Opis|
|`CMFCDisableMenuAnimation::m_animType`|Przechowuje poprzedni typ animacji menu podręcznego.|

### <a name="remarks"></a>Uwagi

Aby tymczasowo wyłączyć menu podręcznego animacji (na przykład podczas przetwarzania polecenia za pomocą klawiatury lub myszy), należy użyć tej klasy pomocnika.

Element `CMFCDisableMenuAnimation` obiektu wyłącza menu podręcznego animacji jego okres istnienia. Konstruktor przechowuje bieżącego typu animacji menu podręczne w `m_animType` pola i ustawia typ bieżącego animacji `CMFCPopupMenu::NO_ANIMATION`. Destruktor przywraca poprzedni typ animacji.

Możesz utworzyć `CMFCDisableMenuAnimation` obiektów na stosie, aby wyłączyć menu podręcznego animacji w jednej funkcji. Jeśli chcesz wyłączyć animację menu podręcznego między funkcjami, Utwórz `CMFCDisableMenuAnimation` obiektów na stercie, a następnie usuń ją, gdy chcesz wykonać przywrócenie menu podręcznego animacji.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób korzystania ze stosu, aby tymczasowo wyłączyć menu animacji.

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpopupmenu.h

##  <a name="restore"></a>  CMFCDisableMenuAnimation::Restore

Przywraca poprzedniej animacji, używany w ramach do wyświetlenia menu podręcznego.

```
void Restore ();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana `CMFCDisableMenuAnimation` destruktora, aby przywrócić poprzednią animację, używany w ramach do wyświetlenia menu podręcznego.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)
