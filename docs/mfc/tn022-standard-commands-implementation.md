---
title: 'TN022: Implementacja poleceń standardowych'
ms.date: 11/04/2016
f1_keywords:
- vc.commands
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
ms.openlocfilehash: 8d568760cc75a4c1f2ddb6dd88108cc830783194
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775834"
---
# <a name="tn022-standard-commands-implementation"></a>TN022: Implementacja poleceń standardowych

> [!NOTE]
>  Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga opisuje implementacji poleceń standardowych dostarczonych przez MFC w wersji 2.0. Odczyt [techniczne 21 Uwaga](../mfc/tn021-command-and-message-routing.md) pierwszy ponieważ opisuje mechanizm używany do implementowania wiele standardowych poleceń.

Założono znajomość architektury, interfejsów API i powszechną praktyką programowania MFC. Udokumentowane, jak również nieudokumentowane "implementację tylko" interfejsy API są opisane. Nie jest miejscem do rozpoczęcia, informacje o funkcji lub jak program w MFC. Odnoszą się do Visual C++, aby uzyskać ogólne informacje i szczegóły udokumentowanych interfejsów API.

## <a name="the-problem"></a>Ten Problem

MFC definiuje wiele identyfikatory poleceń standardowych w pliku nagłówkowym AFXRES. H. Różni się w ramach obsługi tych poleceń. Omówienie, gdzie i jak z klas w ramach obsługi tych poleceń nie tylko umożliwi wyświetlenie możesz jak struktura wewnętrznie działa, ale zawierają przydatne informacje na temat sposobu dostosowywania standardowe wdrożenia i nauczą Cię kilka technik w celu wykonania własne programy obsługi poleceń.

## <a name="contents-of-this-technical-note"></a>Zawartość to Uwaga techniczna

Każdy identyfikator polecenia został opisany w dwie sekcje:

- Tytuł: nazwy symbolicznej identyfikator polecenia (na przykład id_file_save —) następuje celem polecenia (na przykład "zapisuje bieżący dokument"), rozdzielone średnikiem.

- Akapitach opisujące klas, które implementuje polecenie i co to jest domyślna implementacja

Większość implementacji polecenie domyślne są prewired w mapie komunikatów klasy podstawowej struktury. Brak implementacji niektóre polecenia, które wymaga jawnego okablowania w klasie pochodnej. Te ustawienia zostały opisane w obszarze "Note". W przypadku wybrania opcji odpowiednie w AppWizard te domyślne programy obsługi zostaną połączone automatycznie wygenerowany szkielet aplikacji.

## <a name="naming-convention"></a>Konwencje nazewnictwa

Standardowe polecenia wykonaj proste konwencji nazewnictwa, która firma Microsoft zaleca, że używasz, jeśli jest to możliwe. Większość standardowych poleceń znajdują się w standarowych miejsc, w pasku menu aplikacji. Nazwa symboliczna polecenia rozpoczyna się od "ID_", po której następuje nazwa standardowe menu podręcznego następuje nazwa elementu menu. Nazwa symboliczna jest pisany wielkimi literami z dzielenie wyrazów podkreślenia. Dla polecenia, które nie mają nazwy elementów menu standardowego nazwę logiczną polecenia zdefiniowano, począwszy od "ID_" (na przykład id_next_pane —).

Prefiks "ID_" Firma Microsoft służy do wskazywania poleceń, które mają być powiązane z elementami menu, przyciski paska narzędzi lub innych obiektów interfejsu użytkownika polecenia. Obsługa poleceń "ID_" programy obsługi poleceń należy używać mechanizmy ON_COMMAND i ON_UPDATE_COMMAND_UI architektury polecenia MFC.

Zaleca się, że używasz niestandardowym prefiksie "IDM_" dla elementów menu, postępuj zgodnie z architektury polecenia i należy kodu specyficznego dla menu pozwala włączać i wyłączać je. Oczywiście liczba określonych poleceń menu powinien być mały, ponieważ następujące architektury polecenia MFC nie tylko sprawia, że programy obsługi poleceń bardziej zaawansowanych (ponieważ będą one działać z paskami narzędzi), ale sprawia, że kod procedury obsługi poleceń do wielokrotnego użytku.

## <a name="id-ranges"></a>Identyfikator zakresów

Zapoznaj się [Uwagi techniczne 20](../mfc/tn020-id-naming-and-numbering-conventions.md) uzyskać więcej informacji dotyczących użycia zakresów identyfikator w MFC.

Polecenia standardowe MFC należy do zakresu 0xE000 do 0xEFFF. Proszę nie należy polegać na konkretne wartości tych identyfikatorów ponieważ są one ulec zmianie w przyszłych wersjach biblioteki.

Aplikację należy zdefiniować polecenia w zakresie 0x8000 do 0xDFFF.

## <a name="standard-command-ids"></a>Identyfikatory poleceń standardowych

Dla każdego Identyfikatora polecenia występuje ciąg monitu standardową wiadomość wiersza, który można znaleźć w pliku MONITAMI. RC. Identyfikator ciągu dla tego monitu menu musi być taka sama, jak w przypadku identyfikatora polecenia.

