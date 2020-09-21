---
title: 'TN041: migracja MFC-OLE1 do MFC-OLE 2'
ms.date: 10/18/2018
helpviewer_keywords:
- OLE1 [MFC]
- migrating OLE1 to OLE2
- migration [MFC], OLE1 to OLE2
- OLE2 [MFC]
- porting OLE1 to OLE2
- converting OLE1 to OLE2
- upgrading Visual C++ applications [MFC], OLE1 to OLE2
- TN041
ms.assetid: 67f55552-4b04-4ddf-af0b-4d9eaf5da957
ms.openlocfilehash: 7d0381983481278b1410ae0ff11463519d4cbb34
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743155"
---
# <a name="tn041-mfcole1-migration-to-mfcole-2"></a>TN041: migracja z MFC/OLE1 do MFC/OLE 2

> [!NOTE]
> Następująca Uwaga techniczna nie została zaktualizowana, ponieważ została najpierw uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zalecamy wyszukiwanie tematu zainteresowania w indeksie dokumentacji online.

## <a name="general-issues-relating-to-migration"></a>Ogólne problemy związane z migracją

Jednym z celów projektowania klas OLE 2 w MFC 2,5 (i wyższych) było zachowanie większości tej samej architektury w MFC 2,0 dla obsługi OLE 1,0. W związku z tym wiele z tych samych klas OLE w MFC 2,0 nadal istnieje w tej wersji MFC ( `COleDocument` ,, `COleServerDoc` `COleClientItem` , `COleServerItem` ). Ponadto wiele interfejsów API w tych klasach jest dokładnie takie same. Jednak OLE 2 różni się od OLE 1,0, dzięki czemu można oczekiwać, że niektóre szczegóły zostały zmienione. Jeśli znasz obsługę OLE1 MFC 2.0, zobaczysz w domu z obsługą 2,0 MFC.

Jeśli tworzysz istniejącą aplikację MFC/OLE1 i dodasz do niej funkcję OLE 2, należy najpierw przeczytać tę uwagę. Ta uwaga dotyczy niektórych ogólnych problemów, które mogą wystąpić podczas przenoszenia funkcji OLE1 do MFC/OLE 2, a następnie omawiają problemy, które nie zostały pokryte podczas przenoszenia dwóch aplikacji zawartych w MFC 2,0: MFC OLE Samples [OCLIENT](../overview/visual-cpp-samples.md) i [HIERSVR](../overview/visual-cpp-samples.md).

## <a name="mfc-documentview-architecture-is-important"></a>Architektura dokumentu MFC/widoku jest ważna

Jeśli aplikacja nie korzysta z architektury dokumentu/widoku MFC i chcesz dodać do aplikacji obsługę OLE 2, to teraz czas przejścia do dokumentu/widoku. Wiele zalet klas OLE 2 klasy MFC jest realizowanych tylko wtedy, gdy aplikacja korzysta z wbudowanej architektury i składników MFC.

Implementacja serwera lub kontenera bez użycia architektury MFC jest możliwe, ale nie jest to zalecane.

## <a name="use-mfc-implementation-instead-of-your-own"></a>Użyj implementacji MFC zamiast własnych

Klasy MFC "implementacji w trybie konserwowania", takie jak `CToolBar` , `CStatusBar` i `CScrollView` mają wbudowane specjalne kody przypadków dla obsługi OLE 2. Dlatego, jeśli możesz użyć tych klas w aplikacji, możesz skorzystać z nakładu pracy w nich, aby zapewnić im świadomość OLE. Z tego względu możliwe jest, aby w tym celu "klasy" "samodzielnie", ale nie jest to zalecane. Jeśli musisz zaimplementować podobną funkcjonalność, kod źródłowy MFC jest doskonałym odwołaniem do podawania niektórych precyzyjnych punktów OLE (zwłaszcza w przypadku aktywacji w miejscu).

## <a name="examine-the-mfc-sample-code"></a>Badanie przykładowego kodu MFC

Istnieje szereg przykładów MFC, które obejmują funkcje OLE. Każda z tych aplikacji implementuje mechanizm OLE z innego kąta:

- [HIERSVR](../overview/visual-cpp-samples.md) Przeznaczony głównie do użytku jako aplikacja serwera. Została ona uwzględniona w bibliotece MFC 2,0 jako aplikacja MFC/OLE1 i została przełączona do MFC/OLE 2, a następnie rozszerzona, aby implementował wiele funkcji OLE dostępnych w OLE 2.

- [OCLIENT](../overview/visual-cpp-samples.md) Jest to autonomiczna aplikacja kontenera, która przedstawia wiele funkcji OLE z punktu widzenia kontenera. Port został przesunięty z biblioteki MFC 2,0, a następnie rozszerzony do obsługi wielu bardziej zaawansowanych funkcji OLE, takich jak niestandardowe formaty schowka i linki do elementów osadzonych.

- [DRAWCLI](../overview/visual-cpp-samples.md) Ta aplikacja implementuje obsługę kontenera OLE podobnie jak OCLIENT, z tą różnicą, że działa ona w ramach istniejącego programu do rysowania zorientowanego obiektowo. Pokazuje, jak można zaimplementować obsługę kontenera OLE i zintegrować ją z istniejącą aplikacją.

- [SUPERPAD](../overview/visual-cpp-samples.md) Ta aplikacja, a także w przypadku aplikacji autonomicznej, również jest serwerem OLE. Obsługa serwera, który implementuje, jest dość minimalistyczny. Szczególnie ważne jest, w jaki sposób używa usług Schowka OLE do kopiowania danych do schowka, ale używa funkcji wbudowanych w kontrolce "Edytuj" systemu Windows w celu zaimplementowania funkcji wklejania Schowka. Przedstawia to interesujące mieszanie tradycyjnych zastosowań interfejsu API systemu Windows, a także integrację z nowymi interfejsami API OLE.

