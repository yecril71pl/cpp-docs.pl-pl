---
title: 'TN022: implementacja poleceń standardowych'
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
ms.openlocfilehash: 5c7041f40c7e30592f642d29d9d02812a9596864
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370394"
---
# <a name="tn022-standard-commands-implementation"></a>TN022: implementacja poleceń standardowych

> [!NOTE]
> Następująca uwaga techniczna nie została zaktualizowana, ponieważ została po raz pierwszy uwzględniona w dokumentacji online. W rezultacie niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zaleca się wyszukicie tematu interesującego w indeksie dokumentacji online.

W tej notatce opisano implementacje poleceń standardowych dostarczonych przez MFC 2.0. Przeczytaj [najpierw uwagę techniczną 21,](../mfc/tn021-command-and-message-routing.md) ponieważ opisano mechanizmy używane do implementacji wielu standardowych poleceń.

W tym opisie przyjęto znajomość architektury MFC, interfejsów API i typowej praktyki programowania. Opisane są udokumentowane, a także nieudokumentowane interfejsy API "tylko implementacja". To nie jest miejsce, aby rozpocząć naukę o funkcjach lub jak programować w MFC. Więcej ogólnych informacji można znaleźć w języku Visual C++, aby uzyskać szczegółowe informacje na temat udokumentowanych interfejsów API.

## <a name="the-problem"></a>The Problem

MFC definiuje wiele standardowych identyfikatorów poleceń w pliku nagłówkowym AFXRES. H. Obsługa struktury dla tych poleceń jest różna. Zrozumienie, gdzie i jak klasy struktury obsługiwać te polecenia nie tylko pokaże, jak struktura działa wewnętrznie, ale zapewni przydatne informacje na temat dostosowywania implementacji standardowych i nauczyć się kilka technik implementacji własnych programów obsługi poleceń.

## <a name="contents-of-this-technical-note"></a>Zawartość niniejszej noty technicznej

Identyfikator każdego polecenia jest opisany w dwóch sekcjach:

- Tytuł: symboliczna nazwa identyfikatora polecenia (na przykład ID_FILE_SAVE), po której następuje cel polecenia (na przykład "zapisuje bieżący dokument") oddzielony dwukropkiem.

- Jeden lub więcej akapitów opisujących, które klasy implementują polecenie i co robi domyślna implementacja

Większość domyślnych implementacji poleceń są wstępnie przewodzone w mapie komunikatu klasy podstawowej struktury. Istnieje kilka implementacji poleceń, które wymagają jawnego okablowania w klasie pochodnej. Są one opisane w "Uwaga". Jeśli wybierzesz odpowiednie opcje w AppWizard, te domyślne programy obsługi zostaną połączone dla Ciebie w wygenerowanej aplikacji szkieletu.

## <a name="naming-convention"></a>Konwencje nazewnictwa

Standardowe polecenia są zgodne z prostą konwencją nazewnictwa, której zalecamy użycie, jeśli to możliwe. Większość standardowych poleceń znajduje się w standardowych miejscach na pasku menu aplikacji. Nazwa symboliczna polecenia zaczyna się od "ID_", po którym następuje standardowa nazwa menu podręcznego, po której następuje nazwa elementu menu. Nazwa symboliczna jest w wielkich liter z podkreślenia word-breaks. W przypadku poleceń, które nie mają standardowych nazw elementów menu, nazwa polecenia logicznego jest definiowana zaczynając od "ID_" (na przykład ID_NEXT_PANE).

Używamy prefiksu "ID_", aby wskazać polecenia, które są przeznaczone do powiązanych z elementami menu, przyciskami paska narzędzi lub innymi obiektami interfejsu użytkownika polecenia. Programy obsługi poleceń obsługujące polecenia "ID_" powinny używać mechanizmów ON_COMMAND i ON_UPDATE_COMMAND_UI architektury poleceń MFC.

Zaleca się użycie standardowego prefiksu "IDM_" dla elementów menu, które nie są zgodne z architekturą poleceń i potrzebują kodu specyficznego dla menu, aby je włączyć i wyłączyć. Oczywiście liczba poleceń specyficznych dla menu powinna być mała, ponieważ podążanie za architekturą poleceń MFC nie tylko sprawia, że programy obsługi poleceń są bardziej wydajne (ponieważ będą pracować z paskami narzędzi), ale sprawia, że kod obsługi poleceń jest wielokrotnego pożycia.

## <a name="id-ranges"></a>Zakresy identyfikatorów

Więcej informacji na temat wykorzystania zakresów identyfikatorów w MFC można znaleźć w [notatce technicznej 20.](../mfc/tn020-id-naming-and-numbering-conventions.md)

Standardowe polecenia MFC mieszczą się w zakresie od 0xE000 do 0xEFFF. Nie należy polegać na określonych wartościach tych identyfikatorów, ponieważ mogą one ulec zmianie w przyszłych wersjach biblioteki.

Aplikacja powinna zdefiniować jego polecenia w zakresie od 0x8000 do 0xDFFF.

## <a name="standard-command-ids"></a>Standardowe identyfikatory poleceń

Dla każdego identyfikatora polecenia istnieje standardowy ciąg wiersza wiadomości, który można znaleźć w pliku PROMPTS. Rc. Identyfikator ciągu dla tego wiersza menu musi być taki sam, jak w przypadku identyfikatora polecenia.