- Id_file_new — tworzy dokument nowych lub być pusty.

    > [!NOTE]
    >  Musisz połączyć ten element, aby Twoje `CWinApp`-pochodne mapy komunikatów klasy, aby włączyć tę funkcję.

   `CWinApp::OnFileNew` implementuje polecenie to inaczej w zależności od liczby szablonów dokumentów w aplikacji. Jeśli istnieje tylko jedna `CDocTemplate`, `CWinApp::OnFileNew` utworzy nowy dokument tego typu, a także odpowiednią klasą ramki i widoku.

   Jeśli istnieje więcej niż jedna `CDocTemplate`, `CWinApp::OnFileNew` będzie monitować użytkownika przy użyciu okna dialogowego (AFX_IDD_NEWTYPEDLG) pozwalając im na wybranie typu do użycia dokumentu. Wybrane `CDocTemplate` służy do tworzenia dokumentu.

   Jednej wspólnej dostosowywania id_file_new — jest zapewnienie innym i większy wybór graficzny typów dokumentów. W takim przypadku można implementować własne `CMyApp::OnFileNew` i umieścić go na mapie komunikatów zamiast `CWinApp::OnFileNew`. Nie ma potrzeby wywoływały implementację klasy bazowej.

   Inny wspólnej dostosowywania id_file_new — ma na celu dostarczenie osobne polecenie tworzenia dokumentu każdego typu. W takim przypadku należy zdefiniować nowe polecenie identyfikatorów, na przykład ID_FILE_NEW_CHART i ID_FILE_NEW_SHEET.

- Id_file_open — otwiera istniejący dokument.

    > [!NOTE]
    >  Musisz połączyć ten element, aby Twoje `CWinApp`-pochodne mapy komunikatów klasy, aby włączyć tę funkcję.

   `CWinApp::OnFileOpen` jest bardzo prosta implementacja wywołania metody `CWinApp::DoPromptFileName` następuje `CWinApp::OpenDocumentFile` nazwą pliku lub ścieżki pliku, aby otworzyć. `CWinApp` Procedura implementacji `DoPromptFileName` Wyświetla standardowe okno dialogowe FileOpen i wypełnia je z rozszerzeniami, uzyskanego z bieżącym szablonów dokumentów.

   Jednej wspólnej dostosowywania id_file_open — jest dostosować okna dialogowego FileOpen lub dodać dodatkowy plik filtrów. Zalecanym sposobem dostosować jest zastąpić domyślną implementację własne FileOpen okien dialogowych i wywołania `CWinApp::OpenDocumentFile` o nazwie pliku lub ścieżki dokumentu. Nie ma potrzeby wywołać klasy bazowej.

- Id_file_close — powoduje zamknięcie aktualnie otwartego dokumentu.

   `CDocument::OnFileClose` wywołania `CDocument::SaveModified` monit, aby zapisać dokument, jeśli został zmodyfikowany, a następnie wywołuje `OnCloseDocument`. Całą logikę zamknięcia, w tym zniszczenie dokumentu, odbywa się w `OnCloseDocument` procedury.

    > [!NOTE]
    >  Id_file_close — działa inaczej niż komunikat WM_CLOSE SC_CLOSE system polecenie lub wysyłane do okna ramki dokumentów. Zamknięcie okna Zamknij dokument tylko wtedy, gdy to okno ramowe ostatniego przedstawiający dokumentu. Zamykanie dokumentu za pomocą id_file_close — tylko nie zostanie zamknięte dokument, ale spowoduje zamknięcie wszystkich okien ramowych dokumentu wyświetlane w dół.

- Id_file_save — zapisuje bieżący dokument.

   W implementacji użyto procedury Pomocnika `CDocument::DoSave` używanej dla obu `OnFileSave` i `OnFileSaveAs`. Po zapisaniu dokumentu, które nie zostały zapisane przed (oznacza to, że nie ma nazwę ścieżki, jak w przypadku nowy plik) lub które zostały odczytane z dokumentem tylko do odczytu `OnFileSave` logiki będzie działać, takie jak id_file_save_as — polecenie i poprosić użytkownika o podanie nowej nazwy pliku . Rzeczywisty proces otwierania pliku i wykonując zapisywania odbywa się za pośrednictwem funkcji wirtualnej `OnSaveDocument`.

   Istnieją dwie typowe przyczyny, aby dostosować id_file_save —. W przypadku dokumentów, które nie zapisuj po prostu usunąć polecenia id_file_save — elementy menu i przycisków paska narzędzi z poziomu interfejsu użytkownika. Pamiętaj również, nigdy nie zakłóconych dokumentu (oznacza to, że nigdy nie wywołują metody `CDocument::SetModifiedFlag`) i struktura nigdy nie spowodują dokumentu do zapisania. W przypadku dokumentów, które zapisują do wiadomo gdzie innego niż plik dysku należy zdefiniować nowe polecenia dla tej operacji.

   W przypadku właściwości `COleServerDoc`, id_file_save — jest używana zarówno dla zapisu pliku (w przypadku normalnych dokumenty), jak i aktualizacja pliku (w przypadku osadzone dokumenty).

   Jeśli dane dokumentu są przechowywane w plikach poszczególnych dysków, ale nie chcesz użyć domyślnej `CDocument` implementację serializacji, należy zastąpić `CDocument::OnSaveDocument` zamiast `OnFileSave`.

