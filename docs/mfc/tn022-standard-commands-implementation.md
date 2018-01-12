---
title: "TN022: Implementacja poleceń Standard | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.commands
dev_langs: C++
helpviewer_keywords:
- ID_PREV_PANE command [MFC]
- ID_APP_EXIT command [MFC]
- ID_NEXT_PANE command [MFC]
- ID_INDICATOR_REC command [MFC]
- ID_WINDOW_SPLIT command [MFC]
- ID_FILE_PRINT_PREVIEW command [MFC]
- ID_WINDOW_CASCADE command [MFC]
- ID_FILE_CLOSE command [MFC]
- ID_FILE_SAVE_COPY_AS command [MFC]
- ID_WINDOW_ARRANGE command [MFC]
- ID_EDIT_FIND command [MFC]
- ID_FILE_OPEN command [MFC]
- ID_FILE_PAGE_SETUP command [MFC]
- ID_OLE_VERB_FIRST command [MFC]
- ID_EDIT_UNDO command [MFC]
- ID_EDIT_CLEAR command [MFC]
- ID_INDICATOR_CAPS command [MFC]
- ID_HELP_INDEX command [MFC]
- commands [MFC], standard
- ID_FILE_PRINT_SETUP command [MFC]
- ID_DEFAULT_HELP command [MFC]
- ID_INDICATOR_SCRL command [MFC]
- ID_FILE_PRINT command [MFC]
- ID_INDICATOR_OVR command [MFC]
- ID_INDICATOR_KANA command [MFC]
- ID_EDIT_COPY command [MFC]
- ID_EDIT_REDO command [MFC]
- ID_EDIT_PASTE command [MFC]
- ID_OLE_INSERT_NEW command [MFC]
- ID_OLE_EDIT_LINKS command [MFC]
- ID_EDIT_PASTE_SPECIAL command [MFC]
- ID_INDICATOR_EXT command [MFC]
- ID_HELP_USING command [MFC]
- standard commands
- ID_VIEW_STATUS_BAR command [MFC]
- ID_FILE_SAVE_AS command [MFC]
- ID_EDIT_CLEAR_ALL command [MFC]
- ID_WINDOW_NEW command [MFC]
- ID_CONTEXT_HELP command [MFC]
- ID_EDIT_REPLACE command [MFC]
- ID_WINDOW_TILE_HORZ command [MFC]
- ID_APP_ABOUT command [MFC]
- TN022
- ID_VIEW_TOOLBAR command [MFC]
- ID_HELP command [MFC]
- ID_WINDOW_TILE_VERT command [MFC]
- ID_EDIT_CUT command [MFC]
- ID_FILE_UPDATE command [MFC]
- ID_EDIT_REPEAT command [MFC]
- ID_FILE_SAVE command [MFC]
- ID_EDIT_PASTE_LINK command [MFC]
- ID_EDIT_SELECT_ALL command [MFC]
- ID_FILE_NEW command [MFC]
- ID_INDICATOR_NUM command
ms.assetid: a7883b46-23f7-4870-ac3a-804aed9258b5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 05e5e927ebfcb1584913d6415349c473bde4463c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tn022-standard-commands-implementation"></a>TN022: implementacja poleceń standardowych
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga opisuje implementacji standardowego polecenia udostępniane przez MFC 2.0. Odczyt [techniczne notatkę 21](../mfc/tn021-command-and-message-routing.md) pierwszy ponieważ opisuje mechanizmy służące do zaimplementowania wielu standardowych poleceń.  
  
 Założono znajomość architektury MFC, interfejsów API i popularną praktyką programowania. Udokumentowane, jak również nieudokumentowanej "implementacji tylko" interfejsy API są opisane. To nie jest zacząć poznawania funkcji lub na temat programowania MFC. Znajdują się w Visual C++, aby uzyskać więcej ogólnych informacji i szczegółowe udokumentowane interfejsów API.  
  
## <a name="the-problem"></a>Problem  
 MFC definiuje wiele identyfikatory poleceń standardowych w pliku nagłówka AFXRES. H. Zmienia się Framework obsługę tych poleceń. Zrozumienie, jak i gdzie klas w ramach obsługi tych poleceń nie tylko opisano sposób platformę działania wewnętrznie, ale będzie dostarczające przydatnych informacji na temat sposobu dostosowywania implementacji standardowego i omawiające kilka metod wdrażania własne programy obsługi poleceń.  
  
## <a name="contents-of-this-technical-note"></a>Zawartość tej uwagi techniczne  
 Każdy identyfikator polecenia jest opisane w dwie sekcje:  
  
-   Tytuł: nazwy symbolicznej identyfikator polecenia (na przykład **id_file_save —**) następuje celem polecenia (na przykład "zapisuje bieżący dokument"), oddzielone dwukropkiem.  
  
-   Jeden lub kilka akapitów opisujące klas, które implementuje polecenia oraz jaki jest domyślna implementacja  
  
 Większość domyślnej implementacji polecenia są prewired w mapie komunikatów klasy podstawowej struktury. Dostępne są niektóre implementacje polecenia, które wymagają jawną przewodów w klasie pochodnej. Te ustawienia zostały opisane w obszarze "Note". W przypadku wybrania opcji prawo w kreatorami AppWizard te programy obsługi domyślny zostaną połączone automatycznie wygenerowanego szkielet aplikacji.  
  