Aby uzyskać więcej informacji na temat przykładowych aplikacji, zobacz "pomoc Przykładowa MFC".

## <a name="case-study-oclient-from-mfc-20"></a>Analiza przypadku: OCLIENT z MFC 2,0

Jak wspomniano powyżej, [OCLIENT](../overview/visual-cpp-samples.md) został uwzględniony w MFC 2,0 i zaimplementowany OLE z MFC/OLE1. Kroki, według których ta aplikacja była początkowo konwertowana, aby używać klas MFC/OLE 2, opisano poniżej. Dodano szereg funkcji po zakończeniu wstępnego portu w celu lepszego zilustrowania klas MFC/OLE. Te funkcje nie zostaną omówione w tym miejscu. Zapoznaj się z przykładem, aby uzyskać więcej informacji na temat tych zaawansowanych funkcji.

> [!NOTE]
> Błędy kompilatora i proces krok po kroku został utworzony przy użyciu Visual C++ 2,0. Określone komunikaty o błędach i lokalizacje mogą ulec zmianie w Visual C++ 4,0, ale informacje o pojęciach pozostają poprawne.

### <a name="getting-it-up-and-running"></a>Pobieranie i uruchamianie

Podejście podjęte do przenoszenia przykładu OCLIENT do MFC/OLE jest uruchamiane przez skompilowanie go i naprawianie błędów kompilatora, które będą wynikiem. Jeśli pobierasz próbkę OCLIENT z MFC 2,0 i skompilujesz ją w tej wersji MFC, zobaczysz, że nie ma więcej błędów do rozwiązania. Błędy w kolejności, w której wystąpiły, zostały opisane poniżej.

### <a name="compile-and-fix-errors"></a>Kompiluj i naprawiaj błędy

```Output
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters
```

Pierwsze problemy związane z błędami `COleClientItem::Draw` . W MFC/OLE1 trwało więcej parametrów niż jest to wersja MFC/OLE. Dodatkowe parametry często nie są potrzebne i zazwyczaj mają wartość NULL (jak w tym przykładzie). Ta wersja MFC może automatycznie określić wartości dla lpWBounds, gdy do przeszukiwania jest używana wartość w formacie metapliku. Ponadto parametr pFormatDC nie jest już konieczny, ponieważ platforma kompiluje jeden z "Attribute DC" z kontrolera pDC. Aby rozwiązać ten problem, wystarczy usunąć dwa dodatkowe parametry o wartości NULL do wywołania rysowania.

```Output
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier
\oclient\mainview.cpp(273) : error C2057: expected constant expression
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
```

Powyższe błędy powyżej wynikają z faktu, że wszystkie `COleClientItem::CreateXXXX` funkcje w MFC/OLE1 wymagały przekazanie unikatowej nazwy do reprezentowania elementu. Jest to wymaganie źródłowego interfejsu API OLE. Nie jest to konieczne w przypadku MFC/OLE 2, ponieważ OLE 2 nie używa DDE jako podstawowego mechanizmu komunikacji (nazwa została użyta w konwersacji DDE). Aby rozwiązać ten problem, można usunąć funkcję, `CreateNewName` a także wszystkie odwołania do niej. Można łatwo sprawdzić, jakie funkcje MFC/OLE są oczekiwane w tej wersji po prostu przez umieszczenie kursora na wywołaniu i naciśnięcie klawisza F1.

Inny obszar, który jest znacząco różny, to obsługa Schowka OLE 2. W przypadku korzystania z OLE1 interfejsy API Schowka systemu Windows współpracują ze schowka. W przypadku OLE 2 jest to realizowane przy użyciu innego mechanizmu. Interfejsy API MFC/OLE1 założono, że schowek był otwarty przed skopiowaniem `COleClientItem` obiektu do Schowka. Nie jest to już konieczne i spowoduje to niepowodzenie wszystkich operacji w schowku MFC/OLE. Podczas edycji kodu w celu usunięcia zależności w programie `CreateNewName` należy również usunąć kod, który otwiera i zamyka Schowek systemu Windows.

```Output
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function
\oclient\mainview.cpp(344) : error C2057: expected constant expression
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'
```

Te błędy są wynikiem `CMainView::OnInsertObject` procedury obsługi. Obsługa polecenia "Wstaw nowy obiekt" to inny obszar, w którym zmienia się całkiem nieco. W takim przypadku najłatwiej jest po prostu scalić oryginalną implementację z usługą AppWizard dla nowej aplikacji kontenera OLE. W rzeczywistości jest to technika, którą można zastosować do przenoszenia innych aplikacji. W MFC/OLE1 wyświetla się okno dialogowe "Wstaw obiekt", wywołując `AfxOleInsertDialog` funkcję. W tej wersji utworzysz `COleInsertObject` obiekt okna dialogowego i Wywołaj `DoModal` . Ponadto nowe elementy OLE są tworzone przy użyciu **identyfikatora CLSID** zamiast ciągu ClassName. Wynik końcowy powinien wyglądać podobnie do tego

```cpp
COleInsertDialog dlg;
if (dlg.DoModal() != IDOK)
    return;

BeginWaitCursor();

CRectItem* pItem = NULL;
TRY
{
    // First create the C++ object
    pItem = GetDocument()->CreateItem();
    ASSERT_VALID(pItem);

    // Initialize the item from the dialog data.
    if (!dlg.CreateItem(pItem))
        AfxThrowMemoryException();
            // any exception will do
    ASSERT_VALID(pItem);

    // run the object if appropriate
    if (dlg.GetSelectionType() == COleInsertDialog::createNewItem)
        pItem->DoVerb(OLEIVERB_SHOW, this);

    // update right away
    pItem->UpdateLink();
    pItem->UpdateItemRectFromServer();

    // set selection to newly inserted item
    SetSelection(pItem);
    pItem->Invalidate();
}
CATCH (CException, e)
{
    // clean up item
    if (pItem != NULL)
        GetDocument()->DeleteItem(pItem);

    AfxMessageBox(IDP_FAILED_TO_CREATE);
}
END_CATCH

EndWaitCursor();
```