- Id_file_save_as — zapisuje bieżący dokument pod inną nazwą pliku.

   `CDocument::OnFileSaveAs` Implementacja używa tych samych `CDocument::DoSave` procedury pomocnika jako `OnFileSave`. `OnFileSaveAs` Polecenia odbywa się podobnie jak id_file_save —, jeśli brak nazwy pliku przed zapisywania dokumentów. `COleServerDoc::OnFileSaveAs` implementuje logikę, aby zapisać plik danych zwykłego dokumentu lub można zapisać dokumentu serwera, reprezentująca obiekt OLE osadzona w innej aplikacji w oddzielnym pliku.

   W przypadku dostosowania logikę id_file_save — będzie prawdopodobnie chcesz dostosować id_file_save_as — w podobny sposób, lub operacji "Zapisz jako" mogą nie mieć zastosowania do dokumentu. Jeśli nie jest potrzebna, można usunąć element menu na pasku menu.

- Id_file_save_copy_as — zapisuje bieżący dokument pod nową nazwą.

   `COleServerDoc::OnFileSaveCopyAs` Implementacja jest bardzo podobne do `CDocument::OnFileSaveAs`, z tą różnicą, że obiekt dokumentu nie jest "dołączony" do pliku podstawowego po zapisu. Oznacza to jeśli w pamięci "modyfikacji dokumentu" przed zapisywania, jest on nadal "zmodyfikowany". Ponadto to polecenie nie ma wpływu na nazwę ścieżki lub tytuł przechowywany w dokumencie.

- Id_file_update — powiadamia kontener, aby zapisać osadzonego dokumentu.

   `COleServerDoc::OnUpdateDocument` Wdrożenia po prostu notifiies kontenera, w którym mają być zapisywane osadzania. Kontener wywołuje odpowiednie OLE interfejsów API w celu zapisania osadzonego obiektu.

- Id_file_page_setup — wywołuje ono oknem dialogowym instalacji/układu strony specyficzne dla aplikacji.

   Obecnie nie istnieje dla tego okna dialogowego standard, a struktura nie ma domyślnej implementacji tego polecenia.

   Jeśli wybierzesz do zaimplementowania tego polecenia, zaleca się używać tego identyfikatora polecenia.

- Id_file_print_setup — Wywołaj standardowe okno dialogowe Ustawienia wydruku.

    > [!NOTE]
    >  Musisz połączyć ten element, aby Twoje `CWinApp`-pochodne mapy komunikatów klasy, aby włączyć tę funkcję.

   To polecenie wywołuje okno dialogowe Ustawienia wydruku standardowe, które umożliwia użytkownikowi dostosowywanie drukarki i wydruku ustawienia dla co najmniej ten dokument lub co najwyżej wszystkie dokumenty w tej aplikacji. Aby zmienić domyślne ustawienia drukarek dla całego systemu, należy użyć Panelu sterowania.

   `CWinApp::OnFilePrintSetup` jest bardzo prosta implementacja tworzenia `CPrintDialog` obiektu i wywoływania `CWinApp::DoPrintDialog` implementację funkcji. Spowoduje to ustawienia drukarki domyślnej aplikacji.

   Typowe potrzeby Dostosowywanie to polecenie jest umożliwiające ustawienia drukarki poszczególnych dokumentów, które powinny być przechowywane z podczas zapisywania dokumentu. W tym celu należy dodać program obsługi mapę komunikatów w swojej `CDocument` klasy, która tworzy `CPrintDialog` obiektów, inicjuje go za pomocą atrybutów odpowiednie drukarki (zazwyczaj *pole hDevMode* i *hDevNames*), wywołaj `CPrintDialog::DoModal`i Zapisz ustawienia drukarki zmienione. Niezawodne wdrożenia, należy rozważyć implementację `CWinApp::DoPrintDialog` wykrywania błędów i `CWinApp::UpdatePrinterSelection` zajmujących się rozsądne wartości domyślne i śledzenie zmian drukarki całego systemu.

- Id_file_print — standardowa drukowania bieżącego dokumentu

    > [!NOTE]
    >  Musisz połączyć ten element, aby Twoje `CView`-pochodne mapy komunikatów klasy, aby włączyć tę funkcję.

   To polecenie wyświetla bieżący dokument lub dokładniej rozpoczyna się proces drukowania, który obejmuje wywoływanie standardowe okno dialogowe drukowania i uruchomiony aparat drukowania.

   `CView::OnFilePrint` implementuje tego polecenia, a główna pętla drukowania. Wywołuje metodę wirtualną `CView::OnPreparePrinting` monit użytkownika za pomocą okna dialogowego drukowania. Następnie przygotowuje dane wyjściowe kontrolera domeny, aby przejść do drukarki, wyświetla okno dialogowe postępu drukowania (AFX_IDD_PRINTDLG) i wysyła `StartDoc` ucieczki do drukarki. `CView::OnFilePrint` zawiera także główna pętla drukowania podziału na strony. Dla każdej strony wywoływanych przez nią wirtualnego `CView::OnPrepareDC` następuje `StartPage` ucieczki i wywoływać metodę wirtualną `CView::OnPrint` dla tej strony. Po zakończeniu, wirtualnego `CView::OnEndPrinting` jest wywoływana, i drukowania okno dialogowe postępu jest zamknięty.

   Architektura drukowania MFC jest przeznaczony do podłączania na wiele różnych sposobów, aby uzyskać drukowania i podglądu wydruku. Zwykle znajdują się różne `CView` funkcje z możliwością zastąpienia odpowiednia dla wszystkich zadań drukowania podziału na strony. Tylko w przypadku aplikacji, która używa drukarki-stronicowa zorientowane na obiekty w danych wyjściowych należy można znaleźć trzeba zastąpić implementację ID_FILE_PRINT.

