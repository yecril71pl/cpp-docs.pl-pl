---
title: Klasa CSimpleDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleDialog
- ATLWIN/ATL::CSimpleDialog
- ATLWIN/ATL::CSimpleDialog::DoModal
dev_langs:
- C++
helpviewer_keywords:
- CSimpleDialog class
- CSimpleDialog class, modal dialog boxes in ATL
- dialog boxes, modal
- modal dialog boxes, ATL
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0c713781ff6c780e63fdf19545f83bf693a081b
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881662"
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
  
 Identyfikator zasobu zasobu szablonu okna dialogowego.  
  
 *t_bCenter*  
 Wartość TRUE, jeśli ma być oparte na okno właściciela; obiektu okna dialogowego w przeciwnym razie wartość FALSE.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleDialog::DoModal](#domodal)|Tworzy modalne okno dialogowe.|  
  
## <a name="remarks"></a>Uwagi  
 Implementuje okno modalne okno dialogowe z podstawowymi funkcjami. `CSimpleDialog` zapewnia obsługę Windows tylko formanty standardowe. Aby utworzyć i wyświetlić okno modalne okno dialogowe, należy utworzyć wystąpienie tej klasy, podając nazwę istniejącego szablonu zasobu okna dialogowego. Obiekt okno dialogowe zostanie zamknięte po kliknięciu dowolnego formantu za pomocą wstępnie zdefiniowanych wartości (na przykład IDOK lub IDCANCEL).  
  
 `CSimpleDialog` Umożliwia tworzenie tylko modalnych okien dialogowych. `CSimpleDialog` zawiera procedury okno dialogowe używa domyślnego mapy komunikatów do przekierowywania komunikatów do odpowiedniej procedury obsługi.  
  
 Zobacz [Implementowanie okna dialogowego](../../atl/implementing-a-dialog-box.md) Aby uzyskać więcej informacji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CDialogImplBase`  
  
 `CSimpleDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="domodal"></a>  CSimpleDialog::DoModal  
 Wywołuje modalne okno dialogowe i zwraca wynik okno dialogowe po zakończeniu.  
  
```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```  
  
### <a name="parameters"></a>Parametry  
 *hWndParent*  
 Dojście do nadrzędnego okna dialogowego. Jeśli wartość nie zostanie podany, element nadrzędny jest równa bieżące aktywne okno.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, wartość zwracana jest identyfikator zasobu formant, który odrzucić okno dialogowe.  
  
 Jeśli funkcja zawiedzie, wartość zwracana jest wartość -1. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać `GetLastError`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda obsługuje wszystkich interakcji z użytkownikiem, gdy okno dialogowe jest aktywne. Jest to, co sprawia, że okno dialogowe modalne; oznacza to użytkownik nie może korzystać z innymi oknami, do czasu zamknięcia okna dialogowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
