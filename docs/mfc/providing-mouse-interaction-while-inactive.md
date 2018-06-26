---
title: Zapewnianie interakcji z myszą przy braku aktywności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], mouse interaction
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c322493a0ee1aebd068ffe1fedb695445b6274aa
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929497"
---
# <a name="providing-mouse-interaction-while-inactive"></a>Zapewnianie interakcji z myszą przy braku aktywności
Jeśli nie włączono natychmiast formantu, nadal możesz go do procesu WM_SETCURSOR i WM_MOUSEMOVE wiadomości, mimo że formant nie ma żadnego okna własnych. Można to zrobić przez włączenie `COleControl`w implementacji `IPointerInactive` interfejs, który jest domyślnie wyłączona. (Zobacz *ActiveX SDK* opis tego interfejsu.) Aby go włączyć, zawierać flagi pointerInactive w zestawie flagi zwrócony przez [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags):  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_3.cpp)]  
  
 Kod, aby dołączyć ta flaga jest automatycznie generowany w przypadku wybrania **myszy wskaźnik powiadomienia po nieaktywne** opcja [ustawienia kontroli](../mfc/reference/control-settings-mfc-activex-control-wizard.md) strony podczas tworzenia formantu przy użyciu **Kreator formantów MFC ActiveX**.  
  
 Gdy `IPointerInactive` interfejsu jest włączona, kontener deleguje WM_SETCURSOR i WM_MOUSEMOVE wiadomości do niej. `COleControl`w implementacji `IPointerInactive` alokuje wiadomości formantu mapy komunikatów po dostosowanie myszy koordynuje odpowiednio. Może przetwarzać komunikatów, podobnie jak komunikaty okna zwykłej, dodając odpowiednie pozycje do mapy komunikatów. W programy obsługi dla tych wiadomości unikać *m_hWnd* zmiennej członkowskiej (lub dowolnej funkcji członkowskiej, która korzysta z niego) bez wcześniejszego sprawdzenia, że jego wartość nie jest **NULL**.  
  
 Można również nieaktywne formantu jako obiekt docelowy operacji przeciągania i upuszczania OLE. Wymaga to aktywowanie formantu w tej chwili użytkownik przeciąga obiektu nad nim, tak aby formantu okna może być zarejestrowany jako miejsca docelowego. Powoduje aktywacji podczas przeciągania, Zastąp [COleControl::GetActivationPolicy](../mfc/reference/colecontrol-class.md#getactivationpolicy)i zwraca flagę POINTERINACTIVE_ACTIVATEONDRAG:  
  
 [!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_4.cpp)]  
  
 Włączanie `IPointerInactive` interfejsu zazwyczaj oznacza to, że chcesz formantu ma być może przetwarzać komunikatów myszy przez cały czas. Aby uzyskać takie zachowanie w kontenerze, który nie obsługuje `IPointerInactive` interfejsu, musisz mieć formant zawsze aktywowany, gdy jest widoczne, co oznacza, że formant powinien zawierać flagi OLEMISC_ACTIVATEWHENVISIBLE między dodatkowych flag. Aby zapobiec tej flagi z dają efektu w kontenerze, który obsługuje jednak `IPointerInactive`, można również określić flagę OLEMISC_IGNOREACTIVATEWHENVISIBLE:  
  
 [!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_5.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC: optymalizacja](../mfc/mfc-activex-controls-optimization.md)