> [!NOTE]
> Wstawianie nowego obiektu może być inne dla aplikacji):

Należy również uwzględnić \<afxodlgs.h> , który zawiera deklarację dla `COleInsertObject` klasy okna dialogowego, a także inne standardowe okna dialogowe zapewniane przez MFC.

```Output
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters
```

Te błędy są spowodowane faktem, że niektóre stałe OLE1 uległy zmianie w OLE 2, chociaż w koncepcji są takie same. W tym przypadku `OLEVERB_PRIMARY` zmienił się na `OLEIVERB_PRIMARY` . Zarówno OLE1, jak i OLE 2, zlecenie podstawowe jest zwykle wykonywane przez kontener, gdy użytkownik kliknie dwukrotnie element.

Ponadto `DoVerb` teraz pobiera dodatkowy parametr — wskaźnik do widoku ( `CView` *). Ten parametr jest używany tylko do implementacji "edycji wizualnej" (lub aktywacji w miejscu). W przypadku ustawienia tego parametru na wartość NULL, ponieważ ta funkcja nie jest obecnie wdrażana.

Aby upewnić się, że platforma nigdy nie próbuje aktywować w miejscu, należy przesłonić `COleClientItem::CanActivate` następujące czynności:

```cpp
BOOL CRectItem::CanActivate()
{
    return FALSE;
}
```

```Output
\oclient\rectitem.cpp(53) : error C2065: 'GetBounds' : undeclared identifier
\oclient\rectitem.cpp(53) : error C2064: term does not evaluate to a function
\oclient\rectitem.cpp(84) : error C2065: 'SetBounds' : undeclared identifier
\oclient\rectitem.cpp(84) : error C2064: term does not evaluate to a function
```

W MFC/OLE1 `COleClientItem::GetBounds` i `SetBounds` były używane do wykonywania zapytań i manipulowania zakresem elementu ( `left` `top` elementy i są zawsze równe zero). W MFC/OLE 2 jest to bardziej bezpośrednio obsługiwane przez `COleClientItem::GetExtent` `SetExtent` program i, które zajmuje się **rozmiarem** lub w `CSize` zamian.

Kod dla nowych SetItemRectToServer i wywołań UpdateItemRectFromServer wygląda następująco:

```cpp
BOOL CRectItem::UpdateItemRectFromServer()
{
    ASSERT(m_bTrackServerSize);
    CSize size;
    if (!GetExtent(&size))
        return FALSE;    // blank

    // map from HIMETRIC to screen coordinates
    {
        CClientDC screenDC(NULL);
        screenDC.SetMapMode(MM_HIMETRIC);
        screenDC.LPtoDP(&size);
    }
    // just set the item size
    if (m_rect.Size() != size)
    {
        // invalidate the old size/position
        Invalidate();
        m_rect.right = m_rect.left + size.cx;
        m_rect.bottom = m_rect.top + size.cy;
        // as well as the new size/position
        Invalidate();
    }
    return TRUE;
}

BOOL CRectItem::SetItemRectToServer()
{
    // set the official bounds for the embedded item
    CSize size = m_rect.Size();
    {
        CClientDC screenDC(NULL);
        screenDC.SetMapMode(MM_HIMETRIC);
        screenDC.DPtoLP(&size);
    }
    TRY
    {
        SetExtent(size);    // may do a wait
    }
    CATCH(CException, e)
    {
        return FALSE;  // links will not allow SetBounds
    }
    END_CATCH
    return TRUE;
}
```

```Output
\oclient\frame.cpp(50) : error C2039: 'InWaitForRelease' : is not a member of 'COleClientItem'
\oclient\frame.cpp(50) : error C2065: 'InWaitForRelease' : undeclared identifier
\oclient\frame.cpp(50) : error C2064: term does not evaluate to a function
```

W przypadku synchronicznych wywołań interfejsu API MFC/OLE1 z kontenera na serwer zostały *symulowane*, ponieważ OLE1 było w wielu przypadkach asynchroniczne asynchronicznie. Przed przetworzeniem poleceń od użytkownika było konieczne wyszukanie oczekujących wywołań asynchronicznych. MFC/OLE1 udostępnia `COleClientItem::InWaitForRelease` funkcję do wykonania tej czynności. W MFC/OLE 2 nie jest to konieczne, aby można było usunąć przesłonięcie polecenia we wszystkich CMainFrame.

W tym momencie OCLIENT skompiluje i utworzy link.

### <a name="other-necessary-changes"></a>Inne niezbędne zmiany

Istnieje kilka rzeczy, które nie są gotowe do działania OCLIENT. Lepiej jest rozwiązać te problemy teraz zamiast w przyszłości.

Najpierw konieczne jest zainicjowanie bibliotek OLE. Jest to realizowane przez wywołanie `AfxOleInit` z `InitInstance` :

```cpp
if (!AfxOleInit())
{
    AfxMessageBox("Failed to initialize OLE libraries");
    return FALSE;
}
```

Dobrym pomysłem jest również sprawdzenie funkcji wirtualnych dla zmian listy parametrów. Jedna taka funkcja jest `COleClientItem::OnChange` zastępowana w każdej aplikacji kontenera MFC/OLE. Przeglądając pomoc online, zobaczysz, że dodano dodatkową wartość "DWORD dwParam". Nowa CRectItem:: OnChange wygląda następująco:

```cpp
void
CRectItem::OnChange(OLE_NOTIFICATION wNotification, DWORD dwParam)
{
    if (m_bTrackServerSize && !UpdateItemRectFromServer())
    {
        // Blank object
        if (wNotification == OLE_CLOSED)
        {
            // no data received for the object - destroy it
            ASSERT(!IsVisible());
            GetDocument()->DeleteItem(this);
            return; // no update (item is gone now)
        }
    }
    if (wNotification != OLE_CLOSED)
        Dirty();
    Invalidate();
    // any change will cause a redraw
}
```

