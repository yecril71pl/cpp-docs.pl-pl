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
ms.openlocfilehash: 910660253c9d306b13294a710021a6bbd36c1952
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307318"
---
# <a name="special-cwinapp-services"></a>Specjalne usługi CWinApp

Oprócz uruchamiania pętli komunikatów i zapewniając możliwość inicjowania aplikacji i wyczyść zasoby po ukończeniu, [CWinApp](../mfc/reference/cwinapp-class.md) zawiera kilka innych usług.

##  <a name="_core_shell_registration"></a> Rejestracja powłoki

Domyślnie Kreator aplikacji MFC umożliwia użytkownikowi otwieranie plików danych, utworzonych przez dwukrotne kliknięcie pliku w Eksploratorze plików lub Menedżer plików aplikacji. Jeśli Twoja aplikacja jest aplikacją MDI i określ rozszerzenie dla plików, aplikacja tworzy, Kreator aplikacji MFC dodaje wywołania [registershellfiletypes —](../mfc/reference/cwinapp-class.md#registershellfiletypes) i [enableshellopen —](../mfc/reference/cwinapp-class.md#enableshellopen)funkcje elementów członkowskich [CWinApp](../mfc/reference/cwinapp-class.md) do `InitInstance` zastąpienie zapisującej dla Ciebie.

`RegisterShellFileTypes` rejestruje typy dokumentów aplikacji za pomocą Eksploratora plików lub Menedżer plików. Funkcja dodaje wpisy do bazy danych rejestracji, która utrzymuje Windows. Wpisy zarejestrować każdy typ dokumentu, skojarzyć rozszerzenie pliku z typem pliku, określenie wiersza polecenia, aby otworzyć aplikację i określić polecenie do programu exchange (DDE) dane dynamiczne, aby otworzyć dokument tego typu.

`EnableShellOpen` kończy proces, umożliwiając aplikacji na odbieranie poleceń DDE z Eksploratora plików lub Menedżera plików, aby otworzyć plik, wybierany przez użytkownika.

Ta obsługa automatycznej rejestracji w `CWinApp` eliminuje potrzeby dostarczać pliku reg za pomocą aplikacji ani wykonywać pracę specjalnej instalacji.

Jeśli chcesz zainicjować interfejsu GDI + aplikacji (przez wywołanie metody [GdiplusStartup](/windows/desktop/api/gdiplusinit/nf-gdiplusinit-gdiplusstartup) w swojej [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) funkcji), należy pominąć GDI + wątek w tle.

Można to zrobić, ustawiając `SuppressBackgroundThread` członkiem [GdiplusStartupInput](/windows/desktop/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupinput) struktury do **TRUE**. Gdy pomijanie GDI + w tle w wątku, `NotificationHook` i `NotificationUnhook` wywołania należy po prostu wcześniejsze wprowadzanych i wyprowadzanych pętli komunikatów dla aplikacji. Aby uzyskać więcej informacji na temat tych wywołań, zobacz [GdiplusStartupOutput](/windows/desktop/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupoutput). W związku z tym, dobrym miejscem do śledzenia wywołań `GdiplusStartup` i funkcje punktu zaczepienia powiadomień będzie znajdować się w przesłonięcie funkcji wirtualnej [CWinApp::Run](../mfc/reference/cwinapp-class.md#run), jak pokazano poniżej:

[!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]

Jeśli nie pomijać GDI + wątku tła, DDE polecenia mogą być przedwcześnie wydawane do aplikacji przed wyświetleniem głównego okna została utworzona. Wystawiony przez powłokę poleceń DDE można przedwcześnie przerwana, wynikiem komunikaty o błędach.

##  <a name="_core_file_manager_drag_and_drop"></a> Menedżer plików — przeciąganie i upuszczanie

Pliki mogą być przeciągnięte z okna widoku pliku w Menedżerze plików lub Eksploratora plików do okna aplikacji. Być może na przykład włączyć jeden lub więcej plików, można przeciągać do okna głównego aplikacji MDI, gdzie aplikacja może pobrać nazwy pliku i otwórz oknami podrzędnymi MDI dla tych plików.

Do pliku przeciągania i upuszczania w aplikacji, Kreator aplikacji MFC zapisuje wywołanie [CWnd](../mfc/reference/cwnd-class.md) funkcja elementu członkowskiego [DragAcceptFiles](../mfc/reference/cwnd-class.md#dragacceptfiles) dla okna głównej ramki w swojej `InitInstance`. Możesz usunąć to wywołanie, jeśli nie chcesz zaimplementować funkcję przeciągania i upuszczania.

> [!NOTE]
>  Można również zaimplementować bardziej ogólne możliwości przeciągania i upuszczania — przeciąganie danych między lub w dokumentach — przy użyciu OLE. Aby uzyskać informacje, zobacz artykuł [przeciąganie i upuszczanie (OLE)](../mfc/drag-and-drop-ole.md).

##  <a name="_core_keeping_track_of_the_most_recently_used_documents"></a> Rejestrowanie informacji o najbardziej niedawno używane dokumenty

Kiedy użytkownik otwiera i zamyka pliki, obiekt aplikacji śledzi informacje o czterech ostatnio używanych plików. Nazwy tych plików są dodawane do menu Plik i aktualizowane po zmianie. Struktura przechowuje te nazwy plików, albo rejestru lub w pliku .ini, z taką samą nazwę jak projektu i odczytuje je z pliku, podczas uruchamiania aplikacji. `InitInstance` Zastąpienia, Kreator aplikacji MFC tworzy zawiera wywołanie [CWinApp](../mfc/reference/cwinapp-class.md) funkcja elementu członkowskiego [loadstdprofilesettings —](../mfc/reference/cwinapp-class.md#loadstdprofilesettings), który ładuje informacje z rejestru lub pliku ini plik, tym najnowsze używany w nazwach plików.

Te wpisy są przechowywane w następujący sposób:

- Windows NT, Windows 2000 lub nowszym, wartość jest przechowywana w kluczu rejestru.

- W Windows 3.x, a wartość jest przechowywana w ZWYCIĘSTWA. Pliku INI.

- W Windows 95 lub nowszy wartość jest przechowywana w pamięci podręcznej wersji systemu Windows. PLIKU INI.

## <a name="see-also"></a>Zobacz także

[CWinApp: Klasa aplikacji](../mfc/cwinapp-the-application-class.md)