## <a name="naming-convention"></a>Konwencje nazewnictwa  
 Polecenia standardowe wykonaj proste konwencji nazewnictwa, która firma Microsoft zaleca się, że używasz, jeśli to możliwe. Większość standardowych poleceń znajdują się w standardowe miejsca na pasku menu aplikacji. Nazwa symboliczna polecenia rozpoczyna się od "ID_", po której następuje nazwa standardowe menu podręczne, następuje nazwa elementu menu. Nazwa symboliczna jest wielkimi literami z dzielenie wyrazów podkreślenia. Dla poleceń, które nie mają nazwy elementów menu standardowego, nazwę logiczną polecenia jest zdefiniowany, począwszy od "ID_" (na przykład **id_next_pane —**).  
  
 Prefiks "ID_" możemy służy do wskazywania poleceń, które mają być powiązane z elementów menu, przycisków paska narzędzi lub innych obiektów interfejsu użytkownika poleceń. Obsługa poleceń "ID_" programy obsługi poleceń należy użyć `ON_COMMAND` i `ON_UPDATE_COMMAND_UI` mechanizmów MFC polecenia architektury.  
  
 Firma Microsoft zaleca się, że używasz standardowego prefiksu "IDM_" dla elementów menu, które postępuj zgodnie z architekturą polecenia i nie wymagają kodu określonych menu, aby włączyć lub wyłączyć je. Oczywiście liczba określonych poleceń menu powinna być niewielka, ponieważ następujące polecenia architekturę MFC nie tylko zapewnia bardziej zaawansowanych programy obsługi poleceń (ponieważ będą one działać pasków narzędzi), ale powoduje, że kod obsługi polecenia wielokrotnego użytku.  
  
## <a name="id-ranges"></a>Identyfikator zakresów  
 Zapoznaj się z [20 Uwaga techniczna](../mfc/tn020-id-naming-and-numbering-conventions.md) uzyskać więcej informacji dotyczących użycia zakresów identyfikator w MFC.  
  
 Polecenia standardowe MFC należy do zakresu 0xE000 do 0xEFFF. Proszę nie należy polegać na określone wartości tych identyfikatorów ponieważ są one może ulec zmianie w przyszłych wersjach biblioteki.  
  
 Aplikację należy zdefiniować jego poleceń w zakresie 0x8000 do 0xDFFF.  
  
## <a name="standard-command-ids"></a>Identyfikatory poleceń standardowych  
 Dla każdego Identyfikatora polecenia jest ciąg monitu wiersza standardowy komunikat, który znajduje się w pliku MONITÓW. RC. Identyfikator ciągu dla tego monitu menu musi być taki sam jak identyfikator polecenia.  
  
-   Id_file_new — tworzy dokument nowych lub być pusty.  
  
    > [!NOTE]
    >  Należy tutaj, aby połączyć Twoje `CWinApp`-pochodnej klasy mapy wiadomości, aby włączyć tę funkcję.  
  
     `CWinApp::OnFileNew`implementuje to polecenie inaczej w zależności od liczby szablonów dokumentów w aplikacji. Jeśli istnieje tylko jeden `CDocTemplate`, `CWinApp::OnFileNew` utworzy nowy dokument tego typu, a także odpowiednią klasą ramki i widoku.  
  
     Jeśli istnieje więcej niż jeden `CDocTemplate`, `CWinApp::OnFileNew` pojawi się monit z okna dialogowego (**AFX_IDD_NEWTYPEDLG**) pozwalając im wybierz typ dokumentu. Wybrane `CDocTemplate` służy do tworzenia dokumentu.  
  
     Co typowe dostosowywania `ID_FILE_NEW` jest zapewnienie inną i większy wybór graficznego typów dokumentów. W takim przypadku można wdrożyć własne **CMyApp::OnFileNew** i umieścić go w mapy wiadomości zamiast `CWinApp::OnFileNew`. Nie istnieje potrzeba do wywołania implementacji klasy podstawowej.  
  
     Inne dostosowanie wspólnego z `ID_FILE_NEW` jest zapewnienie osobne polecenie tworzenia dokumentu każdego typu. W takim przypadku należy zdefiniować nowe polecenie identyfikatorów, na przykład ID_FILE_NEW_CHART i ID_FILE_NEW_SHEET.  
  
-   Id_file_open — otwiera istniejący dokument.  
  
    > [!NOTE]
    >  Należy tutaj, aby połączyć Twoje `CWinApp`-pochodnej klasy mapy wiadomości, aby włączyć tę funkcję.  
  
     `CWinApp::OnFileOpen`jest bardzo prosta implementacja wywołania metody **CWinApp::DoPromptFileName** następuje `CWinApp::OpenDocumentFile` o nazwie pliku lub ścieżki pliku, aby otworzyć. `CWinApp` Procedura implementacji **DoPromptFileName** Wyświetla standardowe okno dialogowe FileOpen i wypełnia je z rozszerzeniami uzyskane z bieżącym szablonów dokumentów.  
  
     Co typowe dostosowywania `ID_FILE_OPEN` dostosować okna dialogowego FileOpen lub Dodaj filtry dodatkowego pliku. Zalecanym sposobem dostosować ma zastąpić domyślną implementację własne okna dialogowego FileOpen i wywołanie `CWinApp::OpenDocumentFile` z nazwą pliku lub ścieżkę dokumentu. Nie istnieje potrzeba do wywołania klasy podstawowej.  
  
-   Id_file_close — powoduje zamknięcie aktualnie otwartego dokumentu.  
  
     **CDocument::OnFileClose** wywołania `CDocument::SaveModified` monit, aby zapisać dokument, jeśli został zmodyfikowany, a następnie wywołuje `OnCloseDocument`. Całą logikę zamknięcia, łącznie z niszczenia samego dokumentu odbywa się `OnCloseDocument` procedury.  
  
    > [!NOTE]
    >  **Id_file_close —** działa inaczej z `WM_CLOSE` wiadomości lub **SC_CLOSE** systemu polecenia wysyłane do okna ramowe dokumentów. Zamknięcie okna zamknąć dokument tylko wtedy, gdy to okno ramowe ostatniego przedstawiający dokumentu. Zamykanie dokumentów z **id_file_close —** tylko nie zostanie zamknięte dokumentu, ale będzie zamknięcia wszystkich okien ramki przedstawiający dokumentu.  
  
