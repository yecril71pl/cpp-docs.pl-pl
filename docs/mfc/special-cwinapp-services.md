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
ms.openlocfilehash: 1f5abcdab3eda1304879b122acc8072951a0e6c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363903"
---
# <a name="special-cwinapp-services"></a>Specjalne usługi CWinApp

Oprócz uruchomienia pętli komunikatów i daje możliwość zainicjowania aplikacji i oczyścić po niej, [CWinApp](../mfc/reference/cwinapp-class.md) zapewnia kilka innych usług.

## <a name="shell-registration"></a><a name="_core_shell_registration"></a>Rejestracja powłoki

Domyślnie Kreator aplikacji MFC umożliwia użytkownikowi otwieranie plików danych utworzonych przez aplikację przez dwukrotne kliknięcie ich w Eksploratorze plików lub Menedżerze plików. Jeśli aplikacja jest aplikacją MDI i określisz rozszerzenie dla plików, które tworzy aplikacja, Kreator aplikacji MFC dodaje wywołania funkcji elementów członkowskich `InitInstance` [RegisterShellFileTypes](../mfc/reference/cwinapp-class.md#registershellfiletypes) i [EnableShellOpen](../mfc/reference/cwinapp-class.md#enableshellopen) [cWinApp](../mfc/reference/cwinapp-class.md) do zastąpienia, które zapisuje dla Ciebie.

`RegisterShellFileTypes`rejestruje typy dokumentów aplikacji za pomocą Eksploratora plików lub Menedżera plików. Funkcja dodaje wpisy do bazy danych rejestracji, która utrzymuje system Windows. Wpisy rejestrują każdy typ dokumentu, kojarzą rozszerzenie pliku z typem pliku, określają wiersz polecenia, aby otworzyć aplikację, i określają polecenie dynamicznej wymiany danych (DDE), aby otworzyć dokument tego typu.

`EnableShellOpen`kończy proces, umożliwiając aplikacji odbieranie poleceń DDE z Eksploratora plików lub Menedżera plików w celu otwarcia pliku wybranego przez użytkownika.

Ta obsługa automatycznej rejestracji eliminuje `CWinApp` konieczność wysłania pliku reg z aplikacją lub wykonania specjalnej pracy instalacyjnej.

Jeśli chcesz zainicjować GDI+ dla aplikacji (wywołując [GdiplusStartup](/windows/win32/api/gdiplusinit/nf-gdiplusinit-gdiplusstartup) w funkcji [InitInstance),](../mfc/reference/cwinapp-class.md#initinstance) należy pominąć GDI + wątku tła.

Można to zrobić, `SuppressBackgroundThread` ustawiając element członkowski struktury [GdiplusStartupInput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupinput) na **TRUE**. Podczas wskrzeszenia wątku tła GDI+ `NotificationHook` i `NotificationUnhook` wywołania powinny być wykonane tuż przed wprowadzeniem i zamknięciem pętli komunikatów aplikacji. Aby uzyskać więcej informacji na temat tych połączeń, zobacz [GdiplusStartupOutput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupoutput). W związku z tym `GdiplusStartup` dobrym miejscem do wywołania i funkcji powiadomień hak będzie w zastąpienia funkcji wirtualnej [CWinApp::Run](../mfc/reference/cwinapp-class.md#run), jak pokazano poniżej:

[!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]

Jeśli nie pominąć wątku GDI+ w tle, polecenia DDE mogą być przedwcześnie wystawiane aplikacji przed utworzeniem jej głównego okna. Polecenia DDE wydane przez powłokę mogą zostać przedwcześnie przerwane, co spowoduje komunikaty o błędach.

## <a name="file-manager-drag-and-drop"></a><a name="_core_file_manager_drag_and_drop"></a>Przeciąganie i upuszczanie Menedżera plików

Pliki można przeciągać z okna widoku plików w Menedżerze plików lub Eksploratorze plików do okna w aplikacji. Można na przykład włączyć jeden lub więcej plików, które mają być przeciągane do głównego okna aplikacji MDI, gdzie aplikacja może pobrać nazwy plików i otworzyć okna podrzędne MDI dla tych plików.

Aby włączyć przeciąganie i upuszczanie pliku w aplikacji, Kreator aplikacji MFC zapisuje wywołanie funkcji elementu `InitInstance`członkowskiego [CWnd](../mfc/reference/cwnd-class.md) [DragAcceptFiles](../mfc/reference/cwnd-class.md#dragacceptfiles) dla okna ramki głównej w pliku . Można usunąć to wywołanie, jeśli nie chcesz implementować funkcji przeciągania i upuszczania.

> [!NOTE]
> Można również zaimplementować bardziej ogólne możliwości przeciągania i upuszczania — przeciągania danych między dokumentami lub w ich obrębie — za pomocą ole. Aby uzyskać więcej informacji, zobacz artykuł [OLE przeciąganie i upuszczanie](../mfc/drag-and-drop-ole.md).

## <a name="keeping-track-of-the-most-recently-used-documents"></a><a name="_core_keeping_track_of_the_most_recently_used_documents"></a>Śledzenie ostatnio używanych dokumentów

Gdy użytkownik otwiera i zamyka pliki, obiekt aplikacji śledzi cztery ostatnio używane pliki. Nazwy tych plików są dodawane do menu Plik i aktualizowane po ich zmianie. Struktura przechowuje te nazwy plików w rejestrze lub w pliku .ini, o takiej samej nazwie jak projekt i odczytuje je z pliku podczas uruchamiania aplikacji. Zastąpienie `InitInstance` tworzone przez Kreatora aplikacji MFC zawiera wywołanie funkcji członkowskiej [CWinApp](../mfc/reference/cwinapp-class.md) [LoadStdProfileSettings,](../mfc/reference/cwinapp-class.md#loadstdprofilesettings)która ładuje informacje z rejestru lub pliku .ini, w tym ostatnio używane nazwy plików.

Te wpisy są przechowywane w następujący sposób:

- W systemie Windows NT, systemie Windows 2000 i nowszych wartość jest przechowywana w kluczu rejestru.

- W systemie Windows 3.x wartość jest przechowywana w win. ini.

- W systemie Windows 95 i nowszych wartość jest przechowywana w buforowanej wersji win. Ini.

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
