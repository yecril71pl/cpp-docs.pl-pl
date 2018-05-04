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
ms.openlocfilehash: f3a8f6cb2ead8798b86d65a1fa875a42a68cdd77
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
  
 Identyfikator zasobu okna dialogowego zasobu szablon.  
  
 *t_bCenter*  
 **Wartość TRUE,** Jeśli obiektu okna dialogowego, które ma być wyśrodkowany w oknie właściciela; w przeciwnym razie **FALSE**.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleDialog::DoModal](#domodal)|Tworzy modalne okno dialogowe.|  
  
## <a name="remarks"></a>Uwagi  
 Implementuje modalne okno dialogowe z podstawowymi funkcjami. `CSimpleDialog` Formanty standardowe systemu Windows tylko zapewnia obsługę. Można tworzyć i wyświetlać modalne okno dialogowe, należy utworzyć wystąpienie tej klasy, podając nazwę istniejącego szablonu zasobów dla okna dialogowego. Obiekt okno dialogowe zostanie zamknięte po kliknięciu dowolnej kontrolki z wstępnie zdefiniowanych wartości (na przykład IDOK lub IDCANCEL).  
  
 `CSimpleDialog` Umożliwia tworzenie tylko modalnych okien dialogowych. `CSimpleDialog` zawiera procedury okno dialogowe używa domyślnej mapy wiadomości do kierowania wiadomości na odpowiednie programy obsługi.  
  
 Zobacz [implementacja okno dialogowe](../../atl/implementing-a-dialog-box.md) Aby uzyskać więcej informacji.  
  
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
 `hWndParent`  
 Dojście do nadrzędnego okna dialogowego. Jeśli zostanie podana żadna wartość, element nadrzędny ma ustawioną bieżące aktywne okno.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwracana wartość jest identyfikator zasobu formantu, który zostaje zamknięte okno dialogowe.  
  
 Jeśli funkcja nie powiedzie się, wartość zwracana jest wartość -1. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać `GetLastError`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda obsługuje wszystkie interakcji z użytkownikiem, gdy okno dialogowe jest aktywne. Jest to, co sprawia, że okno dialogowe modalne; oznacza to, że użytkownik nie mogą oddziaływać na inne okna do czasu zamknięcia okna dialogowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