-   Id_file_save — zapisuje bieżący dokument.  
  
     Implementacja używa procedury Pomocnika **CDocument::DoSave** używany dla obu **OnFileSave** i **OnFileSaveAs**. Jeśli zapiszesz dokument, który nie został zapisany przed (to znaczy, że nie ma nazwę ścieżki, jak w przypadku nowy plik) lub z dokumentem tylko do odczytu odczytano **OnFileSave** logiki będzie działać tak jak **id_file_save_as —** polecenia, a następnie poprosić użytkownika o Podaj nową nazwę pliku. Rzeczywisty proces otwierania pliku i wykonywania zapisywania odbywa się za pośrednictwem funkcji wirtualnej `OnSaveDocument`.  
  
     Istnieją dwie typowe przyczyny, aby dostosować **id_file_save —**. Dokumenty, które nie zostaną zapisane, wystarczy usunąć **id_file_save —** elementów menu i przycisków paska narzędzi z interfejsu użytkownika. Upewnij się, nigdy nie zmieniony dokument również (oznacza to, że nigdy nie wywołać `CDocument::SetModifiedFlag`) i w ramach nigdy nie spowoduje, że na zapisanie dokumentu. W przypadku dokumentów, które zapisują do wiadomo gdzie innych niż pliki dysku zdefiniować nowe polecenie dla tej operacji.  
  
     W przypadku liczby `COleServerDoc`, **id_file_save —** jest używany zarówno do zapisu pliku (w przypadku normalnych dokumenty) i aktualizacji pliku (dla osadzonych dokumentów).  
  
     Jeśli dane dokumentu są przechowywane w plikach pojedynczego dysku, ale nie chcesz użyć domyślnego **CDocument** serializować implementacji, należy zastąpić `CDocument::OnSaveDocument` zamiast **OnFileSave**.  
  
-   Id_file_save_as — zapisuje bieżący dokument pod inną nazwą pliku.  
  
     **CDocument::OnFileSaveAs** implementacji używana taka sama **CDocument::DoSave** procedury pomocnika jako **OnFileSave**. **OnFileSaveAs** polecenie jest obsługiwane tylko jako **id_file_save —** gdyby nie nazwę pliku przed zapisywania dokumentów. **COleServerDoc::OnFileSaveAs** implementuje logiki można zapisać pliku danych normalnego dokumentu lub zapisać dokument serwera reprezentujący obiekt OLE osadzonych w innej aplikacji jako oddzielny plik.  
  
     W przypadku dostosowania logiki **id_file_save —**, który prawdopodobnie chcesz dostosować **id_file_save_as —** w podobny sposób lub działania "Zapisz jako" nie może zastosować do dokumentu. Jeśli nie jest potrzebna, można usunąć elementu menu z paska menu.  
  
-   Id_file_save_copy_as — zapisuje bieżący dokument pod nową nazwą.  
  
     **COleServerDoc::OnFileSaveCopyAs** implementacja jest bardzo podobny do **CDocument::OnFileSaveAs**, ale obiekt dokumentu nie jest "dołączony" do pliku źródłowego po zapisu. Oznacza to czy w pamięci "modyfikacji dokumentu" przed zapisu, jest on nadal "zmodyfikowany". Ponadto to polecenie nie ma wpływu na nazwy ścieżki lub tytuł przechowywane w dokumencie.  
  
-   Id_file_update — powiadamia kontener, aby zapisać dokument osadzony.  
  
     `COleServerDoc::OnUpdateDocument` Implementacji po prostu notifiies kontenera, w którym ma zostać zapisany osadzania. Kontener wywołuje odpowiednie OLE interfejsy API w celu zapisania osadzonego obiektu.  
  
-   Id_file_page_setup — wywołuje okno dialogowe Ustawienia/układ strony specyficzne dla aplikacji.  
  
     Obecnie nie istnieje dla tego okna dialogowego standard i ramach ma domyślnej implementacji tego polecenia.  
  
     Jeśli wybierzesz opcję wykonania tego polecenia, firma Microsoft zaleca się, że używasz tego identyfikatora polecenia.  
  
-   Id_file_print_setup — Wywołaj standardowe okno dialogowe Ustawienia wydruku.  
  
    > [!NOTE]
    >  Należy tutaj, aby połączyć Twoje `CWinApp`-pochodnej klasy mapy wiadomości, aby włączyć tę funkcję.  
  
     To polecenie wywołuje okno dialogowe standardowe ustawienia wydruku, który umożliwia użytkownikowi dostosowywanie drukarki i wydruku ustawienia dla co najmniej tego dokumentu lub co najwyżej wszystkie dokumenty w tej aplikacji. Panel sterowania należy użyć, aby zmienić domyślne ustawienia drukarki dla całego systemu.  
  
     `CWinApp::OnFilePrintSetup`jest bardzo prosta implementacja tworzenie `CPrintDialog` obiektów i wywoływania **CWinApp::DoPrintDialog** implementację funkcji. To ustawienie aplikacji ustawienia drukarki domyślnej.  
  
     Potrzebują dostosowywania tego polecenia jest umożliwienie dla ustawienia drukarki poszczególnych dokumentów, które powinny być przechowywane z podczas zapisywania dokumentu. W tym celu należy dodać obsługi mapę komunikatów w Twojej **CDocument** klasy, która tworzy `CPrintDialog` obiektów, inicjowane z atrybutami odpowiednich drukarek (zazwyczaj **pole hDevMode** i **hDevNames**), wywołaj **CPrintDialog::DoModal,** i Zapisz ustawienia drukarki zmienione. Niezawodne implementacji, należy rozważyć wykonania **CWinApp::DoPrintDialog** wykrywania błędów i **CWinApp::UpdatePrinterSelection** zajmujących się za pośrednictwem ustawień domyślnych i Śledzenie zmian drukarki całego systemu.  
  