- Wprowadź id_file_print_preview — tryb podglądu wydruku dla bieżącego dokumentu.

    > [!NOTE]
    >  Musisz połączyć ten element, aby Twoje `CView`-pochodne mapy komunikatów klasy, aby włączyć tę funkcję.

   `CView::OnFilePrintPreview` Uruchamia tryb podglądu wydruku przez wywołanie funkcji pomocnika udokumentowanego `CView::DoPrintPreview`. `CView::DoPrintPreview` jest głównego aparatu dla pętli podglądu wydruku, podobnie jak `OnFilePrint` jest aparat głównego drukowania pętli for.

   Operacja podglądu wydruku można dostosować w na różne sposoby, przekazując różnymi parametrami, aby `DoPrintPreview`. Zapoznaj się [techniczne 30 Uwaga](../mfc/tn030-customizing-printing-and-print-preview.md), który w tym artykule omówiono niektóre szczegóły podglądu wydruku i sposobami ich dostosowywania.

- ID_FILE_MRU_FILE1... FILE16 Zakres identyfikatorów poleceń do listy ostatnio używanych plików **listy**.

   `CWinApp::OnUpdateRecentFileMenu` jest aktualizacji program obsługi interfejsu użytkownika poleceń, który jest jednym z bardziej zaawansowanych używa mechanizmu ON_UPDATE_COMMAND_UI. W swoim zasobie menu pojedynczy element menu muszą definiować tylko przy użyciu Identyfikatora ID_FILE_MRU_FILE1. Ten element menu będzie początkowo wyłączone.

   Jako Przypinać w lista rośnie, więcej menu, które elementy są dodawane do listy. Standardowa `CWinApp` implementacji wartość domyślna to standardowa limit czterech ostatnio używanych plików. Domyślne można zmienić, wywołując `CWinApp::LoadStdProfileSettings` wartością większy lub mniejszy. Listy są przechowywane w aplikacji. Pliku INI. Lista jest załadowana w aplikacji `InitInstance` działać, jeśli wywołujesz `LoadStdProfileSettings`i jest zapisywana, gdy aplikacja zakończy działanie. Program obsługi interfejsu użytkownika poleceń update MRU również przekonwertuje ścieżek bezwzględnych ścieżek względnych w celu wyświetlenia menu Plik.

   `CWinApp::OnOpenRecentFile` jest program obsługi ON_COMMAND, który przeprowadza rzeczywiste polecenia. Po prostu pobiera nazwę pliku na liście MRU i wywołania `CWinApp::OpenDocumentFile`, który wykonuje całą pracę, otwierając plik i aktualizowanie listy ostatnio używanych elementów.

   Nie zaleca się dostosowanie ten program obsługi poleceń.

- Id_edit_clear — usuwa bieżące zaznaczenie

   Obecnie nie ma żadnych standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdej `CView`-klasy pochodnej.

   `CEditView` udostępnia implementację użycia tego polecenia `CEdit::Clear`. Polecenie jest wyłączona, jeśli nie ma bieżącego zaznaczenia.

   Jeśli wybierzesz do zaimplementowania tego polecenia, zaleca się używać tego identyfikatora polecenia.

- Id_edit_clear_all — usuwa cały dokument.

   Obecnie nie ma żadnych standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdej `CView`-klasy pochodnej.

   Jeśli wybierzesz do zaimplementowania tego polecenia, zaleca się używać tego identyfikatora polecenia. Zobacz przykładowy samouczek MFC [BAZGROŁY](../overview/visual-cpp-samples.md) związanych z implementacją przykładu.

- Id_edit_copy — kopiuje bieżące zaznaczenie do Schowka.

   Obecnie nie ma żadnych standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdej `CView`-klasy pochodnej.

   `CEditView` udostępnia implementację tego polecenia, która kopiuje aktualnie zaznaczonego tekstu do Schowka, używając CF_TEXT `CEdit::Copy`. Polecenie jest wyłączona, jeśli nie ma bieżącego zaznaczenia.

   Jeśli wybierzesz do zaimplementowania tego polecenia, zaleca się używać tego identyfikatora polecenia.

- Id_edit_cut — obniża bieżące zaznaczenie do Schowka.

   Obecnie nie ma żadnych standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdej `CView`-klasy pochodnej.

   `CEditView` dostarcza implementację tego polecenia, która skraca aktualnie zaznaczonego tekstu do Schowka, używając CF_TEXT `CEdit::Cut`. Polecenie jest wyłączona, jeśli nie ma bieżącego zaznaczenia.

   Jeśli wybierzesz do zaimplementowania tego polecenia, zaleca się używać tego identyfikatora polecenia.