- ID_FILE_NEW Tworzy nowy/pusty dokument.

    > [!NOTE]
    >  Należy połączyć to `CWinApp`z mapą komunikatów klasy pochodnej, aby włączyć tę funkcję.

   `CWinApp::OnFileNew`implementuje to polecenie w różny sposób w zależności od liczby szablonów dokumentów w aplikacji. Jeśli istnieje tylko `CDocTemplate` `CWinApp::OnFileNew` jeden , utworzy nowy dokument tego typu, a także właściwą klasę ramki i widoku.

   Jeśli istnieje więcej `CDocTemplate`niż `CWinApp::OnFileNew` jeden , poprosi użytkownika o okno dialogowe (AFX_IDD_NEWTYPEDLG), pozwalając mu wybrać typ dokumentu do użycia. Wybrana `CDocTemplate` opcja służy do tworzenia dokumentu.

   Jednym z typowych dostosowywania ID_FILE_NEW jest zapewnienie innego i bardziej graficznego wyboru typów dokumentów. W takim przypadku możesz `CMyApp::OnFileNew` zaimplementować swój własny `CWinApp::OnFileNew`i umieścić go na mapie wiadomości zamiast . Nie ma potrzeby wywoływania implementacji klasy podstawowej.

   Innym typowym dostosowaniem ID_FILE_NEW jest podanie osobnego polecenia do tworzenia dokumentu każdego typu. W takim przypadku należy zdefiniować nowe identyfikatory poleceń, na przykład ID_FILE_NEW_CHART i ID_FILE_NEW_SHEET.

- ID_FILE_OPEN Otwiera istniejący dokument.

    > [!NOTE]
    >  Należy połączyć to `CWinApp`z mapą komunikatów klasy pochodnej, aby włączyć tę funkcję.

   `CWinApp::OnFileOpen`ma bardzo prostą `CWinApp::DoPromptFileName` implementację `CWinApp::OpenDocumentFile` połączeń, po której następuje nazwa pliku lub ścieżki pliku do otwarcia. Procedura `CWinApp` `DoPromptFileName` implementacji wywołuje standardowe okno dialogowe FileOpen i wypełnia je rozszerzeniami plików uzyskanymi z bieżących szablonów dokumentów.

   Jednym z typowych dostosowywania ID_FILE_OPEN jest dostosowanie okna dialogowego FileOpen lub dodanie dodatkowych filtrów plików. Zalecanym sposobem dostosowania tej wartości jest zastąpienie domyślnej implementacji własnym `CWinApp::OpenDocumentFile` okańwem FileOpen i wywołanie nazwy pliku lub ścieżki dokumentu. Nie ma potrzeby wywoływania klasy podstawowej.

- ID_FILE_CLOSE Zamyka aktualnie otwarty dokument.

   `CDocument::OnFileClose`wywołania `CDocument::SaveModified` monitu o zapisanie dokumentu, jeśli został `OnCloseDocument`zmodyfikowany, a następnie wywołania . Cała logika zamykania, w tym niszczenie `OnCloseDocument` dokumentu, odbywa się w procedurze.

    > [!NOTE]
    >  ID_FILE_CLOSE działa inaczej niż wiadomość WM_CLOSE lub polecenie systemu SC_CLOSE wysłane do okna ramki dokumentów. Zamknięcie okna spowoduje zamknięcie dokumentu tylko wtedy, gdy jest to ostatnie okno ramki z dokumentem. Zamknięcie dokumentu ID_FILE_CLOSE nie tylko zamknie dokument, ale zamknie wszystkie okna ramek z dokumentem.

- ID_FILE_SAVE Zapisuje bieżący dokument.

   Implementacja używa procedury `CDocument::DoSave` pomocniczej, która `OnFileSave` `OnFileSaveAs`jest używana zarówno dla i . Jeśli zapiszesz dokument, który nie został wcześniej zapisany (to znaczy, że nie ma nazwy ścieżki, jak w przypadku FileNew) lub który został odczytany z dokumentu tylko do odczytu, `OnFileSave` logika będzie działać jak polecenie ID_FILE_SAVE_AS i poprosić użytkownika o podanie nowej nazwy pliku. Rzeczywisty proces otwierania pliku i zapisywania odbywa `OnSaveDocument`się za pośrednictwem funkcji wirtualnej .

   Istnieją dwa typowe powody, aby dostosować ID_FILE_SAVE. W przypadku dokumentów, które nie są zapisywane, po prostu usuń elementy menu ID_FILE_SAVE i przyciski paska narzędzi z interfejsu użytkownika. Upewnij się również, że nigdy nie zabrudzono dokumentu (czyli nigdy nie wywołujesz), `CDocument::SetModifiedFlag`a struktura nigdy nie spowoduje zapisania dokumentu. W przypadku dokumentów, które zapisują w innym miejscu niż plik dysku, należy zdefiniować nowe polecenie dla tej operacji.

   W przypadku `COleServerDoc`ID_FILE_SAVE jest używany zarówno do zapisywania plików (dla zwykłych dokumentów), jak i aktualizacji plików (w przypadku dokumentów osadzonych).

   Jeśli dane dokumentu są przechowywane w poszczególnych plikach dyskowych, `CDocument` ale nie chcesz używać `CDocument::OnSaveDocument` domyślnej `OnFileSave`implementacji serializacji, należy zastąpić zamiast programu .