-   Id_file_print — standardowe drukowanie bieżącego dokumentu  
  
    > [!NOTE]
    >  Należy tutaj, aby połączyć Twoje `CView`-pochodnej klasy mapy wiadomości, aby włączyć tę funkcję.  
  
     To polecenie wyświetla bieżący dokument lub właściwie, rozpoczyna się proces drukowania obejmuje wywoływania standardowe okno dialogowe i uruchamiania aparatu wydruku.  
  
     **CView::OnFilePrint** implementuje tego polecenia, a głównym pętli wydruku. Wywołuje wirtualny `CView::OnPreparePrinting` monit użytkownika z okna dialogowego drukowania. On następnie przygotowuje dane wyjściowe kontrolera domeny, aby przejść do drukarki, powoduje wyświetlenie okna dialogowego postępu drukowania (**AFX_IDD_PRINTDLG**) i wysyła `StartDoc` escape do drukarki. **CView::OnFilePrint** zawiera także zorientowane na stronie wydruku pętli głównej. Dla każdej strony wywołuje wirtualny `CView::OnPrepareDC` następuje `StartPage` escape i wywoływania wirtualnego `CView::OnPrint` dla tej strony. Po zakończeniu, wirtualnej `CView::OnEndPrinting` jest nazywany i drukowania okna dialogowego postępu jest zamknięty.  
  
     Architektura drukowania MFC umożliwia utworzenie punktu zaczepienia w wiele różnych sposobów drukowania i podglądu wydruku. Zwykle znajdują się różne `CView` funkcje z możliwością zastąpienia odpowiednie dla dowolnego zorientowane na stronie zadań drukowania. Tylko w przypadku aplikacji, która używa drukarki dla strony z systemem innym niż zorientowane na dane wyjściowe, użytkownik stwierdzi, że trzeba zastąpić **id_file_print —** implementacji.  
  
-   Wprowadź id_file_print_preview — tryb podglądu wydruku w bieżącym dokumencie.  
  
    > [!NOTE]
    >  Należy tutaj, aby połączyć Twoje `CView`-pochodnej klasy mapy wiadomości, aby włączyć tę funkcję.  
  
     **CView::OnFilePrintPreview** uruchamia tryb podglądu wydruku przez wywołanie funkcji pomocnika udokumentowane **CView::DoPrintPreview**. **CView::DoPrintPreview** jest aparat głównego dla pętli podglądu wydruku, podobnie jak **OnFilePrint** jest aparat głównego drukowania pętli for.  
  
     Operacja podglądu wydruku można dostosować w różny sposób przez przekazanie różnych parametrów do **DoPrintPreview**. Zapoznaj się z [30 Uwaga techniczna](../mfc/tn030-customizing-printing-and-print-preview.md), omówiono w nim szczegóły podglądu wydruku i sposobami ich dostosowywania.  
  
-   **ID_FILE_MRU_FILE1**... **FILE16** zakres identyfikatorów poleceń dla ostatnio używanych plików `list`.  
  
     **CWinApp::OnUpdateRecentFileMenu** obsługi interfejsu użytkownika polecenie aktualizacji, które jest jednym z bardziej zaawansowanych zastosowań `ON_UPDATE_COMMAND_UI` mechanizmu. W menu zasobu, należy tylko zdefiniować pojedynczy element menu o identyfikatorze **ID_FILE_MRU_FILE1**. Element menu pozostaje początkowo wyłączone.  
  
     Jako MRU listy rozwojem więcej menu, które elementy są dodawane do listy. Standardowe `CWinApp` implementacji domyślnie standardowa limit czterech ostatnio używanych plików. Domyślne można zmienić, wywołując `CWinApp::LoadStdProfileSettings` z wartością większy lub mniejszy. Listy są przechowywane w aplikacji. Pliku INI. Lista jest ładowany do aplikacji `InitInstance` działać, jeśli wywołujesz `LoadStdProfileSettings`i jest zapisywana, gdy kończy działanie aplikacji. Program obsługi interfejsu użytkownika poleceń aktualizacji MRU również przekonwertuje ścieżki bezwzględne ścieżki względne do wyświetlenia w menu Plik.  
  
     **CWinApp::OnOpenRecentFile** jest `ON_COMMAND` program obsługi, który wykonuje polecenie rzeczywistych. Po prostu pobiera nazwę pliku z listy ostatnio używanych elementów i wywołania `CWinApp::OpenDocumentFile`, które wykonuje całą pracę otwierania pliku i aktualizowania listy ostatnio używanych.  
  
     Nie zaleca się Dostosowywanie programu obsługi poleceń.  
  
-   Id_edit_clear — usuwa bieżącego zaznaczenia  
  
     Obecnie nie istnieje żadne standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdego `CView`-klasy.  
  
     `CEditView`udostępnia implementację elementu za pomocą tego polecenia `CEdit::Clear`. Polecenie jest wyłączona, jeśli nie ma żadnego bieżącego zaznaczenia.  
  
     Jeśli wybierzesz opcję wykonania tego polecenia, firma Microsoft zaleca się, że używasz tego identyfikatora polecenia.  
  
-   Id_edit_clear_all — usuwa cały dokument.  
  
     Obecnie nie istnieje żadne standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdego `CView`-klasy.  
  
     Jeśli wybierzesz opcję wykonania tego polecenia, firma Microsoft zaleca się, że używasz tego identyfikatora polecenia. Zobacz przykład samouczek MFC [BAZGROŁY](../visual-cpp-samples.md) dla przykładem implementacji.  
  