- Id_edit_find — rozpoczyna się operacja wyszukiwania wyświetla okno dialogowe Znajdź niemodalne.

   Obecnie nie ma żadnych standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdej `CView`-klasy pochodnej.

   `CEditView` udostępnia implementację tego polecenia, która wywołuje funkcję pomocnika implementacji `OnEditFindReplace` i przechowywania poprzednich ustawień Znajdź/Zamień w zmiennych implementacji prywatnej. `CFindReplaceDialog` Klasa jest używana do zarządzania niemodalnego okna dialogowego do monitowania użytkownika.

   Jeśli wybierzesz do zaimplementowania tego polecenia, zaleca się używać tego identyfikatora polecenia.

- Id_edit_paste — Wstawia bieżącą zawartość Schowka.

   Obecnie nie ma żadnych standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdej `CView`-klasy pochodnej.

   `CEditView` udostępnia implementację tego polecenia, które kopiuje bieżące dane Schowka, zastępowanie za pomocą zaznaczony tekst `CEdit::Paste`. Polecenie jest wyłączona, jeśli ma nie **CF_TEXT** w Schowku.

   `COleClientDoc` po prostu udostępnia procedurę obsługi aktualizacji poleceń interfejsu użytkownika dla tego polecenia. Jeśli Schowek nie zawiera elementu/obiektu możliwego do osadzenia OLE, polecenia zostaną wyłączone. Odpowiedzialność za pisanie programu obsługi dla polecenia rzeczywistego celu rzeczywistego wklejania. Jeśli w aplikacji OLE również wkleić w innych formatach, należy podać własne aktualizacji interfejsu użytkownika program obsługi poleceń w dokumencie albo widoku (oznacza to, gdzieś przed `COleClientDoc` w routingu poleceń docelowy).

   Jeśli wybierzesz do zaimplementowania tego polecenia, zaleca się używać tego identyfikatora polecenia.

   W przypadku zastąpienia standardowej implementacji OLE, użyj `COleClientItem::CanPaste`.

- Id_edit_paste_link — wstawia link z bieżącą zawartość Schowka.

   Obecnie nie ma żadnych standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdej `CView`-klasy pochodnej.

   `COleDocument` po prostu udostępnia procedurę obsługi aktualizacji poleceń interfejsu użytkownika dla tego polecenia. Jeśli Schowek nie zawiera możliwym elementu/obiektu OLE, polecenia zostaną wyłączone. Odpowiedzialność za pisanie programu obsługi dla polecenia rzeczywistego celu rzeczywistego wklejania. Jeśli w aplikacji OLE również wkleić w innych formatach, należy podać własne aktualizacji interfejsu użytkownika program obsługi poleceń w dokumencie albo widoku (oznacza to, gdzieś przed `COleDocument` w routingu poleceń docelowy).

   Jeśli wybierzesz do zaimplementowania tego polecenia, zaleca się używać tego identyfikatora polecenia.

   W przypadku zastąpienia standardowej implementacji OLE, użyj `COleClientItem::CanPasteLink`.

- Id_edit_paste_special — Wstawia bieżącą zawartość Schowka z opcjami.

   Obecnie nie ma żadnych standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdej `CView`-klasy pochodnej. MFC nie zapewnia to okno dialogowe.

   Jeśli wybierzesz do zaimplementowania tego polecenia, zaleca się używać tego identyfikatora polecenia.

- Id_edit_repeat — powtarza ostatnią operację.

   Obecnie nie ma żadnych standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdej `CView`-klasy pochodnej.

   `CEditView` udostępnia implementację tego polecenia, aby powtórzyć ostatnią operację wyszukiwania. Zmienne implementacji prywatnej ostatnie wyszukiwanie są używane. Polecenie jest wyłączona, jeśli nie można podjąć próby Znajdź.

   Jeśli wybierzesz do zaimplementowania tego polecenia, zaleca się używać tego identyfikatora polecenia.

- Id_edit_replace — rozpoczyna się operacji zamieniania powoduje wyświetlenie Zastąp niemodalnego okna dialogowego.

   Obecnie nie ma żadnych standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdej `CView`-klasy pochodnej.

   `CEditView` udostępnia implementację tego polecenia, która wywołuje funkcję pomocnika implementacji `OnEditFindReplace` i przechowywania poprzednich ustawień Znajdź/Zamień w zmiennych implementacji prywatnej. `CFindReplaceDialog` Klasa jest używana do zarządzania niemodalnego okna dialogowego, który monituje użytkownika.

   Jeśli wybierzesz do zaimplementowania tego polecenia, zaleca się używać tego identyfikatora polecenia.

- Id_edit_select_all — zaznacza cały dokument.

   Obecnie nie ma żadnych standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdej `CView`-klasy pochodnej.

   `CEditView` udostępnia implementację tego polecenia, który wybiera cały tekst w dokumencie. Polecenie jest wyłączona, jeśli nie ma żadnego tekstu, aby wybrać.

   Jeśli wybierzesz do zaimplementowania tego polecenia, zaleca się używać tego identyfikatora polecenia.

