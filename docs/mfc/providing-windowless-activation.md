---
title: "Zapewnianie aktywacji niepowiązanej z oknami | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- windowless activation of MFC ActiveX controls
- activation [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], activate options
- activation [MFC], windowless
ms.assetid: 094903b5-c344-42fa-96ff-ce01e16891c5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eb33f1dd9f8be8cb06cdfcc2aeecb653c2762410
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="providing-windowless-activation"></a>Zapewnianie aktywacji niepowiązanej z oknami
Kod tworzenia okna (czyli wszystko, co się stanie w przypadku wywołania **właściwości CreateWindow**) jest kosztowne do wykonania. Formant, który obsługuje ekranowa okno ma zarządzać wiadomości dla okna. Formanty bez okien w związku z tym są szybsze niż formantów z systemem windows.  
  
 Kolejną zaletą kontrolek bez okien jest, że w przeciwieństwie do formantów okna kontrolek bez okien obsługi malowanie przezroczyste i regiony ekranu nieprostokątny. Typowym przykładem przezroczystego formantu jest tekst formantu o przezroczyste tło. Formanty do malowania tekstu, ale nie w tle, niezależnie od jest pod tekstem widoczny. Formularze nowszej często wprowadzane Użyj nieprostokątny formantów, takich jak strzałki i zaokrąglona przycisków.  
  
 Często formant nie jest konieczne okna własnych i, zamiast niego, można użyć usług okna swojego kontenera, pod warunkiem, że kontener został zapisany do obsługi obiektów bez okien. Formanty bez okien są zgodne z kontenerów starszej. W starszych kontenery nie są zapisywane do kontrolek bez okien obsługi kontrolek bez okien Utwórz okna, gdy aktywne.  
  
 Ponieważ formanty bez okien nie mają własnych systemu windows, kontenera (która ma okna) jest odpowiedzialny za świadczenia usług, czy zostały dostarczone przez okna dla formantu. Na przykład jeśli formant musi zapytania fokus klawiatury, przechwytywanie myszy lub uzyskać kontekstu urządzenia, te operacje są zarządzane przez kontener. Kontener kieruje komunikaty wejściowe użytkownika wysyłane do okna odpowiednie formantem bez okien, przy użyciu `IOleInPlaceObjectWindowless` interfejsu. (Zobacz *ActiveX SDK* opis tego interfejsu.) `COleControl` tych usług w kontenerze wywołania funkcji elementów członkowskich.  
  
 Aby użyć aktywacji niepowiązanej z oknami formantu, obejmują **windowlessActivate** flagi w zestawie flagi zwrócony przez [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Na przykład:  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-windowless-activation_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#6](../mfc/codesnippet/cpp/providing-windowless-activation_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-windowless-activation_3.cpp)]  
  
 Kod, aby dołączyć ta flaga jest automatycznie generowany w przypadku wybrania **aktywacji niepowiązanej z oknami** opcja [ustawienia kontroli](../mfc/reference/control-settings-mfc-activex-control-wizard.md) strony Kreator formantów MFC ActiveX.  
  
 Po włączeniu aktywacji niepowiązanej z oknami kontenera będzie delegowane komunikaty wejściowe do formantu `IOleInPlaceObjectWindowless` interfejsu. `COleControl`przez implementację tego interfejsu alokuje wiadomości formantu mapy komunikatów, po dostosowanie myszy koordynuje odpowiednio. Można przetwarzać komunikaty, takie jak komunikaty okna zwykłej, dodając odpowiednie wpisy mapy wiadomości. W programy obsługi dla tych wiadomości unikać `m_hWnd` zmiennej członkowskiej (lub dowolnej funkcji członkowskiej, która korzysta z niego) bez wcześniejszego sprawdzenia, że jego wartość nie jest **NULL**.  
  
 `COleControl`udostępnia funkcje Członkowskie, które wywołują przechwytywanie myszy, klawiatury, przewijanie i innych usług okna z kontenera zgodnie z potrzebami, w tym:  
  
-   [Przy uzyskaniu fokusu](../mfc/reference/colecontrol-class.md#getfocus), [SetFocus](../mfc/reference/colecontrol-class.md#setfocus)  
  
-   [GetCapture](../mfc/reference/colecontrol-class.md#getcapture), [SetCapture](../mfc/reference/colecontrol-class.md#setcapture), [ReleaseCapture](../mfc/reference/colecontrol-class.md#releasecapture)  
  
-   [GetDC](../mfc/reference/colecontrol-class.md#getdc), [ReleaseDC](../mfc/reference/colecontrol-class.md#releasedc)  
  
-   [InvalidateRgn](../mfc/reference/colecontrol-class.md#invalidatergn)  
  
-   [ScrollWindow](../mfc/reference/colecontrol-class.md#scrollwindow)  
  
-   [GetClientRect](../mfc/reference/colecontrol-class.md#getclientrect)  
  
 W formanty bez okien, zawsze należy używać `COleControl` funkcje Członkowskie zamiast odpowiadającego `CWnd` funkcji Członkowskich lub ich powiązanych funkcji Win32 API.  
  
 Może być formantem bez okien jako obiekt docelowy operacji przeciągania i upuszczania OLE. To zwykle wymaga zarejestrowania formantu okna jako miejsca docelowego. Ponieważ kontrolka nie ma żadnego okna własnych, kontener używa osobnym oknie jako miejsca docelowego. Formant, dostarcza implementację tego `IDropTarget` interfejsu, do którego kontenera można delegować wywołań w odpowiednim czasie. Uwidacznianie kontenera w tym interfejsie, Zastąp [COleControl::GetWindowlessDropTarget](../mfc/reference/colecontrol-class.md#getwindowlessdroptarget). Na przykład:  
  
 [!code-cpp[NVC_MFC_AxOpt#8](../mfc/codesnippet/cpp/providing-windowless-activation_4.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC: optymalizacja](../mfc/mfc-activex-controls-optimization.md)