- ID_FILE_SAVE_AS Zapisuje bieżący dokument pod inną nazwą pliku.

   Implementacja `CDocument::OnFileSaveAs` używa tej `CDocument::DoSave` samej `OnFileSave`procedury pomocnika, co . Polecenie `OnFileSaveAs` jest obsługiwane tak samo ID_FILE_SAVE, jeśli dokumenty nie miały nazwy pliku przed zapisaniem. `COleServerDoc::OnFileSaveAs`implementuje logikę, aby zapisać normalny plik danych dokumentu lub zapisać dokument serwera reprezentujący obiekt OLE osadzony w innej aplikacji jako oddzielny plik.

   Jeśli dostosujesz logikę ID_FILE_SAVE, prawdopodobnie będziesz chciał dostosować ID_FILE_SAVE_AS w podobny sposób lub działanie "Zapisz jako" może nie dotyczyć dokumentu. Możesz usunąć element menu z paska menu, jeśli nie jest potrzebny.

- ID_FILE_SAVE_COPY_AS Zapisuje kopię bieżącego dokumentu pod nową nazwą.

   Implementacja jest bardzo podobna `COleServerDoc::OnFileSaveCopyAs` do `CDocument::OnFileSaveAs`, z tą różnicą, że obiekt dokumentu nie jest "dołączony" do pliku źródłowego po zapisaniu. Oznacza to, że jeśli dokument w pamięci został "zmodyfikowany" przed zapisaniem, nadal jest "zmodyfikowany". Ponadto to polecenie nie ma wpływu na nazwę ścieżki lub tytuł przechowywane w dokumencie.

- ID_FILE_UPDATE Powiadamia kontener o zapisaniu osadzonego dokumentu.

   Implementacja `COleServerDoc::OnUpdateDocument` po prostu powiadamia kontenera, który należy zapisać osadzanie. Kontener następnie wywołuje odpowiednie interfejsy API OLE w celu zapisania obiektu osadzonego.

- ID_FILE_PAGE_SETUP Wywołuje okno dialogowe konfiguracji/układu strony specyficzne dla aplikacji.

   Obecnie nie ma standardu dla tego okna dialogowego, a struktura nie ma domyślnej implementacji tego polecenia.

   Jeśli zdecydujesz się zaimplementować to polecenie, zaleca się użycie tego identyfikatora polecenia.

- ID_FILE_PRINT_SETUP Wywołać standardowe okno dialogowe Ustawienia drukowania.

    > [!NOTE]
    >  Należy połączyć to `CWinApp`z mapą komunikatów klasy pochodnej, aby włączyć tę funkcję.

   To polecenie wywołuje standardowe okno dialogowe konfiguracji drukowania, które umożliwia użytkownikowi dostosowanie ustawień drukarki i drukowania dla co najmniej tego dokumentu lub co najwyżej wszystkich dokumentów w tej aplikacji. Aby zmienić domyślne ustawienia drukarki dla całego systemu, należy użyć Panelu sterowania.

   `CWinApp::OnFilePrintSetup`ma bardzo prostą implementację `CPrintDialog` tworzącą `CWinApp::DoPrintDialog` obiekt i wywołującą funkcję implementacji. Spowoduje to ustawienie domyślnej konfiguracji drukarki aplikacji.

   Powszechną potrzebą dostosowania tego polecenia jest umożliwienie ustawień drukarki dla dokumentu, które powinny być przechowywane wraz z dokumentem po zapisaniu. Aby to zrobić, należy dodać program `CDocument` obsługi mapy `CPrintDialog` wiadomości w klasie, która tworzy obiekt, inicjuje go z odpowiednimi atrybutami `CPrintDialog::DoModal`drukarki (zwykle *hDevMode* i *hDevNames*), wywołać , i zapisać zmienione ustawienia drukarki. Aby uzyskać niezawodną implementację, należy `CWinApp::DoPrintDialog` przyjrzeć się `CWinApp::UpdatePrinterSelection` implementacji wykrywania błędów i radzenia sobie z rozsądnymi ustawieniami domyślnymi i śledzeniem zmian w drukarce w całym systemie.

- ID_FILE_PRINT Standardowe drukowanie bieżącego dokumentu

    > [!NOTE]
    >  Należy połączyć to `CView`z mapą komunikatów klasy pochodnej, aby włączyć tę funkcję.

   To polecenie drukuje bieżący dokument lub bardziej poprawnie uruchamia proces drukowania, który polega na wywołaniu standardowego okna dialogowego drukowania i uruchomieniu aparatu drukowania.

   `CView::OnFilePrint`implementuje to polecenie i główną pętlę drukowania. Wywołuje wirtualny `CView::OnPreparePrinting` monit użytkownika z okna dialogowego drukowania. Następnie przygotowuje wyjściowy kontroler domeny, aby przejść do drukarki, wywołuje okno dialogowe `StartDoc` postępu drukowania (AFX_IDD_PRINTDLG) i wysyła ucieczkę do drukarki. `CView::OnFilePrint`zawiera również główną pętlę drukowania zorientowaną na stronę główną. Dla każdej strony wywołuje `CView::OnPrepareDC` wirtualne, `StartPage` a następnie `CView::OnPrint` ucieczki i wywołanie wirtualne dla tej strony. Po zakończeniu wywoływana jest wirtualna, `CView::OnEndPrinting` a okno dialogowe postępu drukowania zostanie zamknięte.

   Architektura drukowania MFC została zaprojektowana do podłączania na wiele różnych sposobów do drukowania i podglądu wydruku. Zwykle można znaleźć różne `CView` zastępowalne funkcje odpowiednie dla wszystkich zadań drukowania zorientowanych na stronę. Tylko w przypadku aplikacji, która używa drukarki do wyjścia nieoponsywnego strony, należy znaleźć potrzebę zastąpienia implementacji ID_FILE_PRINT.