-   Id_edit_copy — kopiuje bieżące zaznaczenie do Schowka.  
  
     Obecnie nie istnieje żadne standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdego `CView`-klasy.  
  
     `CEditView`udostępnia implementację tego polecenia, które kopiuje aktualnie zaznaczonego tekstu do Schowka jako CF_TEXT przy użyciu `CEdit::Copy`. Polecenie jest wyłączona, jeśli nie ma żadnego bieżącego zaznaczenia.  
  
     Jeśli wybierzesz opcję wykonania tego polecenia, firma Microsoft zaleca się, że używasz tego identyfikatora polecenia.  
  
-   Id_edit_cut — Wycina bieżące zaznaczenie do Schowka.  
  
     Obecnie nie istnieje żadne standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdego `CView`-klasy.  
  
     `CEditView`udostępnia implementację tego polecenia Wytnij aktualnie zaznaczonego tekstu do Schowka jako CF_TEXT przy użyciu `CEdit::Cut`. Polecenie jest wyłączona, jeśli nie ma żadnego bieżącego zaznaczenia.  
  
     Jeśli wybierzesz opcję wykonania tego polecenia, firma Microsoft zaleca się, że używasz tego identyfikatora polecenia.  
  
-   Id_edit_find — rozpoczyna operację wyszukiwania wyświetla okno dialogowe Znajdź niemodalne.  
  
     Obecnie nie istnieje żadne standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdego `CView`-klasy.  
  
     `CEditView`udostępnia implementację tego polecenia, który wywołuje funkcję pomocnika implementacji **OnEditFindReplace** i przechowywać poprzednie ustawienia Znajdź i Zamień w zmiennych prywatnych implementacji. `CFindReplaceDialog` Klasa jest używana do zarządzania niemodalnego okna dialogowego do monitowania użytkownika.  
  
     Jeśli wybierzesz opcję wykonania tego polecenia, firma Microsoft zaleca się, że używasz tego identyfikatora polecenia.  
  
-   Id_edit_paste — Wstawia bieżącą zawartość Schowka.  
  
     Obecnie nie istnieje żadne standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdego `CView`-klasy.  
  
     `CEditView`udostępnia implementację tego polecenia, które kopiuje bieżące dane Schowka, zastępowanie za pomocą zaznaczonego tekstu `CEdit::Paste`. Polecenie jest wyłączona, jeśli istnieje nie **CF_TEXT** w Schowku.  
  
     **COleClientDoc** tylko udostępnia program obsługi aktualizacji poleceń interfejsu użytkownika dla tego polecenia. Jeśli Schowek nie zawiera osadzenia elementu/obiektu OLE, polecenia zostaną wyłączone. Jest odpowiedzialny za pisanie programu obsługi na rzeczywiste wklejenie rzeczywiste polecenia. Jeśli w aplikacji OLE można również wkleić w innych formatach, należy podać własne polecenia interfejsu użytkownika programu obsługi aktualizacji w widoku lub dokumentu (oznacza to, gdzieś przed **COleClientDoc** w routing poleceń docelowy).  
  
     Jeśli wybierzesz opcję wykonania tego polecenia, firma Microsoft zaleca się, że używasz tego identyfikatora polecenia.  
  
     Zastępowanie standardowego wdrożenia OLE, użyj `COleClientItem::CanPaste`.  
  
-   Id_edit_paste_link — wstawia łącze z bieżącą zawartość Schowka.  
  
     Obecnie nie istnieje żadne standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdego `CView`-klasy.  
  
     `COleDocument`po prostu udostępnia program obsługi aktualizacji poleceń interfejsu użytkownika dla tego polecenia. Jeśli Schowek nie zawiera możliwym OLE elementu obiektu, polecenia zostaną wyłączone. Jest odpowiedzialny za pisanie programu obsługi na rzeczywiste wklejenie rzeczywiste polecenia. Jeśli w aplikacji OLE można również wkleić w innych formatach, należy podać własne polecenia interfejsu użytkownika programu obsługi aktualizacji w widoku lub dokumentu (oznacza to, gdzieś przed `COleDocument` w routing poleceń docelowy).  
  
     Jeśli wybierzesz opcję wykonania tego polecenia, firma Microsoft zaleca się, że używasz tego identyfikatora polecenia.  
  
     Zastępowanie standardowego wdrożenia OLE, użyj `COleClientItem::CanPasteLink`.  
  
-   Id_edit_paste_special — Wstawia bieżącą zawartość Schowka z opcjami.  
  
     Obecnie nie istnieje żadne standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdego `CView`-klasy. MFC nie oferuje tego okna dialogowego.  
  
     Jeśli wybierzesz opcję wykonania tego polecenia, firma Microsoft zaleca się, że używasz tego identyfikatora polecenia.  
  
-   Id_edit_repeat — powtarza ostatnią operację.  
  
     Obecnie nie istnieje żadne standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdego `CView`-klasy.  
  
     `CEditView`udostępnia implementację tego polecenia, aby ponownie wykonać ostatnią operację wyszukiwania. Prywatna implementacja zmienne ostatnie wyszukiwanie są używane. Polecenie jest wyłączona, jeśli nie można podjąć próby uruchomienia Znajdź.  
  
     Jeśli wybierzesz opcję wykonania tego polecenia, firma Microsoft zaleca się, że używasz tego identyfikatora polecenia.  
  
