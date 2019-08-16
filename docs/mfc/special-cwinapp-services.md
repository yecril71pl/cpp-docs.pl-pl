---
title: Specjalne usługi CWinApp
ms.date: 11/04/2016
f1_keywords:
- LoadStdProfileSettings
- EnableShellOpen
helpviewer_keywords:
- files [MFC], most recently used
- DragAcceptFiles method [MFC]
- MRU lists
- GDI+, initializing for MFC
- GDI+, suppressing background thread [MFC]
- CWinApp class [MFC], shell registration
- application objects [MFC], services
- CWinApp class [MFC], initializing GDI+
- MFC, shell registration
- CWinApp class [MFC], File Manager drag and drop
- LoadStdProfileSettings method [MFC]
- MFC, most-recently-used file list
- RegisterShellFileTypes method [MFC]
- drag and drop [MFC], files
- registering file types
- Shell, registering file types
- services, provided by CWinApp
- CWinApp class [MFC], recently used documents
- CWinApp class [MFC], services
- files [MFC], drag and drop
- EnableShellOpen method [MFC]
- registry [MFC], most recently used files
- MFC, file operations
- registration [MFC], shell
ms.assetid: 0480cd01-f629-4249-b221-93432d95b431
ms.openlocfilehash: e96753a5dbc77fdc7aab365439e997585e00f43b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511332"
---
# <a name="special-cwinapp-services"></a>Specjalne usługi CWinApp

Poza uruchomieniem pętli komunikatów i umożliwieniem zainicjowania aplikacji i jej oczyszczenia, [CWinApp](../mfc/reference/cwinapp-class.md) udostępnia kilka innych usług.

##  <a name="_core_shell_registration"></a>Rejestracja powłoki

Domyślnie Kreator aplikacji MFC umożliwia użytkownikowi otwieranie plików danych utworzonych przez aplikację przez dwukrotne kliknięcie ich w Eksploratorze plików lub w Menedżerze plików. Jeśli aplikacja jest aplikacją MDI i określisz rozszerzenie dla plików tworzonych przez aplikację, Kreator aplikacji MFC dodaje wywołania do funkcji składowych [RegisterShellFileTypes](../mfc/reference/cwinapp-class.md#registershellfiletypes) i [EnableShellOpen](../mfc/reference/cwinapp-class.md#enableshellopen) z [CWinApp](../mfc/reference/cwinapp-class.md) do `InitInstance` zastąpienie, które zapisuje dla Ciebie.

`RegisterShellFileTypes`rejestruje typy dokumentów aplikacji w Eksploratorze plików lub Menedżerze plików. Funkcja dodaje wpisy do bazy danych rejestracji przechowywanej w systemie Windows. Wpisy rejestrują każdy typ dokumentu, skojarz rozszerzenie pliku z typem pliku, określ wiersz polecenia, aby otworzyć aplikację, a następnie określ polecenie dynamicznej wymiany danych (DDE), aby otworzyć dokument tego typu.

`EnableShellOpen`kończy proces, umożliwiając aplikacji otrzymywanie poleceń DDE z Eksploratora plików lub Menedżera plików, aby otworzyć plik wybrany przez użytkownika.

Ta Automatyczna obsługa rejestracji w `CWinApp` programie eliminuje konieczność dostarczania pliku reg do aplikacji lub wykonywania specjalnej instalacji.

Jeśli chcesz zainicjować GDI+ dla aplikacji (przez wywołanie [GdiplusStartup](/windows/win32/api/gdiplusinit/nf-gdiplusinit-gdiplusstartup) w funkcji [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) ), musisz pominąć wątek w tle GDI+.

Można to zrobić, ustawiając `SuppressBackgroundThread` element członkowski struktury [GdiplusStartupInput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupinput) na **wartość true**. W `NotificationHook` przypadku pomijania wątku w tle GDI+, wywołania `NotificationUnhook` i powinny zostać wykonane tuż przed wejściem i wyjściem z pętli komunikatów aplikacji. Aby uzyskać więcej informacji na temat tych wywołań, zobacz [GdiplusStartupOutput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupoutput). W związku z tym, dobrym miejscem `GdiplusStartup` do wywołania i funkcji powiadomień punktu zaczepienia byłaby przesłonięcie funkcji wirtualnej [CWinApp:: Run](../mfc/reference/cwinapp-class.md#run), jak pokazano poniżej:

[!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]

Jeśli nie zostanie pominięty wątek GDI+ w tle, polecenia DDE mogą być przedwcześnie wystawione dla aplikacji przed utworzeniem jej okna głównego. Polecenia DDE, które są emitowane przez powłokę, mogą być przedwcześnie przerywane, co skutkuje komunikatami o błędach.

##  <a name="_core_file_manager_drag_and_drop"></a>Przeciąganie i upuszczanie Menedżera plików

Pliki można przeciągać z okna widok plików w Menedżerze plików lub Eksploratorze plików do okna w aplikacji. Możesz na przykład włączyć przeciąganie co najmniej jednego pliku do głównego okna aplikacji MDI, gdzie aplikacja może pobrać nazwy plików i otworzyć okna podrzędne MDI dla tych plików.

Aby włączyć przeciąganie i upuszczanie plików w aplikacji, Kreator aplikacji MFC zapisuje wywołanie do funkcji [](../mfc/reference/cwnd-class.md) składowej CWnd [element DragAcceptFiles](../mfc/reference/cwnd-class.md#dragacceptfiles) dla głównego `InitInstance`okna ramki w. To wywołanie można usunąć, jeśli nie chcesz zaimplementować funkcji przeciągania i upuszczania.

> [!NOTE]
>  Możesz również zaimplementować bardziej ogólne możliwości przeciągania i upuszczania — przeciągając dane między lub w obrębie dokumentów — za pomocą OLE. Aby uzyskać więcej informacji, zobacz artykuł przeciąganie [i upuszczanie (OLE)](../mfc/drag-and-drop-ole.md).

##  <a name="_core_keeping_track_of_the_most_recently_used_documents"></a>Śledzenie ostatnio używanych dokumentów

Gdy użytkownik otwiera i zamyka pliki, obiekt aplikacji śledzi cztery ostatnio używane pliki. Nazwy tych plików są dodawane do menu plik i aktualizowane wraz z ich zmianą. W strukturze są przechowywane te nazwy plików w rejestrze lub w pliku. ini o takiej samej nazwie jak projekt i odczytywane z pliku podczas uruchamiania aplikacji. Zastąpienie tworzonego przez Kreatora aplikacji MFC obejmuje wywołanie funkcji składowej CWinApp [LoadStdProfileSettings](../mfc/reference/cwinapp-class.md#loadstdprofilesettings), która ładuje informacje z rejestru lub pliku ini, w tym ostatnio używany plik [](../mfc/reference/cwinapp-class.md) `InitInstance` nazwisko.

Te wpisy są przechowywane w następujący sposób:

- W systemie Windows NT, Windows 2000 i nowszych wartość jest przechowywana w kluczu rejestru.

- W systemie Windows 3. x wartość jest przechowywana w WIN. Plik INI.

- W systemie Windows 95 i nowszych wartość jest przechowywana w buforowanej wersji programu WIN. Nośnika.

## <a name="see-also"></a>Zobacz także

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
