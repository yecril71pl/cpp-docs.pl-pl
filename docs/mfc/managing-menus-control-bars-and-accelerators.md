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
ms.openlocfilehash: 9a089829658265cd835a8c7344aa5bc45fbc109a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226173"
---
# <a name="managing-menus-control-bars-and-accelerators"></a>Zarządzanie menu, paskami sterowania i akceleratorami

Okno ramowe zarządza aktualizowanie obiektów interfejsu użytkownika, w tym menu, przyciski paska narzędzi, pasek stanu i akceleratorów. Umożliwia także zarządzanie, udostępnianie na pasku menu w aplikacji MDI.

## <a name="managing-menus"></a>Zarządzanie menu

Okno ramowe uczestniczy w aktualizowania elementów interfejsu użytkownika przy użyciu mechanizmu ON_UPDATE_COMMAND_UI opisanego w [jak obiektów interfejsu użytkownika aktualizacji](../mfc/how-to-update-user-interface-objects.md). Przyciski na paskach narzędzi i innych pasków sterowania są aktualizowane podczas wykonywania pętli bezczynności. Elementy menu w menu rozwijane na pasku menu są aktualizowane, tuż przed, w menu zostanie rozwinięte.

Dla aplikacji MDI okna ramki MDI zarządza pasek menu i podpis. Okno ramki MDI jest właścicielem co domyślne menu używany jako pasek menu, gdy nie ma żadnych aktywnych okien podrzędnych MDI. W przypadku aktywnych elementów podrzędnych pasek menu okna ramki MDI zostanie przejęty przez menu dla aktywnego okna podrzędnego MDI. Gdy aplikacja MDI obsługuje wiele typów dokumentów, takich jak dokumenty wykresu i arkusza każdego typu umieszcza swój własny menu z paska menu i zmieni podpis ramką głównego okna.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) zawiera domyślne implementacje dla standardowych poleceń w menu Okno, który pojawia się dla aplikacji MDI. W szczególności polecenie nowe okno (id_window_new —) zaimplementowany, aby utworzyć nowe okno ramek i widok do bieżącego dokumentu. Należy zastąpić tych implementacji tylko wtedy, gdy potrzebujesz Dostosowywanie zaawansowane.

Wiele okien podrzędnych MDI typu dokumentu udostępnianie zasobów menu. Jeśli kilka okien podrzędnych MDI są tworzone przez tego samego szablonu dokumentu, można wszystkie używają tego samego zasobu menu Zapisywanie zasobów systemu Windows.

## <a name="managing-the-status-bar"></a>Zarządzanie na pasku stanu

Okno ramowe również umieszcza na pasku stanu w obrębie obszaru klienckiego i zarządza nimi stan paska wskaźników. Okno ramowe Czyści i aktualizuje obszarze wiadomości w pasku stanu, zgodnie z potrzebami i wyświetla monit ciągi zgodnie z wybraniu przez użytkownika w menu i przycisków paska narzędzi, zgodnie z opisem w [jak wyświetlanie informacji polecenia na pasku stanu](../mfc/how-to-display-command-information-in-the-status-bar.md).

## <a name="managing-accelerators"></a>Zarządzanie akceleratorów

Każde okno ramki zachowuje tabeli akceleratora opcjonalne, za pomocą klawiatury tłumaczenia accelerator dla Ciebie automatycznie. Ten mechanizm można łatwo zdefiniować klawisze skrótów (nazywane również klawiszy skrótów), które wywołują polecenia menu.

## <a name="see-also"></a>Zobacz także

[Używanie okien ramowych](../mfc/using-frame-windows.md)
