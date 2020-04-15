---
title: Klasa CSimpleDialog
ms.date: 11/04/2016
f1_keywords:
- CSimpleDialog
- ATLWIN/ATL::CSimpleDialog
- ATLWIN/ATL::CSimpleDialog::DoModal
helpviewer_keywords:
- CSimpleDialog class
- CSimpleDialog class, modal dialog boxes in ATL
- dialog boxes, modal
- modal dialog boxes, ATL
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
ms.openlocfilehash: 345372d71ad96a74bb0ae6dd7e89bdf0724cd822
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330830"
---
# <a name="csimpledialog-class"></a>Klasa CSimpleDialog

Ta klasa implementuje podstawowe modalne okno dialogowe.

## <a name="syntax"></a>Składnia

```
template <WORD t_wDlgTemplateID, BOOL t_bCenter = TRUE>
class CSimpleDialog : public CDialogImplBase
```

#### <a name="parameters"></a>Parametry

*t_wDlgTemplateID*

Identyfikator zasobu zasób szablonu okna dialogowego.

*t_bCenter*<br/>
PRAWDA, jeśli obiekt okna dialogowego ma być wyśrodkowany w oknie właściciela; w przeciwnym razie FALSE.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleDialog::DoModal](#domodal)|Tworzy modalne okno dialogowe.|

## <a name="remarks"></a>Uwagi

Implementuje modalne okno dialogowe z podstawową funkcjonalnością. `CSimpleDialog`zapewnia obsługę tylko typowych formantów systemu Windows. Aby utworzyć i wyświetlić modalne okno dialogowe, utwórz wystąpienie tej klasy, podając nazwę istniejącego szablonu zasobu dla okna dialogowego. Obiekt okna dialogowego zostanie zamknięty, gdy użytkownik kliknie dowolny formant o wstępnie zdefiniowanej wartości (np.

`CSimpleDialog`umożliwia tworzenie tylko modalnych okien dialogowych. `CSimpleDialog`zawiera procedurę okna dialogowego, która używa domyślnej mapy wiadomości do kierowania wiadomości do odpowiednich programów obsługi.

Aby uzyskać więcej informacji, zobacz [Implementowanie okna dialogowego.](../../atl/implementing-a-dialog-box.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CDialogImplBase`

`CSimpleDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="csimpledialogdomodal"></a><a name="domodal"></a>CSimpleDialog::DoModal

Wywołuje modalne okno dialogowe i zwraca wynik okna dialogowego po zakończeniu.

```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parametry

*hWndRodziciek*<br/>
Uchwyt do nadrzędnego okna dialogowego. Jeśli nie podano żadnej wartości, element nadrzędny jest ustawiony na bieżące aktywne okno.

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwracana wartość jest identyfikatorem zasobu formantu, który odrzucił okno dialogowe.

Jeśli funkcja nie powiedzie się, zwracana wartość wynosi -1. Aby uzyskać rozszerzone informacje `GetLastError`o błędzie, zadzwoń do pliku .

### <a name="remarks"></a>Uwagi

Ta metoda obsługuje całą interakcję z użytkownikiem, gdy okno dialogowe jest aktywne. To, co sprawia, że modalne okno dialogowe; oznacza to, że użytkownik nie może wchodzić w interakcje z innymi oknami, dopóki okno dialogowe nie zostanie zamknięte.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
