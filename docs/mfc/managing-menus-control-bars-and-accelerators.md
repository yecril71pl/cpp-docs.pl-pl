---
title: Zarządzanie menu, paskami sterowania i akceleratorami
ms.date: 11/04/2016
helpviewer_keywords:
- MDI [MFC], frame windows
- control bars [MFC], updating in frame windows
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- accelerator tables [MFC]
- sharing menus [MFC]
- updating user-interface objects [MFC]
- frame windows [MFC], updating
- status bars [MFC], updating
ms.assetid: 97ca1997-06df-4373-b023-4f7ecd81047b
ms.openlocfilehash: 9945dc68ffd46bbf5e114a79467299e4b67e3659
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621328"
---
# <a name="managing-menus-control-bars-and-accelerators"></a>Zarządzanie menu, paskami sterowania i akceleratorami

Okno ramy zarządza aktualizacjami obiektów interfejsu użytkownika, w tym menu, przyciski paska narzędzi, pasek stanu i akceleratory. Zarządza również udostępnianiem paska menu w aplikacjach MDI.

## <a name="managing-menus"></a>Zarządzanie menu

Okno ramek uczestniczy w aktualizowaniu elementów interfejsu użytkownika przy użyciu mechanizmu ON_UPDATE_COMMAND_UI opisanego w artykule [jak zaktualizować obiekty interfejsu użytkownika](how-to-update-user-interface-objects.md). Przyciski na paskach narzędzi i innych paskach sterowania są aktualizowane w pętli bezczynności. Elementy menu w menu rozwijanych na pasku menu są aktualizowane tuż przed zmniejszeniem menu.

W przypadku aplikacji MDI okno ramka MDI zarządza paskiem menu i podpisem. Okno ramek MDI jest właścicielem jednego menu domyślnego, które jest używane jako pasek menu, gdy nie ma aktywnych okien podrzędnych MDI. Gdy istnieją aktywne elementy podrzędne, pasek menu okna ramki MDI jest przejęty przez menu aktywnego okna elementu podrzędnego MDI. Jeśli aplikacja MDI obsługuje wiele typów dokumentów, takich jak dokumenty wykresu i arkusza, każdy typ umieszcza własne menu na pasku menu i zmienia podpis głównego okna ramki.

[CMDIFrameWnd](reference/cmdiframewnd-class.md) udostępnia domyślne implementacje standardowych poleceń w menu okno, które pojawia się dla aplikacji MDI. W szczególności polecenie New window (ID_WINDOW_NEW) jest implementowane w celu utworzenia nowego okna ramki i wyświetlenia w bieżącym dokumencie. Te implementacje należy przesłonić tylko wtedy, gdy potrzebne jest zaawansowane dostosowywanie.

Wiele okien podrzędnych MDI tego samego typu dokumentu zasobów menu udostępniania. Jeśli w tym samym szablonie dokumentu utworzono kilka okien podrzędnych MDI, mogą one korzystać z tego samego zasobu menu, co oszczędza zasoby systemowe w systemie Windows.

## <a name="managing-the-status-bar"></a>Zarządzanie paskiem stanu

Okno ramki umieszcza również pasek stanu w obszarze klienta i zarządza wskaźnikami paska stanu. Okno ramka czyści i aktualizuje obszar wiadomości na pasku stanu w miarę potrzeby i wyświetla ciągi monitów, ponieważ użytkownik wybiera elementy menu lub przyciski paska narzędzi, zgodnie z opisem w temacie [jak wyświetlić informacje o poleceniu na pasku stanu](how-to-display-command-information-in-the-status-bar.md).

## <a name="managing-accelerators"></a>Zarządzanie akceleratorami

Każde okno ramki utrzymuje opcjonalną tabelę akceleratorów, która automatycznie wykonuje translację klawiszy skrótu. Ten mechanizm ułatwia definiowanie klawiszy akceleratora (nazywanych również skrótami klawiaturowymi), które wywołują polecenia menu.

## <a name="see-also"></a>Zobacz też

[Używanie okien ramowych](using-frame-windows.md)