- ID_FILE_PRINT_PREVIEW Wprowadź tryb podglądu wydruku dla bieżącego dokumentu.

    > [!NOTE]
    >  Należy połączyć to `CView`z mapą komunikatów klasy pochodnej, aby włączyć tę funkcję.

   `CView::OnFilePrintPreview`uruchamia tryb podglądu wydruku, wywołując funkcję `CView::DoPrintPreview`udokumentowanego pomocnika . `CView::DoPrintPreview`jest głównym silnikiem pętli podglądu `OnFilePrint` wydruku, podobnie jak główny silnik pętli drukowania.

   Operację podglądu wydruku można dostosować na wiele sposobów, `DoPrintPreview`przekazując różne parametry do . Zapoznaj się [z notą techniczną 30,](../mfc/tn030-customizing-printing-and-print-preview.md)która omawia niektóre szczegóły podglądu wydruku i jak ją dostosować.

- ID_FILE_MRU_FILE1... PLIK16 Zakres identyfikatorów poleceń dla **listy**Mru pliku .

   `CWinApp::OnUpdateRecentFileMenu`jest program obsługi interfejsu użytkownika polecenia aktualizacji, który jest jednym z bardziej zaawansowanych zastosowań mechanizmu ON_UPDATE_COMMAND_UI. W zasobie menu wystarczy zdefiniować tylko jeden element menu o identyfikatorze ID_FILE_MRU_FILE1. Ten element menu pozostaje początkowo wyłączony.

   Wraz z rozwojem listy MRU do listy dodawane są kolejne elementy menu. Standardowa `CWinApp` implementacja domyślnie wynosi standardowy limit czterech ostatnio używanych plików. Wartość domyślną można `CWinApp::LoadStdProfileSettings` zmienić, wywołując z większą lub mniejszą wartością. Lista MRU jest przechowywana w aplikacji . ini. Lista jest ładowana w `InitInstance` funkcji aplikacji, jeśli wywołasz `LoadStdProfileSettings`program , i jest zapisywana po zamknięciu aplikacji. Program obsługi interfejsu użytkownika polecenia aktualizacji MRU konwertuje również ścieżki bezwzględne na ścieżki względne do wyświetlenia w menu pliku.

   `CWinApp::OnOpenRecentFile`jest ON_COMMAND program obsługi, który wykonuje rzeczywiste polecenie. Po prostu pobiera nazwę pliku z listy `CWinApp::OpenDocumentFile`MRU i wywołuje , co wykonuje całą pracę nad otwarciem pliku i aktualizacją listy MRU.

   Dostosowanie tego programu obsługi poleceń nie jest zalecane.

- ID_EDIT_CLEAR Czyści bieżący wybór

   Obecnie nie ma standardowej implementacji dla tego polecenia. Należy zaimplementować to dla każdej `CView`klasy pochodnej.

   `CEditView`zapewnia implementację tego `CEdit::Clear`polecenia za pomocą programu . Polecenie jest wyłączone, jeśli nie ma bieżącego zaznaczenia.

   Jeśli zdecydujesz się zaimplementować to polecenie, zaleca się użycie tego identyfikatora polecenia.

- ID_EDIT_CLEAR_ALL Czyści cały dokument.

   Obecnie nie ma standardowej implementacji dla tego polecenia. Należy zaimplementować to dla każdej `CView`klasy pochodnej.

   Jeśli zdecydujesz się zaimplementować to polecenie, zaleca się użycie tego identyfikatora polecenia. Zobacz przykładowy przykładowy przewodnik [MFC SCRIBBLE](../overview/visual-cpp-samples.md) dla przykładowej implementacji.

- ID_EDIT_COPY Kopiuje bieżące zaznaczenie do Schowka.

   Obecnie nie ma standardowej implementacji dla tego polecenia. Należy zaimplementować to dla każdej `CView`klasy pochodnej.

   `CEditView`zapewnia implementację tego polecenia, które kopiuje aktualnie zaznaczony tekst do `CEdit::Copy`Schowka jako CF_TEXT za pomocą programu . Polecenie jest wyłączone, jeśli nie ma bieżącego zaznaczenia.

   Jeśli zdecydujesz się zaimplementować to polecenie, zaleca się użycie tego identyfikatora polecenia.

- ID_EDIT_CUT Wycina bieżące zaznaczenie do Schowka.

   Obecnie nie ma standardowej implementacji dla tego polecenia. Należy zaimplementować to dla każdej `CView`klasy pochodnej.

   `CEditView`zapewnia implementację tego polecenia, które wycina aktualnie zaznaczony tekst `CEdit::Cut`do Schowka jako CF_TEXT za pomocą programu . Polecenie jest wyłączone, jeśli nie ma bieżącego zaznaczenia.

   Jeśli zdecydujesz się zaimplementować to polecenie, zaleca się użycie tego identyfikatora polecenia.

