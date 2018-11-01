---
title: Zapewnianie aktywacji niepowiązanej z oknami
ms.date: 11/04/2016
helpviewer_keywords:
- windowless activation of MFC ActiveX controls
- activation [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], activate options
- activation [MFC], windowless
ms.assetid: 094903b5-c344-42fa-96ff-ce01e16891c5
ms.openlocfilehash: 1e962584faa826ce87533806edc2bed1d1248286
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475637"
---
# <a name="providing-windowless-activation"></a>Zapewnianie aktywacji niepowiązanej z oknami

Kod tworzenia okna (czyli wszystko, co się dzieje, gdy wywołujesz `CreateWindow`) jest kosztowne do wykonania. Formant, który przechowuje na ekranie okna musi zarządzać wiadomości dla okna. Od kontrolek bez okien są zatem szybciej niż formanty z systemem windows.

Kolejną zaletą kontrolek bez okien to, że w przeciwieństwie do formantów okna od kontrolek bez okien obsługi malowanie przezroczyste i regiony ekranu prostokątny. Typowym przykładem przezroczyste kontroli jest kontrolki tekstu z przezroczystym tłem. Formanty do malowania tekst, ale nie w tle, więc niezależnie od rodzaju znajduje się w tekście pojawia się za pośrednictwem. Nowsze formy, że często użytkowania nieprostokątne formanty, takie jak strzałki i zaokrąglanie przycisków.

Często formant nie wymaga własnego okna i, zamiast tego mogą korzystać z usług okna swojego kontenera, pod warunkiem, że kontener został zapisany do obsługi obiektów bez okien. Od kontrolek bez okien są zgodne z poprzednimi wersjami z kontenerami starszych. W starszych kontenery nie są zapisywane do kontrolek bez okien obsługi kontrolek bez okien Tworzenie okna, gdy jest ona aktywna.

Ponieważ kontrolek bez okien nie mają własne systemu windows, kontener, (która ma okno) jest odpowiedzialne za świadczenie usług, które mogłyby zostały podane przez okno własne kontrolki. Na przykład jeśli formant musi zapytania fokus klawiatury, przechwytywanie myszy lub uzyskać kontekst urządzenia, te operacje są zarządzane przez kontener. Kontener kieruje komunikaty wejściowe użytkownika wysyłane do okna do odpowiedniej kontroli niepowiązanej z oknami, za pomocą `IOleInPlaceObjectWindowless` interfejsu. (Zobacz *ActiveX SDK* opis tego interfejsu.) `COleControl` elementu członkowskiego wywołają procedurę obsługi tych usług, z kontenera.

Aby użyć aktywacji niepowiązanej z oknami kontrolki, obejmują **windowlessActivate** flagi w zestawie flagi zwrócony przez [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Na przykład:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-windowless-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#6](../mfc/codesnippet/cpp/providing-windowless-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-windowless-activation_3.cpp)]

Kod, aby dołączyć tę flagę, jest generowany automatycznie po wybraniu **aktywacji niepowiązanej z oknami** opcja [ustawienia kontroli](../mfc/reference/control-settings-mfc-activex-control-wizard.md) strony kreatora kontrolek ActiveX MFC.

Po włączeniu aktywacji niepowiązanej z oknami kontenera oddeleguje komunikaty wejściowe z formantem `IOleInPlaceObjectWindowless` interfejsu. `COleControl`przez implementację tego interfejsu alokuje wiadomości formantu mapy komunikatów, po dostosowanie myszy służy do koordynowania odpowiednio. Może przetwarzać komunikaty, takie jak komunikaty zwykłych okna, dodając odpowiednie wpisy mapy komunikatów. W procedurach obsługi dla tych komunikatów należy unikać *m_hWnd* zmienną członkowską (lub dowolnej funkcji elementu członkowskiego, która korzysta z niego) bez wcześniejszego sprawdzenia, że jego wartość nie jest **NULL**.

`COleControl` dostarcza funkcji elementów członkowskich, które wywołują przechwytywanie myszy fokus klawiatury, przewijania i innymi usługami okna z kontenera, zgodnie z potrzebami, w tym:

- [Przy uzyskaniu fokusu](../mfc/reference/colecontrol-class.md#getfocus), [SetFocus](../mfc/reference/colecontrol-class.md#setfocus)

- [GetCapture](../mfc/reference/colecontrol-class.md#getcapture), [SetCapture](../mfc/reference/colecontrol-class.md#setcapture), [ReleaseCapture](../mfc/reference/colecontrol-class.md#releasecapture)

- [Getdc —](../mfc/reference/colecontrol-class.md#getdc), [ReleaseDC](../mfc/reference/colecontrol-class.md#releasedc)

- [InvalidateRgn](../mfc/reference/colecontrol-class.md#invalidatergn)

- [ScrollWindow](../mfc/reference/colecontrol-class.md#scrollwindow)

- [GetClientRect](../mfc/reference/colecontrol-class.md#getclientrect)

W kontrolkach niepowiązanej z oknami, należy zawsze używać `COleControl` zamiast odpowiednich elementów członkowskich `CWnd` funkcji składowych lub ich pokrewnych funkcji Win32 API.

Możesz chcieć kontrolce jako obiekt docelowy operacji przeciągania i upuszczania OLE. Zwykle wymagałoby to, że okno Kontrola zostać zarejestrowana jako miejsca docelowego. Ponieważ kontrolka nie ma żadnych własnego okna, kontener używa osobnym oknie jako miejsca docelowego. Kontrolka zawiera implementację `IDropTarget` interfejsu, do którego kontener mogą delegować uprawnienia do wywołania w odpowiednim czasie. Aby udostępnić ten interfejs do kontenera, należy zastąpić [COleControl::GetWindowlessDropTarget](../mfc/reference/colecontrol-class.md#getwindowlessdroptarget). Na przykład:

[!code-cpp[NVC_MFC_AxOpt#8](../mfc/codesnippet/cpp/providing-windowless-activation_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC: optymalizacja](../mfc/mfc-activex-controls-optimization.md)