- Id_edit_undo — Cofa ostatnią operację.

   Obecnie nie ma żadnych standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdej `CView`-klasy pochodnej.

   `CEditView` udostępnia implementację tego polecenia, za pomocą `CEdit::Undo`. Polecenie jest wyłączona, jeśli `CEdit::CanUndo` zwraca wartość FALSE.

   Jeśli wybierzesz do zaimplementowania tego polecenia, zaleca się używać tego identyfikatora polecenia.

- Id_edit_redo — wykonuje ponownie ostatnią operację.

   Obecnie nie ma żadnych standardowej implementacji dla tego polecenia. Musisz zaimplementować to dla każdej `CView`-klasy pochodnej.

   Jeśli wybierzesz do zaimplementowania tego polecenia, zaleca się używać tego identyfikatora polecenia.

- Id_window_new — Otwiera inne okno w aktywnym dokumencie.

   `CMDIFrameWnd::OnWindowNew` implementuje tej zaawansowanej funkcji przy użyciu szablonu dokumentu, bieżącego dokumentu w celu utworzenia innej ramki zawierający inny widok bieżącego dokumentu.

   Jak większość wielu dokumentów (MDI) interfejsu polecenia menu okna polecenie jest wyłączona, jeśli żadnego aktywnego okna podrzędnego MDI.

   Nie zaleca się dostosowanie ten program obsługi poleceń. Jeśli chcesz podać polecenie, które tworzy dodatkowe widoki lub okien ramowych prawdopodobnie będzie lepiej inventing własne polecenia. Można sklonować kodu z `CMDIFrameWnd::OnWindowNew` i zmodyfikuj go do określonych ramki i wyświetlanie klas swoich potrzeb.

- Id_window_arrange — Rozmieszcza ikony w dolnej części okna MDI.

   `CMDIFrameWnd` implementuje standardowe polecenie MDI w implementacji funkcji pomocnika `OnMDIWindowCmd`. Tego pomocnika mapuje identyfikatory poleceń komunikatów Windows MDI i w związku z tym można udostępniać duże ilości kodu.

   Podobnie jak większość polecenia menu okna MDI polecenie jest wyłączona, jeśli żadnego aktywnego okna podrzędnego MDI.

   Nie zaleca się dostosowanie ten program obsługi poleceń.

- Id_window_cascade — kaskady windows tak, aby się.

   `CMDIFrameWnd` implementuje standardowe polecenie MDI w implementacji funkcji pomocnika `OnMDIWindowCmd`. Tego pomocnika mapuje identyfikatory poleceń komunikatów Windows MDI i w związku z tym można udostępniać duże ilości kodu.

   Podobnie jak większość polecenia menu okna MDI polecenie jest wyłączona, jeśli żadnego aktywnego okna podrzędnego MDI.

   Nie zaleca się dostosowanie ten program obsługi poleceń.

- Kafelki id_window_tile_horz — windows poziomo.

   To polecenie jest zaimplementowana w `CMDIFrameWnd` podobnie jak w przypadku id_window_cascade —, z wyjątkiem inny komunikat Windows MDI jest używany dla tej operacji.

   Należy wybrać domyślną orientację kafelka aplikacji. Można to zrobić, zmieniając identyfikator elementu menu "Kafelka" okna id_window_tile_horz — lub id_window_tile_vert —.

- Id_window_tile_vert — Kafelki systemu windows w pionie.

   To polecenie jest zaimplementowana w `CMDIFrameWnd` podobnie jak w przypadku id_window_cascade —, z wyjątkiem inny komunikat Windows MDI jest używany dla tej operacji.

   Należy wybrać domyślną orientację kafelka aplikacji. Można to zrobić, zmieniając identyfikator elementu menu "Kafelka" okna id_window_tile_horz — lub id_window_tile_vert —.

- Id_window_split — klawiatura interfejs do podziału.

   `CView` to polecenie dla obsługuje `CSplitterWnd` implementacji. Jeśli widok jest częścią okno rozdzielacza, to polecenie będzie delegować do implementacji funkcji `CSplitterWnd::DoKeyboardSplit`. Spowoduje to umieszczenie rozdzielacza w trybie który umożliwi użytkownikom klawiatury w celu dzielenia lub cofnąć podziału okno rozdzielacza.

   To polecenie jest wyłączona, jeśli widok jest rozdzielacza.

   Nie zaleca się dostosowanie ten program obsługi poleceń.

- Id_app_about — wywołuje okno dialogowe informacje.

   Nie ma żadnych standardową implementację dla aplikacji o pola. Domyślna aplikacja utworzona przez AppWizard utworzy klasę niestandardowe okno dialogowe dla aplikacji i używać go jako użytkownika o polu. AppWizard również będzie zapisywać obsługi proste polecenia, który obsługuje tego polecenia, a następnie wywołuje okno dialogowe.

   To polecenie prawie zawsze będzie implementowany.