- ID_EDIT_FIND Rozpoczyna operację znajdowania, powoduje wyświetlenia niemodless okna dialogowego znajdowania.

   Obecnie nie ma standardowej implementacji dla tego polecenia. Należy zaimplementować to dla każdej `CView`klasy pochodnej.

   `CEditView`zapewnia implementację tego polecenia, które wywołuje `OnEditFindReplace` funkcję pomocnika implementacji do używania i przechowywania poprzednich ustawień find/replace w prywatnych zmiennych implementacji. Klasa `CFindReplaceDialog` służy do zarządzania niemodytnym oknie dialogowym monitowania użytkownika.

   Jeśli zdecydujesz się zaimplementować to polecenie, zaleca się użycie tego identyfikatora polecenia.

- ID_EDIT_PASTE Wstawia bieżącą zawartość Schowka.

   Obecnie nie ma standardowej implementacji dla tego polecenia. Należy zaimplementować to dla każdej `CView`klasy pochodnej.

   `CEditView`zapewnia implementację tego polecenia, które kopiuje bieżące dane `CEdit::Paste`Schowka zastępując zaznaczony tekst za pomocą programu . Polecenie jest wyłączone, jeśli w Schowku nie ma **żadnych CF_TEXT.**

   `COleClientDoc`po prostu zapewnia program obsługi interfejsu użytkownika polecenia aktualizacji dla tego polecenia. Jeśli Schowek nie zawiera osadzania elementu/obiektu OLE, polecenie zostanie wyłączone. Jesteś odpowiedzialny za napisanie programu obsługi dla rzeczywistego polecenia do rzeczywistego wklejania. Jeśli aplikacja OLE można również wkleić inne formaty, należy podać własny program obsługi interfejsu `COleClientDoc` użytkownika polecenia aktualizacji w widoku lub dokumencie (oznacza to, gdzieś przed w routingu docelowego polecenia).

   Jeśli zdecydujesz się zaimplementować to polecenie, zaleca się użycie tego identyfikatora polecenia.

   Aby zastąpić standardową implementację OLE, należy użyć `COleClientItem::CanPaste`.

- ID_EDIT_PASTE_LINK Wstawia łącze z bieżącej zawartości Schowka.

   Obecnie nie ma standardowej implementacji dla tego polecenia. Należy zaimplementować to dla każdej `CView`klasy pochodnej.

   `COleDocument`po prostu zapewnia program obsługi interfejsu użytkownika polecenia aktualizacji dla tego polecenia. Jeśli Schowek nie zawiera łącza element/obiekt OLE, polecenie zostanie wyłączone. Jesteś odpowiedzialny za napisanie programu obsługi dla rzeczywistego polecenia do rzeczywistego wklejania. Jeśli aplikacja OLE można również wkleić inne formaty, należy podać własny program obsługi interfejsu `COleDocument` użytkownika polecenia aktualizacji w widoku lub dokumencie (oznacza to, gdzieś przed w routingu docelowego polecenia).

   Jeśli zdecydujesz się zaimplementować to polecenie, zaleca się użycie tego identyfikatora polecenia.

   Aby zastąpić standardową implementację OLE, należy użyć `COleClientItem::CanPasteLink`.

- ID_EDIT_PASTE_SPECIAL Wstawia bieżącą zawartość Schowka z opcjami.

   Obecnie nie ma standardowej implementacji dla tego polecenia. Należy zaimplementować to dla każdej `CView`klasy pochodnej. MFC nie udostępnia tego okna dialogowego.

   Jeśli zdecydujesz się zaimplementować to polecenie, zaleca się użycie tego identyfikatora polecenia.

- ID_EDIT_REPEAT Powtarza ostatnią operację.

   Obecnie nie ma standardowej implementacji dla tego polecenia. Należy zaimplementować to dla każdej `CView`klasy pochodnej.

   `CEditView`zapewnia implementację tego polecenia, aby powtórzyć operację ostatniego znalezienia. Używane są zmienne implementacji prywatnej dla ostatniego find. Polecenie jest wyłączone, jeśli nie można podjąć próby znalezienia.

   Jeśli zdecydujesz się zaimplementować to polecenie, zaleca się użycie tego identyfikatora polecenia.

- ID_EDIT_REPLACE Rozpoczyna operację wymiany, powoduje wyświetlenia niemodytowego okna dialogowego zamiany.

   Obecnie nie ma standardowej implementacji dla tego polecenia. Należy zaimplementować to dla każdej `CView`klasy pochodnej.

   `CEditView`zapewnia implementację tego polecenia, które wywołuje `OnEditFindReplace` funkcję pomocnika implementacji do używania i przechowywania poprzednich ustawień find/replace w prywatnych zmiennych implementacji. Klasa `CFindReplaceDialog` służy do zarządzania niemodless okno dialogowe, które monituje użytkownika.

   Jeśli zdecydujesz się zaimplementować to polecenie, zaleca się użycie tego identyfikatora polecenia.

- ID_EDIT_SELECT_ALL Wybiera cały dokument.

   Obecnie nie ma standardowej implementacji dla tego polecenia. Należy zaimplementować to dla każdej `CView`klasy pochodnej.

   `CEditView`zapewnia implementację tego polecenia, które wybiera cały tekst w dokumencie. Polecenie jest wyłączone, jeśli nie ma tekstu do zaznaczenia.

   Jeśli zdecydujesz się zaimplementować to polecenie, zaleca się użycie tego identyfikatora polecenia.