W MFC/OLE1, aplikacje kontenera pochodne klasy dokumentu `COleClientDoc` . W MFC/OLE 2 Ta klasa została usunięta i zastąpiona przez `COleDocument` (Ta nowa organizacja ułatwia tworzenie aplikacji kontenera/serwera). Istnieje **#define** , która jest mapowana `COleClientDoc` na, aby `COleDocument` uprościć port MFC/OLE1 do MFC/OLE 2, takich jak OCLIENT. Jedną z funkcji, które nie są dostarczane przez `COleDocument` program, `COleClientDoc` jest standardowe wpisy mapy komunikatów poleceń. Dzieje się tak, aby aplikacje serwera, które również używały `COleDocument` (pośrednio), nie przenoszą do nich nakładów obsługi poleceń, chyba że są to aplikacje kontenera/serwera. Należy dodać następujące wpisy do mapy komunikatów CMainDoc:

```cpp
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE, OnUpdatePasteMenu)
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK, OnUpdatePasteLinkMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS, OnUpdateEditLinksMenu)
ON_COMMAND(ID_OLE_EDIT_LINKS, COleDocument::OnEditLinks)
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST, OnUpdateObjectVerbMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT, OnUpdateObjectVerbMenu)
ON_COMMAND(ID_OLE_EDIT_CONVERT, OnEditConvert)
```

Implementacja wszystkich tych poleceń znajduje się w `COleDocument` , która jest klasą bazową dla dokumentu.

W tym momencie OCLIENT jest funkcjonalną aplikacją kontenera OLE. Można wstawiać elementy dowolnego typu (OLE1 lub OLE 2). Ponieważ wymagany kod umożliwiający aktywację w miejscu nie jest zaimplementowany, elementy są edytowane w osobnym oknie, podobnie jak w przypadku OLE1. W następnej sekcji omówiono niezbędne zmiany, które umożliwiają edycję w miejscu (czasami nazywaną "edycją wizualizacji").

### <a name="adding-visual-editing"></a>Dodawanie "edycji wizualnej"

Jedną z najbardziej interesujących funkcji technologii OLE jest aktywacja w miejscu (lub "Edycja wizualna"). Ta funkcja umożliwia aplikacji serwera przejęcie części interfejsu użytkownika kontenera w celu zapewnienia bardziej bezproblemowego interfejsu edycji dla użytkownika. Aby zaimplementować aktywację w miejscu do OCLIENT, należy dodać pewne zasoby specjalne, a także dodatkowy kod. Te zasoby i kod są zwykle dostarczane przez AppWizard — w rzeczywistości większość kodu została pokazana bezpośrednio od nowej aplikacji AppWizard z obsługą "Container".