-   Id_edit_replace — rozpoczyna operacji Zastąp Wyświetla okno dialogowe niemodalne Zamień.  
  
     Obecnie nie istnieje żadne standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdego `CView`-klasy.  
  
     `CEditView`udostępnia implementację tego polecenia, który wywołuje funkcję pomocnika implementacji **OnEditFindReplace** i przechowywać poprzednie ustawienia Znajdź i Zamień w zmiennych prywatnych implementacji. `CFindReplaceDialog` Klasa jest używana do zarządzania niemodalnego okna dialogowego, które monituje użytkownika.  
  
     Jeśli wybierzesz opcję wykonania tego polecenia, firma Microsoft zaleca się, że używasz tego identyfikatora polecenia.  
  
-   Id_edit_select_all — zaznacza cały dokument.  
  
     Obecnie nie istnieje żadne standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdego `CView`-klasy.  
  
     `CEditView`udostępnia implementację tego polecenia, który wybiera cały tekst w dokumencie. Polecenie jest wyłączona, jeśli nie ma żadnego tekstu, aby wybrać.  
  
     Jeśli wybierzesz opcję wykonania tego polecenia, firma Microsoft zaleca się, że używasz tego identyfikatora polecenia.  
  
-   Id_edit_undo — Cofa ostatnią operację.  
  
     Obecnie nie istnieje żadne standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdego `CView`-klasy.  
  
     `CEditView`udostępnia implementację tego polecenia, za pomocą `CEdit::Undo`. Polecenie jest wyłączona, jeśli `CEdit::CanUndo` zwraca wartość FALSE.  
  
     Jeśli wybierzesz opcję wykonania tego polecenia, firma Microsoft zaleca się, że używasz tego identyfikatora polecenia.  
  
-   Id_edit_redo — wykonuje ponownie ostatnią operację.  
  
     Obecnie nie istnieje żadne standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdego `CView`-klasy.  
  
     Jeśli wybierzesz opcję wykonania tego polecenia, firma Microsoft zaleca się, że używasz tego identyfikatora polecenia.  
  
-   Id_window_new — Otwiera inne okno w aktywnym dokumencie.  
  
     **CMDIFrameWnd::OnWindowNew** implementuje ten zaawansowanych funkcji przy użyciu szablonu dokumentu bieżącego dokumentu w celu utworzenia innej ramki zawierające innego widoku bieżącego dokumentu.  
  
     Podobnie jak większość wielu dokumentów (MDI) interfejsu polecenia menu okna polecenie jest wyłączona, jeśli nie aktywne okno podrzędne MDI.  
  
     Nie zaleca się Dostosowywanie programu obsługi poleceń. Jeśli chcesz podać polecenie, które tworzy dodatkowe widoki lub ramka okna, prawdopodobnie będzie lepiej inventing własne polecenia. Można sklonować kod z **CMDIFrameWnd::OnWindowNew** i zastąp go dla określonych ramki oraz widoku klasy Twoim preferencjom.  
  
-   Id_window_arrange — Rozmieszcza ikony w dolnej części okna MDI.  
  
     `CMDIFrameWnd`implementuje standardowe polecenie MDI w implementacji funkcji pomocnika **OnMDIWindowCmd**. Tego pomocnika mapuje identyfikatory poleceń na komunikaty systemu Windows MDI i w związku z tym można udostępniać dużej ilości kodu.  
  
     Podobnie jak większość używanych poleceń menu okna MDI polecenie jest wyłączona, jeśli istnieje nie aktywne okno podrzędne MDI.  
  
     Nie zaleca się Dostosowywanie programu obsługi poleceń.  
  
-   Id_window_cascade — kaskady systemu windows, aby zachodziły na siebie.  
  
     `CMDIFrameWnd`implementuje standardowe polecenie MDI w implementacji funkcji pomocnika **OnMDIWindowCmd**. Tego pomocnika mapuje identyfikatory poleceń na komunikaty systemu Windows MDI i w związku z tym można udostępniać dużej ilości kodu.  
  
     Podobnie jak większość używanych poleceń menu okna MDI polecenie jest wyłączona, jeśli istnieje nie aktywne okno podrzędne MDI.  
  
     Nie zaleca się Dostosowywanie programu obsługi poleceń.  
  
-   Kafelki id_window_tile_horz — windows poziomo.  
  
     To polecenie jest zaimplementowana w `CMDIFrameWnd` podobnie jak **id_window_cascade —**, z wyjątkiem różnych komunikatów okien interfejsu MDI jest używany dla tej operacji.  
  
     Należy wybrać domyślną orientację kafelka aplikacji. Można to zrobić, zmieniając identyfikator dla elementu menu okna "Fragment" albo **id_window_tile_horz —** lub **id_window_tile_vert —**.  
  
-   Kafelki id_window_tile_vert — windows pionowo.  
  
     To polecenie jest zaimplementowana w `CMDIFrameWnd` podobnie jak **id_window_cascade —**, z wyjątkiem różnych komunikatów okien interfejsu MDI jest używany dla tej operacji.  
  
     Należy wybrać domyślną orientację kafelka aplikacji. Można to zrobić, zmieniając identyfikator dla elementu menu okna "Fragment" albo **id_window_tile_horz —** lub **id_window_tile_vert —**.  
  
-   Interfejs id_window_split — klawiatury do podziału.  
  
     `CView`to polecenie dla obsługi `CSplitterWnd` implementacji. Jeśli widok jest częścią okna podziału, to polecenie będzie delegowane do implementacji funkcji `CSplitterWnd::DoKeyboardSplit`. To spowoduje umieszczenie rozdzielacza w trybie, co umożliwi użytkownikom klawiatury podzielona lub cofnąć podziału okna podziału.  
  
     To polecenie jest niedostępne, jeśli widok nie jest rozdzielacza.  
  
     Nie zaleca się Dostosowywanie programu obsługi poleceń.  
  