- ID_EDIT_UNDO Cofa ostatnią operację.

   Obecnie nie ma standardowej implementacji dla tego polecenia. Należy zaimplementować to dla każdej `CView`klasy pochodnej.

   `CEditView`zapewnia implementację tego polecenia, używając `CEdit::Undo`. Polecenie jest wyłączone, jeśli `CEdit::CanUndo` zwraca wartość FAŁSZ.

   Jeśli zdecydujesz się zaimplementować to polecenie, zaleca się użycie tego identyfikatora polecenia.

- ID_EDIT_REDO ponawia ostatnią operację.

   Obecnie nie ma standardowej implementacji dla tego polecenia. Należy zaimplementować to dla każdej `CView`klasy pochodnej.

   Jeśli zdecydujesz się zaimplementować to polecenie, zaleca się użycie tego identyfikatora polecenia.

- ID_WINDOW_NEW Otwiera kolejne okno aktywnego dokumentu.

   `CMDIFrameWnd::OnWindowNew`implementuje tę zaawansowana funkcję przy użyciu szablonu dokumentu bieżącego dokumentu w celu utworzenia innej ramki zawierającej inny widok bieżącego dokumentu.

   Podobnie jak większość wielu poleceń menu okna interfejsu dokumentu (MDI), polecenie jest wyłączone, jeśli nie ma aktywnego okna podrzędnego MDI.

   Dostosowanie tego programu obsługi poleceń nie jest zalecane. Jeśli chcesz podać polecenie, które tworzy dodatkowe widoki lub okna ramki, prawdopodobnie lepiej będzie wymyślić własne polecenie. Można sklonować kod `CMDIFrameWnd::OnWindowNew` z i zmodyfikować go do określonej ramki i wyświetlić klasy swoich upodobań.

- ID_WINDOW_ARRANGE Rozmieszcza ikony u dołu okna MDI.

   `CMDIFrameWnd`implementuje to standardowe polecenie MDI w `OnMDIWindowCmd`funkcji pomocnika implementacji . Ten pomocnik mapuje identyfikatory poleceń do komunikatów mdi systemu Windows i dlatego może udostępniać dużo kodu.

   Podobnie jak większość poleceń menu okna MDI, polecenie jest wyłączone, jeśli nie ma aktywnego okna podrzędnego MDI.

   Dostosowanie tego programu obsługi poleceń nie jest zalecane.

- ID_WINDOW_CASCADE kaskadowe okna, aby nakładały się na siebie.

   `CMDIFrameWnd`implementuje to standardowe polecenie MDI w `OnMDIWindowCmd`funkcji pomocnika implementacji . Ten pomocnik mapuje identyfikatory poleceń do komunikatów mdi systemu Windows i dlatego może udostępniać dużo kodu.

   Podobnie jak większość poleceń menu okna MDI, polecenie jest wyłączone, jeśli nie ma aktywnego okna podrzędnego MDI.

   Dostosowanie tego programu obsługi poleceń nie jest zalecane.

- ID_WINDOW_TILE_HORZ Kafelki okna poziomo.

   To polecenie jest `CMDIFrameWnd` implementowane w taki sam ID_WINDOW_CASCADE, z wyjątkiem innego komunikatu systemu Windows MDI jest używany do operacji.

   Należy wybrać domyślną orientację kafelka dla aplikacji. Można to zrobić, zmieniając identyfikator elementu menu Okno "Kafelek" na ID_WINDOW_TILE_HORZ lub ID_WINDOW_TILE_VERT.

- ID_WINDOW_TILE_VERT okna kafelków w pionie.

   To polecenie jest `CMDIFrameWnd` implementowane w taki sam ID_WINDOW_CASCADE, z wyjątkiem innego komunikatu systemu Windows MDI jest używany do operacji.

   Należy wybrać domyślną orientację kafelka dla aplikacji. Można to zrobić, zmieniając identyfikator elementu menu Okno "Kafelek" na ID_WINDOW_TILE_HORZ lub ID_WINDOW_TILE_VERT.

- ID_WINDOW_SPLIT interfejs klawiatury do rozdzielacza.

   `CView`obsługuje to polecenie `CSplitterWnd` dla implementacji. Jeśli widok jest częścią okna rozdzielacza, to polecenie `CSplitterWnd::DoKeyboardSplit`zostanie delegowane do funkcji implementacji . Spowoduje to umieszczenie rozdzielacza w trybie, który pozwoli użytkownikom klawiatury na dzielenie lub rozpisywać okno rozdzielacza.

   To polecenie jest wyłączone, jeśli widok nie znajduje się w rozdzielaczu.

   Dostosowanie tego programu obsługi poleceń nie jest zalecane.

- ID_APP_ABOUT wywołuje okno dialogowe Informacje.

   Nie ma standardowej implementacji dla pola Informacje o aplikacji. Domyślna aplikacja utworzona przez AppWizard utworzy niestandardową klasę okna dialogowego dla aplikacji i użyje jej jako pola Informacje. AppWizard będzie również napisać program obsługi polecenia trywialne, który obsługuje to polecenie i wywołuje okno dialogowe.

   Prawie zawsze zaimplementujesz to polecenie.