- Id_app_exit — Zamknij aplikację.

   `CWinApp::OnAppExit` obsługuje polecenie to, wysyłając komunikat WM_CLOSE do głównego okna aplikacji. Standardowa zamykanie aplikacji (monitowania o zmodyfikowane pliki i tak dalej) jest obsługiwany przez `CFrameWnd` implementacji.

   Nie zaleca się dostosowanie ten program obsługi poleceń. Zastępowanie `CWinApp::SaveAllModified` lub `CFrameWnd` zaleca się zamknięcie logiki.

   Jeśli wybierzesz do zaimplementowania tego polecenia, zaleca się używać tego identyfikatora polecenia.

- Wyświetla Pomoc id_help_index — tematy z. Plik HLP.

    > [!NOTE]
    >  Musisz połączyć ten element, aby Twoje `CWinApp`-pochodne mapy komunikatów klasy, aby włączyć tę funkcję.

   `CWinApp::OnHelpIndex` obsługuje polecenie przypadku wywołując `CWinApp::WinHelp`.

   Nie zaleca się dostosowanie ten program obsługi poleceń.

- Wyświetla id_help_using — pomoc na temat korzystania z pomocy.

    > [!NOTE]
    >  Musisz połączyć ten element, aby Twoje `CWinApp`-pochodne mapy komunikatów klasy, aby włączyć tę funkcję.

   `CWinApp::OnHelpUsing` obsługuje polecenie przypadku wywołując `CWinApp::WinHelp`.

   Nie zaleca się dostosowanie ten program obsługi poleceń.

- Id_context_help — wprowadza SHIFT-F1 Pomoc tryb.

    > [!NOTE]
    >  Musisz połączyć ten element, aby Twoje `CWinApp`-pochodne mapy komunikatów klasy, aby włączyć tę funkcję.

   `CWinApp::OnContextHelp` obsługuje tego polecenia, ustawiając kursor trybu pomocy, wprowadzając modalną pętle i Oczekiwanie na użytkownika wybrać okno, aby uzyskać pomoc dotyczącą. Zapoznaj się [Uwagi techniczne 28](../mfc/tn028-context-sensitive-help-support.md) dodatkowe szczegóły dotyczące implementacji MFC pomocy.

   Nie zaleca się dostosowanie ten program obsługi poleceń.

- Id_help — zapewnia pomoc w bieżącym kontekście

    > [!NOTE]
    >  Musisz połączyć ten element, aby Twoje `CWinApp`-pochodne mapy komunikatów klasy, aby włączyć tę funkcję.

   `CWinApp::OnHelp` obsługuje tego polecenia, uzyskując w kontekście pomocy odpowiednie dla bieżącego kontekstu aplikacji. Obsługuje prosty pomocy F1, pomoc na temat okna komunikatów i tak dalej. Zapoznaj się [Uwagi techniczne 28](../mfc/tn028-context-sensitive-help-support.md) dla implementacji zajmujących się szczegółowe informacje na temat MFC.

   Nie zaleca się dostosowanie ten program obsługi poleceń.

- Wyświetla id_default_help — pomoc domyślnego kontekstu

    > [!NOTE]
    >  Musisz połączyć ten element, aby Twoje `CWinApp`-pochodne mapy komunikatów klasy, aby włączyć tę funkcję.

   To polecenie zwykle będzie mapowany do `CWinApp::OnHelpIndex`.

   Obsługi innego polecenia można podać, jeśli pożądane jest różnica między domyślnymi pomocy i indeksu Pomocy.

- Id_next_pane — przechodzi do następnego okienka

   `CView` to polecenie dla obsługuje `CSplitterWnd` implementacji. Jeśli widok jest częścią okno rozdzielacza, to polecenie będzie delegować do implementacji funkcji `CSplitterWnd::OnNextPaneCmd`. Spowoduje to przeniesienie bieżącym widokiem do następnego okienka w rozdzielacza.

   To polecenie jest niedostępne, jeśli widok jest rozdzielacz lub dostępna jest nie następne okienko, aby przejść do.

   Nie zaleca się dostosowanie ten program obsługi poleceń.

- Id_prev_pane — przejście do poprzedniego okienka

   `CView` to polecenie dla obsługuje `CSplitterWnd` implementacji. Jeśli widok jest częścią okno rozdzielacza, to polecenie będzie delegować do implementacji funkcji `CSplitterWnd::OnNextPaneCmd`. Spowoduje to przeniesienie bieżącym widokiem do poprzedniego okienka w rozdzielacza.

   To polecenie jest niedostępne, jeśli widok jest rozdzielacz lub dostępna jest nie poprzedniego okienka, aby przejść do.

   Nie zaleca się dostosowanie ten program obsługi poleceń.

- Id_ole_insert_new — Wstawia nowy obiekt OLE

   Obecnie nie ma żadnych standardowej implementacji dla tego polecenia. Należy zaimplementować dla Twojego `CView`-klasy, aby wstawić nowy element OLE/obiekt na bieżącym zaznaczeniu.

   Wszystkie aplikacje klienckie OLE powinny implementować to polecenie. AppWizard, z opcją OLE, zostanie utworzony szkielet implementacji `OnInsertObject` w klasie widoku, który trzeba będzie wykonać.

   Zobacz przykładową MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) przykład pełną implementację tego polecenia.