Najpierw należy dodać zasób menu, który ma być używany, gdy istnieje element, który jest aktywny. Ten dodatkowy zasób menu można utworzyć w Visual C++ przez skopiowanie zasobu IDR_OCLITYPE i usunięcie wszystkich plików i okien wyskakujących. Dwa paski separatora są wstawiane między oknami wyskakującymi plików i okien, aby wskazać separację grup (powinna wyglądać tak: plik &#124;&#124; okno). Aby uzyskać więcej informacji o tym, co oznaczają te separatory i jak są scalane menu serwera i kontenera, zobacz menu [i zasoby: scalanie menu](../mfc/menus-and-resources-menu-merging.md).

Po utworzeniu tych menu musisz powiadomić o nich strukturę. W tym celu należy wywołać `CDocTemplate::SetContainerInfo` szablon dokumentu przed dodaniem go do listy szablonów dokumentów w InitInstance. Nowy kod do zarejestrowania szablonu dokumentu wygląda następująco:

```cpp
CDocTemplate* pTemplate = new CMultiDocTemplate(
    IDR_OLECLITYPE,
    RUNTIME_CLASS(CMainDoc),
    RUNTIME_CLASS(CMDIChildWnd), // standard MDI child frame
    RUNTIME_CLASS(CMainView));

pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);

AddDocTemplate(pTemplate);
```

Zasób IDR_OLECLITYPE_INPLACE jest specjalnym zasobem w miejscu utworzonym w Visual C++.

Aby włączyć aktywację w miejscu, istnieje kilka rzeczy, które należy zmienić zarówno w `CView` klasie pochodnej (CMainView), jak i `COleClientItem` klasie pochodnej (CRectItem). Wszystkie te zastąpienia są udostępniane przez AppWizard i większość implementacji będzie pochodzić bezpośrednio z domyślnej aplikacji AppWizard.

W pierwszym kroku tego portu aktywacja w miejscu została wyłączona całkowicie przez zastąpienie `COleClientItem::CanActivate` . To zastąpienie powinno zostać usunięte, aby umożliwić aktywację w miejscu. Ponadto wartość NULL została przeniesiona do wszystkich wywołań do `DoVerb` (Istnieją dwa z nich), ponieważ udostępnienie widoku było wymagane tylko w przypadku aktywacji w miejscu. Aby w pełni zaimplementować aktywację w miejscu, konieczne jest przekazanie poprawnego widoku w `DoVerb` wywołaniu. Jedno z tych wywołań jest w `CMainView::OnInsertObject` :

```cpp
pItem->DoVerb(OLEIVERB_SHOW, this);
```

Drugi jest w `CMainView::OnLButtonDblClk` :

```cpp
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);
```

Konieczne jest przesłonięcie `COleClientItem::OnGetItemPosition` . Informuje to serwer, na którym należy umieścić okno względem okna kontenera, gdy element jest aktywowany w miejscu. W przypadku OCLIENT implementacja jest prosta:

```cpp
void CRectItem::OnGetItemPosition(CRect& rPosition)
{
    rPosition = m_rect;
}
```

Większość serwerów implementuje również to, co jest nazywane "zmianą w miejscu". Umożliwia to rozmiar i przeniesienie okna serwera, gdy użytkownik edytuje element. Kontener musi brać udział w tej akcji, ponieważ przeniesienie lub zmiana rozmiaru okna zwykle wpływa na położenie i rozmiar w obrębie samego dokumentu kontenera. Implementacja OCLIENT synchronizuje wewnętrzny prostokąt, który jest obsługiwany przez m_rect z nową pozycją i rozmiarem.

```cpp
BOOL CRectItem::OnChangeItemPosition(const CRect& rectPos)
{
    ASSERT_VALID(this);

    if (!COleClientItem::OnChangeItemPosition(rectPos))
        return FALSE;

    Invalidate();
    m_rect = rectPos;
    Invalidate();
    GetDocument()->SetModifiedFlag();

    return TRUE;
}
```

W tym momencie jest wystarczająco duży kod, aby umożliwić aktywowanie elementu w miejscu i zaradzić sobie z rozmiarem i przeniesieniem elementu, gdy jest aktywny, ale żaden kod nie zezwoli użytkownikowi na zakończenie sesji edytowania. Mimo że niektóre serwery będą zapewniały te funkcje przez obsługę klucza ucieczki, zaleca się, aby kontenery zapewniały dwa sposoby dezaktywowania elementu: (1) przez kliknięcie elementu poza elementem i (2) przez naciśnięcie klawisza UCIECZKi.

Dla klawisza UCIECZKi Dodaj akcelerator z Visual C++, który mapuje klucz VK_ESCAPE na polecenie, ID_CANCEL_EDIT zostanie dodany do zasobów. Procedura obsługi dla tego polecenia jest następująca:

```cpp
// The following command handler provides the standard
// keyboard user interface to cancel an in-place
// editing session.void CMainView::OnCancelEdit()
{
    // Close any in-place active item on this view.
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->Close();
    ASSERT(GetDocument()->GetInPlaceActiveItem(this) == NULL);
}
```

Aby obsłużyć przypadek, w którym użytkownik kliknie poza elementem, należy dodać następujący kod na początku `CMainView::SetSelection` :

```cpp
if (pNewSel != m_pSelection || pNewSel == NULL)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL&& pActiveItem != pNewSel)
        pActiveItem->Close();
}
```

Gdy element jest aktywny, powinien mieć fokus. Aby upewnić się, że jest to przypadek obsługujący funkcji OnSetFocus, dzięki czemu fokus jest zawsze przenoszony do aktywnego elementu, gdy widok otrzymuje fokus:

```cpp
// Special handling of OnSetFocus and OnSize are required
// when an object is being edited in-place.
void CMainView::OnSetFocus(CWnd* pOldWnd)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);

    if (pActiveItem != NULL &&
        pActiveItem->GetItemState() == COleClientItem::activeUIState)
    {
        // need to set focus to this item if it is same view
        CWnd* pWnd = pActiveItem->GetInPlaceWindow();
        if (pWnd != NULL)
        {
            pWnd->SetFocus();   // don't call the base class
            return;
        }
    }

    CView::OnSetFocus(pOldWnd);
}
```

Gdy zmieniany jest rozmiar widoku, należy powiadomić aktywny element, że prostokąt wycinka został zmieniony. W tym celu należy udostępnić program obsługi dla `OnSize` :

```cpp
void CMainView::OnSize(UINT nType, int cx, int cy)
{
    CView::OnSize(nType, cx, cy);
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->SetItemRects();
}
```

## <a name="case-study-hiersvr-from-mfc-20"></a>Analiza przypadku: HIERSVR z MFC 2,0

[HIERSVR](../overview/visual-cpp-samples.md) również został uwzględniony w MFC 2,0 i zaimplementowane OLE z MFC/OLE1. W tej uwadze krótko opisano kroki, za pomocą których ta aplikacja była początkowo konwertowana do używania klas MFC/OLE 2. Po zakończeniu wstępnego portu dodano szereg funkcji, aby lepiej zilustrować klasy MFC/OLE 2. Te funkcje nie zostaną omówione w tym miejscu. Zapoznaj się z przykładem, aby uzyskać więcej informacji na temat tych zaawansowanych funkcji.

> [!NOTE]
> Błędy kompilatora i proces krok po kroku został utworzony przy użyciu Visual C++ 2,0. Określone komunikaty o błędach i lokalizacje mogą ulec zmianie w Visual C++ 4,0, ale informacje o pojęciach pozostają poprawne.

### <a name="getting-it-up-and-running"></a>Pobieranie i uruchamianie

Podejście podjęte do przenoszenia przykładu HIERSVR do MFC/OLE jest uruchamiane przez skompilowanie go i naprawianie błędów kompilatora, które będą wynikiem. Jeśli pobierasz próbkę HIERSVR z MFC 2,0 i skompilujesz ją w tej wersji MFC, zobaczysz, że nie ma wielu błędów do rozwiązania (chociaż jest więcej niż z przykładem OCLIENT). Błędy w kolejności, w której zwykle występują, są opisane poniżej.

### <a name="compile-and-fix-errors"></a>Kompiluj i naprawiaj błędy

```Output
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'
```

Ten pierwszy błąd wskazuje na znacznie większy problem z `InitInstance` funkcją dla serwerów. Inicjalizacja wymagana dla serwera OLE jest prawdopodobnie jednym z największych zmian, które trzeba wykonać w aplikacji MFC/OLE1, aby było uruchomione. Najlepszym zagadnieniem jest to, co AppWizard tworzy dla serwera OLE i w razie potrzeby modyfikuje kod. Poniżej przedstawiono niektóre kwestie, o których należy pamiętać:

Konieczne jest zainicjowanie bibliotek OLE, wywołując `AfxOleInit`

Wywołaj SetServerInfo w obiekcie szablonu dokumentu, aby ustawić uchwyty zasobów serwera i informacje o klasie środowiska uruchomieniowego, których nie można ustawić za pomocą `CDocTemplate` konstruktora.

Nie pokazuj okna głównego aplikacji, jeśli przełącznikiem/Embedding jest obecny w wierszu polecenia.

Wymagany jest **Identyfikator GUID** dla dokumentu. To jest unikatowy identyfikator typu dokumentu (128 bitów). AppWizard utworzy aplikację, więc jeśli używasz opisanej tutaj techniki kopiowania nowego kodu z nowej aplikacji serwera wygenerowanej przez AppWizard, możesz po prostu "ukraść" Identyfikator GUID z tej aplikacji. Jeśli nie, możesz użyć narzędzia GUIDGEN.EXE w katalogu BIN.

Należy "połączyć" `COleTemplateServer` obiekt z szablonem dokumentu przez wywołanie `COleTemplateServer::ConnectTemplate` .

Zaktualizuj rejestr systemu, gdy aplikacja jest uruchamiana autonomicznie. W ten sposób, jeśli użytkownik przenosi. Program EXE dla aplikacji, który uruchamia go z nowej lokalizacji, zaktualizuje bazę danych rejestracji systemu Windows, aby wskazywała nową lokalizację.

Po zastosowaniu wszystkich tych zmian w zależności od tego, co AppWizard tworzy dla programu `InitInstance` , `InitInstance` (i powiązany identyfikator GUID) dla HIERSVR powinien zostać odczytany w następujący sposób:

```cpp
// this is the GUID for HIERSVR documents
static const GUID BASED_CODE clsid =
{ 0xA0A16360L, 0xC19B, 0x101A, { 0x8C, 0xE5, 0x00, 0xDD, 0x01, 0x11, 0x3F, 0x12 } };

/////////////////////////////////////////////////////////////////////////////
// COLEServerApp initialization

BOOL COLEServerApp::InitInstance()
{
    // OLE 2 initialization
    if (!AfxOleInit())
    {
        AfxMessageBox("Initialization of the OLE failed!");
        return FALSE;
    }

    // Standard initialization
    LoadStdProfileSettings();   // Load standard INI file options

    // Register document templates
    CDocTemplate* pDocTemplate;
    pDocTemplate = new CMultiDocTemplate(IDR_HIERSVRTYPE,
        RUNTIME_CLASS(CServerDoc),
        RUNTIME_CLASS(CMDIChildWnd),
        RUNTIME_CLASS(CServerView));
    pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB);
    AddDocTemplate(pDocTemplate);

    // create main MDI Frame window
    CMainFrame* pMainFrame = new CMainFrame;
    if (!pMainFrame->LoadFrame(IDR_MAINFRAME))
        return FALSE;
    m_pMainWnd = pMainFrame;

    SetDialogBkColor(); // gray look

    // enable file manager drag/drop and DDE Execute open
    m_pMainWnd->DragAcceptFiles();
    EnableShellOpen();

    m_server.ConnectTemplate(clsid, pDocTemplate, FALSE);
    COleTemplateServer::RegisterAll();

    // try to launch as an OLE server
    if (RunEmbedded())
    {
        // "short-circuit" initialization -- run as server!
        return TRUE;
    }
    m_server.UpdateRegistry();
    RegisterShellFileTypes();

    // not run as OLE server, so show the main window
    if (m_lpCmdLine[0] == '\0')
    {
        // create a new (empty) document
        OnFileNew();
    }
    else
    {
        // open an existing document
        OpenDocumentFile(m_lpCmdLine);
    }

    pMainFrame->ShowWindow(m_nCmdShow);
    pMainFrame->UpdateWindow();

    return TRUE;
}
```

Zobaczysz, że powyższy kod odwołuje się do nowego identyfikatora zasobu, IDR_HIERSVRTYPE_SRVR_EMB. Jest to zasób menu, który ma być używany, gdy edytowany jest dokument osadzony w innym kontenerze. W MFC/OLE1 elementy menu specyficzne dla edycji osadzonego elementu zostały zmodyfikowane na bieżąco. Użycie całkowicie różnej struktury menu podczas edytowania elementu osadzonego zamiast edytowania dokumentu opartego na plikach ułatwia udostępnianie różnych interfejsów użytkownika dla tych dwóch oddzielnych trybów. Jak zobaczysz później, w trakcie edycji osadzonego obiektu w miejscu zostanie użyty całkowicie oddzielny zasób menu.

Aby utworzyć ten zasób, Załaduj skrypt zasobów do Visual C++ i skopiuj istniejący zasób menu IDR_HIERSVRTYPE. Zmień nazwę nowego zasobu na IDR_HIERSVRTYPE_SRVR_EMB (jest to taka sama Konwencja nazewnictwa, której używa AppWizard). Dalej Zmień "plik Zapisz" na "Aktualizacja plików"; Nadaj mu identyfikator polecenia ID_FILE_UPDATE. Zmień również plik "Zapisz jako" na "plik Zapisz kopię jako"; Nadaj mu identyfikator polecenia ID_FILE_SAVE_COPY_AS. Struktura zawiera implementację obu tych poleceń.

```Output
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers
```

Istnieje wiele błędów wynikających z przesłonięcia `OnSetData` , ponieważ odwołuje się do typu **OleStatus** . **OleStatus** był sposób, w jaki OLE1 zwrócił błędy. Ten element został zmieniony na **HRESULT** w OLE 2, chociaż MFC zwykle konwertuje **wynik HRESULT** na `COleException` błąd. W tym konkretnym przypadku przesłonięcie `OnSetData` nie jest już konieczne, więc najprostszym rozwiązaniem jest jego usunięcie.

```Output
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters
```

`COleServerItem`Konstruktor pobiera dodatkowy parametr "bool". Ta flaga określa sposób zarządzania pamięcią w `COleServerItem` obiektach. Po ustawieniu na wartość TRUE Framework obsługuje zarządzanie pamięcią tych obiektów, usuwając je, gdy nie są już potrzebne. HIERSVR używa `CServerItem` obiektów pochodnych (pochodzących z `COleServerItem` ) jako części danych natywnych, więc ustawisz flagę na wartość false. Dzięki temu HIERSVR określić, kiedy każdy element serwera jest usuwany.

```Output
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
```

Ponieważ te błędy oznaczają, istnieją pewne funkcje "czysty-wirtualny", które nie zostały zastąpione w CServerItem. Najprawdopodobniej wynika to z faktu, że lista parametrów OnDraw została zmieniona. Aby naprawić ten błąd, należy zmienić `CServerItem::OnDraw` w następujący sposób (a także deklarację w svritem. h):

```cpp
BOOL CServerItem::OnDraw(CDC* pDC, CSize& rSize)
{
    // request from OLE to draw node
    pDC->SetMapMode(MM_TEXT); // always in pixels
    return DoDraw(pDC, CPoint(0, 0), FALSE);
}
```

Nowy parametr to "elementu rsize". Pozwala to na wypełnienie rozmiaru rysunku, o ile jest to wygodne. Ten rozmiar musi być w **HIMETRIC**. W tym przypadku nie jest to wygodne do wypełnienia tej wartości w, więc struktura wywołuje w `OnGetExtent` celu pobrania zakresu. Aby to działało, należy wdrożyć `OnGetExtent` :

```cpp
BOOL CServerItem::OnGetExtent(DVASPECT dwDrawAspect, CSize& rSize)
{
    if (dwDrawAspect != DVASPECT_CONTENT)
        return COleServerItem::OnGetExtent(dwDrawAspect, rSize);

    rSize = CalcNodeSize();
    return TRUE;
}
```

```Output
\hiersvr\svritem.cpp(104) : error C2065: 'm_rectBounds' : undeclared identifier
\hiersvr\svritem.cpp(104) : error C2228: left of '.SetRect' must have class/struct/union type
\hiersvr\svritem.cpp(106) : error C2664: 'void __pascal __far DPtoLP(struct ::tagPOINT __far *,
    int)__far const ' : cannot convert parameter 1 from 'int __far *' to 'struct ::tagPOINT __far *'
```

W funkcji CServerItem:: CalcNodeSize rozmiar elementu jest konwertowany na **HIMETRIC** i przechowywany w *m_rectBounds*. Nieudokumentowany element członkowski "*m_rectBounds*" `COleServerItem` nie istnieje (częściowo zastąpiony przez *M_SIZEEXTENT*, ale w OLE 2 ten element członkowski ma nieco inne użycie niż *m_rectBounds* OLE1). Zamiast ustawiania rozmiaru **HIMETRIC** w tej zmiennej składowej, należy ją zwrócić. Ta wartość zwracana jest używana w `OnGetExtent` , wcześniej wdrożone.

```cpp
CSize CServerItem::CalcNodeSize()
{
    CClientDC dcScreen(NULL);

    m_sizeNode = dcScreen.GetTextExtent(m_strDescription,
        m_strDescription.GetLength());
    m_sizeNode += CSize(CX_INSET * 2, CY_INSET * 2);

    // set suggested HIMETRIC size
    CSize size(m_sizeNode.cx, m_sizeNode.cy);
    dcScreen.SetMapMode(MM_HIMETRIC);
    dcScreen.DPtoLP(&size);
    return size;
}
```

CServerItem również zastąpień `COleServerItem::OnGetTextData` . Ta funkcja jest przestarzała w MFC/OLE i jest zastępowana przez inny mechanizm. Wersja MFC 3,0 przykładu MFC OLE [HIERSVR](../overview/visual-cpp-samples.md) implementuje tę funkcję przez zastąpienie `COleServerItem::OnRenderFileData` . Ta funkcja nie jest ważna dla tego podstawowego portu, więc można usunąć zastąpienie OnGetTextData.

Istnieje dużo więcej błędów w svritem. cpp, które nie zostały rozkierowane. Nie są to "prawdziwe" błędy — tylko błędy spowodowane przez poprzednie błędy.

```Output
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters
```

`COleServerItem::CopyToClipboard` nie obsługuje już `bIncludeNative` flagi. Dane natywne (dane zapisywane przez funkcję serializacji elementu serwera) są zawsze kopiowane, dlatego należy usunąć pierwszy parametr. Ponadto program `CopyToClipboard` zgłosi wyjątek, gdy wystąpi błąd, zamiast zwracać wartość false. Zmień kod dla CServerView:: OnEditCopy w następujący sposób:

```cpp
void CServerView::OnEditCopy()
{
    if (m_pSelectedNode == NULL)
        AfxThrowNotSupportedException();

    TRY
    {
        m_pSelectedNode->CopyToClipboard(TRUE);
    }
    CATCH_ALL(e)
    {
        AfxMessageBox("Copy to clipboard failed");
    }
    END_CATCH_ALL
}
```

Mimo że wystąpiły błędy związane z kompilacją wersji MFC 2,0 HIERSVR niż w przypadku tej samej wersji OCLIENT, wprowadzono mniej zmian.

W tym momencie HIERSVR kompiluje i łączy i działa jako serwer OLE, ale bez funkcji edycji w miejscu, która zostanie wdrożona dalej.

### <a name="adding-visual-editing"></a>Dodawanie "edycji wizualnej"

Aby dodać "edycję wizualizacji" (lub aktywację w miejscu) do tej aplikacji serwera, należy wziąć pod uwagę tylko kilka rzeczy:

- Potrzebujesz specjalnego zasobu menu, który będzie używany, gdy element jest aktywny.

- Ta aplikacja ma pasek narzędzi, Dlatego potrzebny jest pasek narzędzi z tylko podzbiorem normalnego paska narzędzi, aby dopasować polecenia menu dostępne na serwerze (zgodne z powyższym zasobem menu).

- Potrzebna jest nowa klasa pochodna, `COleIPFrameWnd` która zapewnia interfejs użytkownika w miejscu (podobnie jak CMainFrame, pochodny od `CMDIFrameWnd` , udostępnia interfejs użytkownika MDI).

- Należy popowiedzieć platformę dotyczącą tych specjalnych zasobów i klas.

Zasób menu jest łatwy do utworzenia. Uruchom Visual C++, skopiuj zasób menu IDR_HIERSVRTYPE do zasobu menu o nazwie IDR_HIERSVRTYPE_SRVR_IP. Zmodyfikuj menu tak, aby tylko okna podręczne menu Edycja i pomoc zostały pozostawione. Dodaj dwa separatory do menu w oknie Edycja i pomoc (powinny wyglądać następująco: Edycja pomocy &#124;&#124; ). Aby uzyskać więcej informacji o tym, co oznaczają te separatory i jak są scalane menu serwera i kontenera, zobacz menu [i zasoby: scalanie menu](../mfc/menus-and-resources-menu-merging.md).

Mapę bitową dla podzestawu na pasku narzędzi można łatwo utworzyć przez skopiowanie jednego z AppWizard wygenerowanej aplikacji z opcją "serwer". Tę mapę bitową można następnie zaimportować do Visual C++. Upewnij się, że mapa bitowa ma identyfikator IDR_HIERSVRTYPE_SRVR_IP.

Klasa pochodna z `COleIPFrameWnd` może zostać skopiowana z aplikacji wygenerowanej przez AppWizard z obsługą serwera. Skopiuj oba pliki, IPFRAME. CPP i IPFRAME. H i Dodaj do projektu. Upewnij się, że `LoadBitmap` wywołanie odwołuje się do IDR_HIERSVRTYPE_SRVR_IP, mapa bitowa utworzona w poprzednim kroku.

Teraz, gdy zostaną utworzone wszystkie nowe zasoby i klasy, Dodaj wymagany kod, aby platforma wie o tych (i wie, że ta aplikacja obsługuje teraz edycję w miejscu). Jest to realizowane przez dodanie kilku parametrów do `SetServerInfo` wywołania w `InitInstance` funkcji:

```cpp
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,
    IDR_HIERSVRTYPE_SRVR_IP,
    RUNTIME_CLASS(CInPlaceFrame));
```

Jest teraz gotowa do uruchamiania w miejscu w dowolnym kontenerze, który również obsługuje aktywację w miejscu. Jednak istnieje jedna drobna usterka nadal lurking w kodzie. HIERSVR obsługuje menu kontekstowe, wyświetlane, gdy użytkownik naciśnie prawy przycisk myszy. To menu działa, gdy HIERSVR jest w pełni otwarte, ale nie działa podczas edytowania osadzania w miejscu. Przyczyna może być przypięta do tego samego wiersza kodu w CServerView:: OnRButtonDown:

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetApp()->m_pMainWnd);
```

Zwróć uwagę na odwołanie do `AfxGetApp()->m_pMainWnd` . Gdy serwer jest aktywowany w miejscu, ma okno główne, a m_pMainWnd jest ustawiony, ale jest zwykle niewidoczny. Ponadto to okno odnosi się do *głównego* okna aplikacji, okna ramki MDI, które pojawia się, gdy serwer jest w pełni otwarty lub uruchamiany autonomicznie. Nie odwołuje się do aktywnego okna ramki, które w miejscu aktywowanym jest oknem ramki pochodnym `COleIPFrameWnd` . Aby uzyskać poprawne aktywne okno, nawet w przypadku edycji w miejscu, ta wersja MFC dodaje nową funkcję, `AfxGetMainWnd` . Ogólnie rzecz biorąc należy używać tej funkcji zamiast `AfxGetApp()->m_pMainWnd` . Ten kod musi ulec zmianie w następujący sposób:

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetMainWnd());
```

Teraz można korzystać z serwera OLE w minimalnym stopniu dla funkcjonalnej aktywacji w miejscu. Jednak nadal dostępnych jest wiele funkcji MFC/OLE 2, które nie były dostępne w MFC/OLE1. Zobacz przykład HIERSVR, aby poznać więcej pomysłów na temat funkcji, które warto zaimplementować. Poniżej wymieniono niektóre z funkcji, które HIERSVR implementuje:

- Powiększanie, w przypadku rzeczywistego zachowania WYSIWYG w odniesieniu do kontenera.

- Przeciąganie/upuszczanie i niestandardowy format schowka.

- Przewijanie okna kontenera w miarę zmiany zaznaczenia.

Przykład HIERSVR w MFC 3,0 używa również nieco innego projektu dla elementów serwera. Pozwala to zaoszczędzić pamięć i sprawia, że linki są bardziej elastyczne. W przypadku wersji 2,0 HIERSVR każdy węzeł w drzewie *to-a* `COleServerItem` . `COleServerItem` wykonuje nieco bardziej narzuty, niż jest to absolutnie konieczne dla każdego z tych węzłów, ale `COleServerItem` jest wymagany dla każdego aktywnego linku. Jednak w większości przypadków aktywne linki są dostępne w danym momencie. Aby zwiększyć efektywność, HIERSVR w tej wersji MFC oddziela węzeł od `COleServerItem` . Ma zarówno CServerNode, jak i `CServerItem` klasę. `CServerItem`(Pochodny od `COleServerItem` ) jest tworzony tylko w razie potrzeby. Gdy kontener (lub kontenery) zakończy korzystanie z tego konkretnego linku do tego określonego węzła, obiekt CServerItem skojarzony z CServerNode jest usuwany. Ten projekt jest bardziej wydajny i bardziej elastyczny. Jego elastyczność jest dostępna podczas pracy z wieloma łączami wyboru. Żadna z tych dwóch wersji programu HIERSVR nie obsługuje wielokrotnego wyboru, ale byłoby znacznie łatwiejsze do dodania (i do obsługi linków do takich opcji) z wersją MFC 3,0 HIERSVR, ponieważ `COleServerItem` jest oddzielona od danych natywnych.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numeru](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