- ID_APP_EXIT Zakończ aplikację.

   `CWinApp::OnAppExit`obsługuje to polecenie, wysyłając wiadomość WM_CLOSE do głównego okna aplikacji. Standardowe zamykanie aplikacji (monitowanie o brudne pliki i tak `CFrameWnd` dalej) jest obsługiwane przez implementację.

   Dostosowanie tego programu obsługi poleceń nie jest zalecane. Zalecana `CWinApp::SaveAllModified` jest `CFrameWnd` logika zastępowania lub zamykania.

   Jeśli zdecydujesz się zaimplementować to polecenie, zaleca się użycie tego identyfikatora polecenia.

- ID_HELP_INDEX Listy tematów Pomocy z programu . HLP.

    > [!NOTE]
    >  Należy połączyć to `CWinApp`z mapą komunikatów klasy pochodnej, aby włączyć tę funkcję.

   `CWinApp::OnHelpIndex`obsługuje to polecenie, trywialnie wywołując `CWinApp::WinHelp`.

   Dostosowanie tego programu obsługi poleceń nie jest zalecane.

- ID_HELP_USING Wyświetla pomoc dotyczącą korzystania z Pomocy.

    > [!NOTE]
    >  Należy połączyć to `CWinApp`z mapą komunikatów klasy pochodnej, aby włączyć tę funkcję.

   `CWinApp::OnHelpUsing`obsługuje to polecenie, trywialnie wywołując `CWinApp::WinHelp`.

   Dostosowanie tego programu obsługi poleceń nie jest zalecane.

- ID_CONTEXT_HELP wchodzi w tryb pomocy SHIFT-F1.

    > [!NOTE]
    >  Należy połączyć to `CWinApp`z mapą komunikatów klasy pochodnej, aby włączyć tę funkcję.

   `CWinApp::OnContextHelp`obsługuje to polecenie, ustawiając kursor trybu pomocy, wprowadzając pętlę modalną i czekając, aż użytkownik wybierze okno, aby uzyskać pomoc. Więcej informacji na temat implementacji pomocy MFC można znaleźć w [notatce technicznej 28.](../mfc/tn028-context-sensitive-help-support.md)

   Dostosowanie tego programu obsługi poleceń nie jest zalecane.

- ID_HELP Udziela pomocy w bieżącym kontekście

    > [!NOTE]
    >  Należy połączyć to `CWinApp`z mapą komunikatów klasy pochodnej, aby włączyć tę funkcję.

   `CWinApp::OnHelp`obsługuje to polecenie, uzyskując odpowiedni kontekst pomocy dla bieżącego kontekstu aplikacji. Obsługuje to prostą pomoc F1, pomoc w skrzynkach wiadomości i tak dalej. Więcej informacji na temat implementacji pomocy MFC można znaleźć w [notatce technicznej 28.](../mfc/tn028-context-sensitive-help-support.md)

   Dostosowanie tego programu obsługi poleceń nie jest zalecane.

- ID_DEFAULT_HELP Wyświetla domyślną pomoc kontekstu

    > [!NOTE]
    >  Należy połączyć to `CWinApp`z mapą komunikatów klasy pochodnej, aby włączyć tę funkcję.

   To polecenie jest zwykle `CWinApp::OnHelpIndex`mapowane na .

   Jeśli żądane jest rozróżnienie między domyślną Pomocą a indeksem Pomocy, można podać inny program obsługi poleceń.

- ID_NEXT_PANE Przechodzi do następnego okienka

   `CView`obsługuje to polecenie `CSplitterWnd` dla implementacji. Jeśli widok jest częścią okna rozdzielacza, to polecenie `CSplitterWnd::OnNextPaneCmd`zostanie delegowane do funkcji implementacji . Spowoduje to przeniesienie aktywnego widoku do następnego okienka w rozdzielaczu.

   To polecenie jest wyłączone, jeśli widok nie znajduje się w rozdzielaczu lub nie ma następnego okienka, do które można przejść.

   Dostosowanie tego programu obsługi poleceń nie jest zalecane.

- ID_PREV_PANE Przechodzi do poprzedniego okienka

   `CView`obsługuje to polecenie `CSplitterWnd` dla implementacji. Jeśli widok jest częścią okna rozdzielacza, to polecenie `CSplitterWnd::OnNextPaneCmd`zostanie delegowane do funkcji implementacji . Spowoduje to przeniesienie aktywnego widoku do poprzedniego okienka w rozdzielaczu.

   To polecenie jest wyłączone, jeśli widok nie znajduje się w rozdzielaczu lub nie ma poprzedniego okienka, do które można przejść.

   Dostosowanie tego programu obsługi poleceń nie jest zalecane.

- ID_OLE_INSERT_NEW Wstawia nowy obiekt OLE

   Obecnie nie ma standardowej implementacji dla tego polecenia. Należy zaimplementować to dla klasy `CView`pochodnej, aby wstawić nowy element/obiekt OLE przy bieżącym zaznaczeniu.

   Wszystkie aplikacje klienckie OLE należy zaimplementować to polecenie. AppWizard, z opcją OLE, utworzy `OnInsertObject` szkielet implementacji w klasie widoku, które trzeba będzie zakończyć.

   Zobacz przykład [OCLIENT](../overview/visual-cpp-samples.md) OLE MFC dla pełnej implementacji tego polecenia.