-   Id_app_about — wywołuje okno dialogowe informacje.  
  
     Brak implementacji standardowe pole o aplikacji. Aplikacja utworzone z kreatorami AppWizard domyślne tworzenie klasy okien dialogowych niestandardowych aplikacji i używać go jako sieci o polu. Kreatorami AppWizard będzie również zapisywać obsługi trivial polecenia, który obsługuje tego polecenia, a następnie wywołuje okno dialogowe.  
  
     Prawie zawsze będzie wykonania tego polecenia.  
  
-   Id_app_exit — Zakończ działanie aplikacji.  
  
     **CWinApp::OnAppExit** obsługi tego polecenia, wysyłając `WM_CLOSE` wiadomości do okna głównego aplikacji. Standard zamykanie aplikacji (monitowanie o zanieczyszczeniu plików itd.) jest obsługiwany przez `CFrameWnd` implementacji.  
  
     Nie zaleca się Dostosowywanie programu obsługi poleceń. Zastępowanie `CWinApp::SaveAllModified` lub `CFrameWnd` zaleca się zamknięcie logiki.  
  
     Jeśli wybierzesz opcję wykonania tego polecenia, firma Microsoft zaleca się, że używasz tego identyfikatora polecenia.  
  
-   Wyświetla Pomoc id_help_index — tematy z. Plik HLP.  
  
    > [!NOTE]
    >  Należy tutaj, aby połączyć Twoje `CWinApp`-pochodnej klasy mapy wiadomości, aby włączyć tę funkcję.  
  
     `CWinApp::OnHelpIndex`obsługuje polecenie trivially wywołując `CWinApp::WinHelp`.  
  
     Nie zaleca się Dostosowywanie programu obsługi poleceń.  
  
-   Id_help_using — Wyświetla Pomoc na temat korzystania z pomocy.  
  
    > [!NOTE]
    >  Należy tutaj, aby połączyć Twoje `CWinApp`-pochodnej klasy mapy wiadomości, aby włączyć tę funkcję.  
  
     `CWinApp::OnHelpUsing`obsługuje polecenie trivially wywołując `CWinApp::WinHelp`.  
  
     Nie zaleca się Dostosowywanie programu obsługi poleceń.  
  
-   Tryb pomocy id_context_help — wprowadza SHIFT-F1.  
  
    > [!NOTE]
    >  Należy tutaj, aby połączyć Twoje `CWinApp`-pochodnej klasy mapy wiadomości, aby włączyć tę funkcję.  
  
     `CWinApp::OnContextHelp`obsługuje to polecenie ustawia kursor myszy trybu pomocy, wprowadzając pętli modalnej i Oczekiwanie na użytkownika wybrać okno, aby uzyskać pomoc na temat. Zapoznaj się z [28 Uwaga techniczna](../mfc/tn028-context-sensitive-help-support.md) uzyskać więcej informacji dotyczących implementacji MFC pomocy.  
  
     Nie zaleca się Dostosowywanie programu obsługi poleceń.  
  
-   Id_help — zapewnia pomoc w bieżącym kontekście  
  
    > [!NOTE]
    >  Należy tutaj, aby połączyć Twoje `CWinApp`-pochodnej klasy mapy wiadomości, aby włączyć tę funkcję.  
  
     `CWinApp::OnHelp`obsługuje polecenie pobierając kontekstu właściwą pomoc dla bieżącego kontekstu aplikacji. Obsługuje prosty pomocy F1, pomoc na temat pola wiadomości i tak dalej. Zapoznaj się z [28 Uwaga techniczna](../mfc/tn028-context-sensitive-help-support.md) dodatkowe szczegóły dotyczące MFC pomocy implementacji.  
  
     Nie zaleca się Dostosowywanie programu obsługi poleceń.  
  
-   Id_default_help — Wyświetla domyślny Pomoc dla kontekstu  
  
    > [!NOTE]
    >  Należy tutaj, aby połączyć Twoje `CWinApp`-pochodnej klasy mapy wiadomości, aby włączyć tę funkcję.  
  
     To polecenie jest zwykle mapowane na `CWinApp::OnHelpIndex`.  
  
     Jeśli wymagane jest różnica między domyślnymi pomocy i indeksu Pomocy można podać inną programem obsługi.  
  
-   Id_next_pane — przechodzi do następnego okienka  
  
     `CView`to polecenie dla obsługi `CSplitterWnd` implementacji. Jeśli widok jest częścią okna podziału, to polecenie będzie delegowane do implementacji funkcji **CSplitterWnd::OnNextPaneCmd**. Spowoduje to przeniesienie widoku aktywnego do następnego okienka w rozdzielacza.  
  
     To polecenie jest niedostępne, jeśli widok nie jest rozdzielacza lub nie nie następne okienko, aby przejść do.  
  
     Nie zaleca się Dostosowywanie programu obsługi poleceń.  
  
-   Id_prev_pane — przejście do poprzedniego okienka  
  
     `CView`to polecenie dla obsługi `CSplitterWnd` implementacji. Jeśli widok jest częścią okna podziału, to polecenie będzie delegowane do implementacji funkcji **CSplitterWnd::OnNextPaneCmd**. Spowoduje to przeniesienie widoku aktywnego do poprzedniego okienka w rozdzielacza.  
  
     To polecenie jest niedostępne, jeśli widok nie jest rozdzielacza lub nie nie poprzednie okienko, aby przejść do.  
  
     Nie zaleca się Dostosowywanie programu obsługi poleceń.  
  
-   Id_ole_insert_new — Wstawia nowy obiekt OLE  
  
     Obecnie nie istnieje żadne standardowej implementacji dla tego polecenia. Musisz zaimplementować dla Twojej `CView`-klasy, aby wstawić nowy element OLE/obiekt na bieżącym zaznaczeniu.  
  
     Wszystkie aplikacje klienckie OLE powinien implementować tego polecenia. Kreatorami AppWizard, z opcją OLE utworzy szkielet implementacja **OnInsertObject** w klasie widoku, który trzeba będzie wykonać.  
  
     Zobacz przykład MFC OLE [OCLIENT](../visual-cpp-samples.md) przykład pełną wykonania tego polecenia.  
  
