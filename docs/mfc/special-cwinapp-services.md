---
title: "Specjalne usługi CWinApp | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LoadStdProfileSettings
- EnableShellOpen
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28a12d9553e1519c158c0a0e9d2fcec6365b65fe
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="special-cwinapp-services"></a>Specjalne usługi CWinApp
Poza systemem pętli komunikatów i zapewniając możliwość inicjowania aplikacji i wyczyścić, po którym [CWinApp](../mfc/reference/cwinapp-class.md) zawiera kilka innych usług.  
  
##  <a name="_core_shell_registration"></a>Rejestracja powłoki  
 Domyślnie Kreator aplikacji MFC umożliwia użytkownikowi otwieranie plików danych, utworzonych przez aplikację poprzez dwukrotne kliknięcie w Eksploratorze plików lub Menedżera plików. Jeśli aplikacja to aplikacja MDI i określ rozszerzeń plików, aplikacja tworzy, Kreator aplikacji MFC dodaje wywołań [RegisterShellFileTypes](../mfc/reference/cwinapp-class.md#registershellfiletypes) i [EnableShellOpen](../mfc/reference/cwinapp-class.md#enableshellopen)funkcji Członkowskich [CWinApp](../mfc/reference/cwinapp-class.md) do `InitInstance` zastąpienie zapisującej dla Ciebie.  
  
 `RegisterShellFileTypes`rejestruje typów dokumentów aplikacji z Eksploratora plików lub Menedżera plików. Funkcja dodaje wpisy w bazie danych rejestracji systemu Windows zachowuje. Wpisy rejestru każdego typu dokumentu, skojarzyć rozszerzenie pliku z typem pliku określ wiersz polecenia, aby otworzyć aplikację i określ polecenie programu exchange (DDE) dane dynamiczne, aby otworzyć dokument tego typu.  
  
 `EnableShellOpen`kończy proces, co pozwala aplikacji odbierać polecenia DDE z Eksploratora plików lub Menedżera plików, aby otworzyć plik, wybierany przez użytkownika.  
  
 Ta obsługa automatycznej rejestracji w `CWinApp` eliminuje potrzebę dostarczać pliku reg z aplikacją lub wykonać pracę specjalnej instalacji.  
  
 Jeśli chcesz zainicjować GDI + aplikacji (wywołując [GdiplusStartup](https://msdn.microsoft.com/library/ms534077) w Twojej [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) funkcji), należy pominąć GDI + wątek w tle.  
  
 Można to zrobić przez ustawienie **SuppressBackgroundThread** członkiem [GdiplusStartupInput](https://msdn.microsoft.com/library/ms534067) struktury do **TRUE**. Gdy pomijanie GDI + w tle wątku, **NotificationHook** i **NotificationUnhook** wywołania należy po prostu wcześniejsze wprowadzanie i zamykanie pętli komunikatów aplikacji. Aby uzyskać więcej informacji o tych wywołań, zobacz [GdiplusStartupOutput](https://msdn.microsoft.com/library/ms534068). W związku z tym dobrym miejscem do wywołania **GdiplusStartup** i funkcji punktów zaczepienia powiadomień będzie znajdować się w przesłonięcie funkcji wirtualnej [CWinApp::Run](../mfc/reference/cwinapp-class.md#run), jak pokazano poniżej:  
  
 [!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]  
  
 Jeśli nie pominąć GDI + wątku tła, DDE polecenia mogą być przedwcześnie wydawane do aplikacji przed utworzeniem jej głównego okna. Wystawiony przez powłokę poleceń DDE można przedwcześnie przerwana, co w komunikatach o błędach.  
  
##  <a name="_core_file_manager_drag_and_drop"></a>Menedżer plików — przeciąganie i upuszczanie  
 Pliki mogą być przeciągnięte z okno widoku plików w Menedżerze plików lub Eksploratora plików do okna aplikacji. Może na przykład włączyć co najmniej jeden plik do przeciąganych do głównego okna MDI aplikacji, gdzie aplikacja może pobrać nazwy pliku i okien podrzędnych MDI dla tych plików.  
  
 Do pliku przeciągania i upuszczania w aplikacji, Kreator aplikacji MFC zapisuje wywołanie [CWnd](../mfc/reference/cwnd-class.md) funkcji członkowskiej [DragAcceptFiles](../mfc/reference/cwnd-class.md#dragacceptfiles) główną ramkę okna w Twojej `InitInstance`. Jeśli nie chcesz wdrożyć funkcję przeciągania i upuszczania, można usunąć tego wywołania.  
  
> [!NOTE]
>  Można też wdrożyć bardziej ogólne możliwości przeciągania i upuszczania — przeciąganie danych między lub w dokumentach — z OLE. Aby uzyskać informacje, zobacz artykuł [przeciąganie i upuszczanie (OLE)](../mfc/drag-and-drop-ole.md).  
  
##  <a name="_core_keeping_track_of_the_most_recently_used_documents"></a>Rejestrowanie informacji o najczęściej niedawno używane dokumenty  
 Jako użytkownik otwiera i zamyka pliki, obiekt aplikacji przechowuje informacje o czterech ostatnio używanych plików. Nazwy tych plików są dodawane do menu Plik i aktualizowane po zmianie. Platformę przechowuje te nazwy plików w rejestrze albo lub w pliku .ini, z taką samą nazwę jak projektu i odczytuje je z pliku podczas uruchamiania aplikacji. `InitInstance` Zastąpienia, że Kreator aplikacji MFC tworzy zawiera wywołanie [CWinApp](../mfc/reference/cwinapp-class.md) funkcji członkowskiej [LoadStdProfileSettings](../mfc/reference/cwinapp-class.md#loadstdprofilesettings), który ładuje informacje z rejestru lub pliku ini plik, tym najnowsze używane nazwy pliku.  
  
 Te wpisy są przechowywane w następujący sposób:  
  
-   W systemie Windows NT, Windows 2000 lub nowszym, wartość jest przechowywana w kluczu rejestru.  
  
-   W systemie Windows 3.x, wartość jest przechowywana w Windows. Pliku INI.  
  
-   W systemie Windows 95 lub nowszy wartość jest przechowywana w pamięci podręcznej wersji systemu Windows. INI.  
  
## <a name="see-also"></a>Zobacz też  
 [CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)