- ID_OLE_EDIT_LINKS Edytuje łącza OLE

   `COleDocument`obsługuje to polecenie przy użyciu implementacji dostarczonych przez MFC standardowego okna dialogowego łączy OLE. Implementacja tego okna dialogowego `COleLinksDialog` jest dostępna za pośrednictwem klasy. Jeśli bieżący dokument nie zawiera żadnych łączy, polecenie jest wyłączone.

   Dostosowanie tego programu obsługi poleceń nie jest zalecane.

- ID_OLE_VERB_FIRST... LAST Zakres identyfikatorów dla czasowników OLE

   `COleDocument`używa tego zakresu identyfikatorów polecenia dla zleceń obsługiwanych przez aktualnie wybrany element/obiekt OLE. Musi to być zakres, ponieważ dany element OLE/typ obiektu może obsługiwać zero lub więcej zleceń niestandardowych. W menu aplikacji powinien mieć jeden element menu o identyfikatorze ID_OLE_VERB_FIRST. Po uruchomieniu programu menu zostanie zaktualizowane o odpowiedni opis czasownika menu (lub menu podręczne z wieloma zleceniami). Zarządzanie menu OLE jest obsługiwane `AfxOleSetEditMenu`przez , zrobić w programie obsługi interfejsu użytkownika polecenia aktualizacji dla tego polecenia.

   Nie ma żadnych jawnych programów obsługi poleceń do obsługi każdego identyfikatora polecenia w tym zakresie. `COleDocument::OnCmdMsg`jest zastępowany, aby podeszli do wszystkich identyfikatorów poleceń w tym zakresie, przekształcić je w `COleClientItem::DoVerb`liczby czasowników opartych na wartościach zerowych i uruchomić serwer dla tego zlecenia (używającego ).

   Nie zaleca się dostosowywania lub innego użycia tego zakresu identyfikatorów poleceń.

- ID_VIEW_TOOLBAR Włącza i wyłącza pasek narzędzi

   `CFrameWnd`obsługuje to polecenie i program obsługi interfejsu użytkownika polecenia aktualizacji, aby przełączyć widoczny stan paska narzędzi. Pasek narzędzi musi być oknem podrzędnym ramki z identyfikatorem okna podrzędnego AFX_IDW_TOOLBAR. Program obsługi poleceń faktycznie przełącza widoczność okna paska narzędzi. `CFrameWnd::RecalcLayout`służy do ponownego rysowania okna ramki z paskiem narzędzi w nowym stanie. Program obsługi interfejsu użytkownika polecenia aktualizacji sprawdza element menu, gdy pasek narzędzi jest widoczny.

   Dostosowanie tego programu obsługi poleceń nie jest zalecane. Jeśli chcesz dodać dodatkowe paski narzędzi, należy sklonować i zmodyfikować program obsługi poleceń i program obsługi interfejsu użytkownika polecenia aktualizacji dla tego polecenia.

- ID_VIEW_STATUS_BAR Włącza i wyłącza pasek stanu

   To polecenie jest `CFrameWnd` implementowane w taki sam ID_VIEW_TOOLBAR, z wyjątkiem innego identyfikatora okna podrzędnego (AFX_IDW_STATUS_BAR).

## <a name="update-only-command-handlers"></a>Programy obsługi poleceń tylko do aktualizacji

Kilka standardowych identyfikatorów poleceń jest używanych jako wskaźniki w paskach stanu. Używają one tego samego mechanizmu obsługi interfejsu użytkownika polecenia aktualizacji, aby wyświetlić ich bieżący stan wizualny podczas bezczynnego czasu aplikacji. Ponieważ nie mogą być wybrane przez użytkownika (oznacza to, że nie można wypchnąć okienko paska stanu), nie ma sensu mieć ON_COMMAND obsługi dla tych identyfikatorów poleceń.

- ID_INDICATOR_CAPS : Wskaźnik blokady WPR.

- ID_INDICATOR_NUM : Wskaźnik blokady NUM.

- ID_INDICATOR_SCRL : Wskaźnik blokady SCRL.

- ID_INDICATOR_KANA : Wskaźnik blokady KANA (dotyczy tylko japońskich systemów).

Wszystkie trzy z nich `CFrameWnd::OnUpdateKeyIndicator`są implementowane w , pomocnika implementacji, który używa identyfikatora polecenia do mapowania do odpowiedniego klucza wirtualnego. Wspólna implementacja włącza lub wyłącza (dla okienek `CCmdUI` stanu wyłączone = bez tekstu) obiekt w zależności od tego, czy odpowiedni klucz wirtualny jest aktualnie zablokowany.

Dostosowanie tego programu obsługi poleceń nie jest zalecane.

- ID_INDICATOR_EXT : Wskaźnik wyboru EXTended.

- ID_INDICATOR_OVR : Wskaźnik OVeRstrike.

- ID_INDICATOR_REC : Wskaźnik RECording.

Obecnie nie ma standardowego wdrożenia tych wskaźników.

Jeśli zdecydujesz się zaimplementować te wskaźniki, zalecamy użycie tych identyfikatorów wskaźników i utrzymanie kolejności wskaźników na pasku stanu (czyli w następującej kolejności: EXT, CAP, NUM, SCRL, OVR, REC).

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