- Id_ole_edit_links — edytuje OLE łącza

   `COleDocument` obsługuje polecenie przy użyciu implementacji MFC — pod warunkiem standardowe okno dialogowe łącza OLE. Implementacja tego okna dialogowego odbywa się za pośrednictwem `COleLinksDialog` klasy. Jeśli bieżący dokument nie zawiera żadnych linków, polecenie jest wyłączone.

   Nie zaleca się dostosowanie ten program obsługi poleceń.

- ID_OLE_VERB_FIRST —... OSTATNI zakres identyfikator dla zleceń OLE

   `COleDocument` używa tego zakresu identyfikator polecenia obsługiwane przez aktualnie zaznaczonego elementu OLE/obiektu. Musi być zakresem, ponieważ danego typu elementu/obiektu OLE może obsługiwać niestandardowych czasowników zero lub więcej. W menu aplikacji powinna mieć jeden element menu przy użyciu Identyfikatora id_ole_verb_first —. Gdy program jest uruchamiany, menu zostaną zaktualizowane przy użyciu menu odpowiednie zlecenie opis (lub menu podręcznego przy użyciu wielu poleceń). Zarządzanie OLE menu odbywa się przez `AfxOleSetEditMenu`, gotowe programu obsługi aktualizacji poleceń interfejsu użytkownika dla tego polecenia.

   Nie ma żadnych obsługi jawnego polecenia do obsługi każdego identyfikatora polecenia, w tym zakresie. `COleDocument::OnCmdMsg` zostanie zastąpiona w celu namierzania wszystkie identyfikatory poleceń, w tym zakresie, przekształcając numery zlecenie liczony od zera i uruchomić serwera dla tego zlecenia (przy użyciu `COleClientItem::DoVerb`).

   Dostosowywanie lub inne użycie tego polecenia identyfikator zakresu nie jest zalecane.

- Id_view_toolbar — Włącza lub wyłącza pasek narzędzi i wyłączanie

   `CFrameWnd` obsługuje polecenie i obsługi interfejsu użytkownika aktualizacji poleceń, aby przełączyć widoczny stan paska narzędzi. Musi być pasek narzędzi okna podrzędnego ramki za pomocą okna podrzędnego Identyfikatora AFX_IDW_TOOLBAR. Program obsługi poleceń faktycznie przełącza widoczność okna narzędzi. `CFrameWnd::RecalcLayout` Służy do ponownie narysować okno ramki za pomocą paska narzędzi w stanie nowe. Program obsługi interfejsu użytkownika aktualizacji sprawdza, czy element menu, gdy jest on widoczny.

   Nie zaleca się dostosowanie ten program obsługi poleceń. Jeśli chcesz dodać dodatkowe paski narzędzi, można sklonować, i zmodyfikuj program obsługi poleceń i polecenia update interfejsu użytkownika programu obsługi dla tego polecenia.

- Id_view_status_bar — Włącza lub wyłącza pasek stanu włączać i wyłączać

   To polecenie jest zaimplementowana w `CFrameWnd` podobnie jak id_view_toolbar —, z wyjątkiem okna podrzędnego inny identyfikator (AFX_IDW_STATUS_BAR) jest używany.

## <a name="update-only-command-handlers"></a>Programy obsługi poleceń w trybie tylko do aktualizacji

Identyfikatory poleceń standardowych kilka są używane jako wskaźniki na paskach stanu. Te używać tego samego interfejsu użytkownika aktualizacji poleceń mechanizm obsługi do wyświetlenia ich bieżącego stanu wizualnego w czasie bezczynności aplikacji. Ponieważ nie można wybrać przez użytkownika (oznacza to, że nie można wypchnąć w okienku paska stanu), a następnie nie ma sensu ma nieprawidłowego ON_COMMAND tych identyfikatorów poleceń.

- ID_INDICATOR_CAPS : Zakończenie blokady wskaźnik.

- ID_INDICATOR_NUM —: NUM lock wskaźnik.

- ID_INDICATOR_SCRL —: Wskaźnik blokady SCRL.

- ID_INDICATOR_KANA —: Znaki KANA zablokować wskaźnika (dotyczy tylko systemów japońskiego).

Wszystkie trzy z nich są implementowane w `CFrameWnd::OnUpdateKeyIndicator`, pomocnika wdrożenia, który używa Identyfikatora polecenia do mapowania na odpowiedni klucz wirtualnego. Najczęstszą implementacją Włącza lub wyłącza (dla okienka stanu wyłączone = Brak tekstu) `CCmdUI` obiekt, w zależności od tego, czy odpowiedni klucz wirtualnych jest zablokowana.

Nie zaleca się dostosowanie ten program obsługi poleceń.

- ID_INDICATOR_EXT —: Rozszerzone Wybierz wskaźnik.

- ID_INDICATOR_OVR —: Wskaźnik zastępowania.

- ID_INDICATOR_REC —: Wskaźnik rejestrowania.

Obecnie nie ma żadnych standardowej implementacji dla tych wskaźników.

Jeśli użytkownik chce zaimplementować te wskaźniki, zalecamy użycie tych identyfikatorów wskaźnika i utrzymywania porządkowanie wskaźników w pasku stanu (czyli w następującej kolejności: EXT, ZAKOŃCZENIA, LICZBA, SCRL, ZAS, "REC").

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