-   Id_ole_edit_links — umożliwia edytowanie OLE łącza  
  
     `COleDocument`obsługuje polecenie za pomocą implementacji MFC — pod warunkiem standardowe okno dialogowe łącza OLE. Implementacja tego okna dialogowego jest dostępny za pośrednictwem `COleLinksDialog` klasy. Jeśli bieżący dokument nie zawiera żadnych łączy, polecenie jest wyłączone.  
  
     Nie zaleca się Dostosowywanie programu obsługi poleceń.  
  
-   ID_OLE_VERB_FIRST —... OSTATNI zakres Identyfikatora dla zleceń OLE  
  
     `COleDocument`używa tego zakresu identyfikator polecenia obsługiwane przez aktualnie zaznaczony element OLE/obiekt. Musi to być zakresu, ponieważ danego typu elementu/obiektu OLE może obsługiwać zero lub więcej poleceń niestandardowych. W menu aplikacji powinien mieć jeden element menu o identyfikatorze **id_ole_verb_first —**. Gdy program jest uruchamiany, menu zostanie zaktualizowany z menu odpowiednie zlecenie opis (lub menu podręczne z wielu zleceń). Zarządzanie OLE menu jest obsługiwany przez `AfxOleSetEditMenu`, gotowe programu obsługi aktualizacji poleceń interfejsu użytkownika dla tego polecenia.  
  
     Nie ma żadnych programów obsługi jawnego polecenia obsługi każdego identyfikatora polecenia, w tym zakresie. **COleDocument::OnCmdMsg** zostanie zastąpiona w celu namierzania wszystkie identyfikatory poleceń w tym zakresie, przekształcić numery zlecenie liczony od zera i uruchomić serwera dla tego zlecenia (przy użyciu `COleClientItem::DoVerb`).  
  
     Dostosowanie lub innego korzystania z tego zakresu identyfikator polecenia jest niezalecane.  
  
-   Id_view_toolbar — Włącza lub wyłącza pasek narzędzi i wyłącza  
  
     `CFrameWnd`obsługuje tego polecenia i obsługi interfejsu użytkownika polecenia update, aby przełączyć widoczny stan paska narzędzi. Pasek narzędzi musi być oknem podrzędnym ramki o identyfikatorze okna podrzędnego `AFX_IDW_TOOLBAR`. Program obsługi poleceń faktycznie przełącza widoczność, okna narzędzi. `CFrameWnd::RecalcLayout`Służy do ponownie narysować okno ramowe z paska narzędzi w jego nowego stanu. Polecenie aktualizacji obsługi interfejsu użytkownika sprawdza element menu, gdy jest on widoczny.  
  
     Nie zaleca się Dostosowywanie programu obsługi poleceń. Jeśli chcesz dodać dodatkowe paski narzędzi, można sklonować i modyfikować program obsługi poleceń i polecenia update obsługi interfejsu użytkownika dla tego polecenia.  
  
-   Id_view_status_bar — Włącza lub wyłącza pasek stanu i wyłącza  
  
     To polecenie jest zaimplementowana w `CFrameWnd` podobnie jak **id_view_toolbar —**, z wyjątkiem Identyfikatora obiektu podrzędnego innego okna (**AFX_IDW_STATUS_BAR**) jest używany.  
  
## <a name="update-only-command-handlers"></a>Programy obsługi poleceń tylko do aktualizacji  
 Identyfikatory poleceń standardowych kilka są używane jako wskaźników na paskach stanu. Te używać tego samego interfejsu użytkownika polecenia update mechanizmu obsługi można wyświetlić ich bieżącego stanu wizualnego w czasie bezczynności aplikacji. Ponieważ nie może być wybrany przez użytkownika (to znaczy, że nie można wypchnąć okienku paska stanu), a następnie nie ma sensu mają `ON_COMMAND` obsługi dla tych identyfikatorów poleceń.  
  
-   **Id_indicator_caps —** : zakończenie blokady wskaźnika.  
  
-   **Id_indicator_num —** : NUM blokady wskaźnika.  
  
-   **Id_indicator_scrl —** : SCRL wskaźnik.  
  
-   **Id_indicator_kana —** : KANA wskaźnik (dotyczy tylko systemów japoński).  
  
 Wszystkie trzy te są wykonywane w **CFrameWnd::OnUpdateKeyIndicator**, pomocnika wdrożenia, który używa Identyfikatora polecenia do mapowania na odpowiedni klucz wirtualny. Najczęstszą implementacją Włącza lub wyłącza (dla okienka stanu wyłączone = Brak tekstu) `CCmdUI` obiektu, w zależności od tego, czy odpowiedni klucz wirtualny jest obecnie zablokowany.  
  
 Nie zaleca się Dostosowywanie programu obsługi poleceń.  
  
-   **Id_indicator_ext —: EXT**zakończone wybór wskaźnika.  
  
-   **Id_indicator_ovr —: OV**e**R**znalezienia wskaźnika.  
  
-   **Id_indicator_rec —: REC**ording wskaźnika.  
  
 Obecnie nie istnieje żadne standardowej implementacji dla tych wskaźników.  
  
 Jeśli wybierzesz do wdrożenia tych wskaźników, zalecane jest użycie tych identyfikatorów wskaźnik i utrzymywanie kolejność wskaźniki na pasku stanu (to znaczy w następującej kolejności: EXT, centralnych zasad dostępu, NUM, SCRL, zas, zAL.).  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

