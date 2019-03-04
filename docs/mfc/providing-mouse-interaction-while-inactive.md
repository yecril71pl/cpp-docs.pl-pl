---
title: Zapewnianie interakcji z myszą przy braku aktywności
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], mouse interaction
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
ms.openlocfilehash: d37deeec06551ae8bf340c99a9759327ce2ec2b7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287846"
---
# <a name="providing-mouse-interaction-while-inactive"></a>Zapewnianie interakcji z myszą przy braku aktywności

Jeśli formant nie jest od razu aktywowana, nadal można je do procesu WM_SETCURSOR i WM_MOUSEMOVE wiadomości, mimo, że kontrolka nie ma żadnych własnego okna. Można to zrobić przez włączenie `COleControl`przez implementację `IPointerInactive` interfejs, który jest domyślnie wyłączona. (Zobacz *ActiveX SDK* opis tego interfejsu.) Aby ją włączyć, zawierać flagi pointerInactive zestaw flag zwrócony przez [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags):

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_3.cpp)]

Kod, aby dołączyć tę flagę, jest generowany automatycznie po wybraniu **myszy wskaźnik powiadomienia po nieaktywne** opcja [ustawienia kontroli](../mfc/reference/control-settings-mfc-activex-control-wizard.md) stronie podczas tworzenia kontrolki przy użyciu **Kreator kontrolek ActiveX MFC**.

Gdy `IPointerInactive` interfejs jest włączony, kontener deleguje WM_SETCURSOR i WM_MOUSEMOVE wiadomości do niego. `COleControl`w implementacji `IPointerInactive` alokuje wiadomości formantu mapy wiadomości po dostosowanie myszy służy do koordynowania odpowiednio. Pozwala na przetwarzanie komunikatów, tak jak zwykły okna komunikatów, dodając odpowiednie pozycje na mapie komunikatów. W procedurach obsługi dla tych komunikatów należy unikać *m_hWnd* zmienną członkowską (lub dowolnej funkcji elementu członkowskiego, która korzysta z niego) bez wcześniejszego sprawdzenia, że jego wartość nie jest **NULL**.

Można również nieaktywne sterowania jako obiekt docelowy operacji przeciągania i upuszczania OLE. Wymaga aktywowania kontrolki w tym momencie użytkownik przeciąga obiekt nad nim, tak, aby okna formantu może zostać zarejestrowana jako miejsca docelowego. Aby spowodować Aktywacja podczas przeciągania, należy zastąpić [COleControl::GetActivationPolicy](../mfc/reference/colecontrol-class.md#getactivationpolicy)i zwraca flagę POINTERINACTIVE_ACTIVATEONDRAG:

[!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_4.cpp)]

Włączanie `IPointerInactive` interfejsu zazwyczaj oznacza, że ma formant aby mieć możliwość przetwarzania komunikatów myszy przez cały czas. Aby uzyskać takie zachowanie w kontenerze, który nie obsługuje `IPointerInactive` interfejsu, musisz mieć formantu zawsze aktywowany, gdy jest widoczne, co oznacza, że formant powinien zawierać flagi OLEMISC_ACTIVATEWHENVISIBLE wśród różnych flag. Jednak aby uniknąć tej flagi z zastosowaniem w pojemniku, który obsługuje `IPointerInactive`, można również określić flagę OLEMISC_IGNOREACTIVATEWHENVISIBLE:

[!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_5.cpp)]

## <a name="see-also"></a>Zobacz także

[Kontrolki ActiveX MFC: Optymalizacja](../mfc/mfc-activex-controls-optimization.md)
