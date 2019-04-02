---
title: 'TN041: MFC / Ole1 do MFC / OLE 2'
ms.date: 10/18/2018
f1_keywords:
- vc.mfc.ole
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
ms.openlocfilehash: b398a1adbf2f47343eed076f32ade5bb2564cd52
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767980"
---
# <a name="tn041-mfcole1-migration-to-mfcole-2"></a>TN041: MFC/Ole1 do MFC/OLE 2

> [!NOTE]
> Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

## <a name="general-issues-relating-to-migration"></a>Ogólne problemy dotyczące migracji

Jednym z celów projektowania dla klas OLE 2 w wersji 2.5 MFC (lub nowsza) było przechowywać wiele taką samą architekturę wprowadzone w MFC w wersji 2.0 dla pomocy technicznej w wersji 1.0 OLE. W rezultacie wiele z tych samych klas OLE w MFC w wersji 2.0 nadal istnieć w tej wersji biblioteki MFC (`COleDocument`, `COleServerDoc`, `COleClientItem`, `COleServerItem`). Ponadto wiele interfejsów API w ramach tych zajęć są dokładnie takie same. Jednak OLE 2 różni się znacząco od OLE 1.0, dzięki czemu można spodziewać się, że niektóre szczegóły zostały zmienione. Osoby zaznajomione z obsługą OLE1 MFC 2.0 będzie uważasz, że w domu z obsługą 2.0 biblioteki MFC.

Jeśli jesteś biorąc istniejącej aplikacji MFC/OLE1 i dodawanie funkcji OLE 2 do niego, należy najpierw przeczytaj tę uwagę. Ta uwaga opisano niektóre ogólne problemy mogą wystąpić podczas przenoszenia własne funkcje OLE1 do MFC/OLE 2, a następnie omówiono problemy niewykrytych podczas przenoszenia dwie aplikacje uwzględnione w MFC w wersji 2.0: przykłady MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) i [HIERSVR](../overview/visual-cpp-samples.md).

## <a name="mfc-documentview-architecture-is-important"></a>Ważne jest, architektury dokument/widok MFC

Jeśli aplikacja nie używa architektury dokument/widok MFC i chcesz dodać obsługę OLE 2 do swojej aplikacji, nadszedł czas, aby przejść do dokumentu/widoku. Wiele korzyści klasy MFC-OLE 2 tylko są realizowane, gdy aplikacja wykorzystuje wbudowanych architektury i składników MFC.

Implementowanie serwera lub kontenera bez korzystania z architektury MFC jest możliwe, ale niezalecane.

## <a name="use-mfc-implementation-instead-of-your-own"></a>Użyj MFC — implementacja zamiast własne

Klasy MFC "puszkach wykonania", takie jak `CToolBar`, `CStatusBar`, i `CScrollView` wbudowanych specjalnych przypadków kod obsługi OLE 2. Tak Jeśli używasz tych klas w aplikacji będą korzystać z umieścić w nich działań zmierzających do uświadomić im OLE. Ponownie możliwe jest "roll własnej" klas w tym miejscu dla tych celów, ale nie jest zalecane. Jeśli musisz zaimplementować podobne funkcje, kodzie źródłowym MFC jest doskonałą odwołaniem radzenia sobie z niektórych bardziej precyzyjną punktów OLE (zwłaszcza jeśli chodzi o aktywacji w miejscu).

## <a name="examine-the-mfc-sample-code"></a>Wypróbowaniem przykładowego kodu MFC

Istnieje kilka przykładów MFC, które obejmują funkcje OLE. Każda z tych aplikacji implementuje OLE z o określony kąt:

- [HIERSVR](../overview/visual-cpp-samples.md) przeznaczony głównie do użytku jako aplikacja serwera. Została uwzględniona w MFC w wersji 2.0 jako aplikacja MFC/OLE1 i został przenoszone do MFC/OLE 2 i następnie rozszerzone w taki sposób, że implementuje w OLE 2 wiele funkcji OLE.

- [OCLIENT](../overview/visual-cpp-samples.md) jest to aplikacja autonomiczna kontenera, przeznaczony do zademonstrowania wiele funkcji OLE z punktu widzenia kontenera. Zbyt został on przenoszone z MFC w wersji 2.0, a następnie rozszerzyć w celu obsługi wielu bardziej zaawansowanych funkcji OLE, takich jak formaty Schowka niestandardowych i łącza do elementów osadzonych.

- [DRAWCLI](../overview/visual-cpp-samples.md) tej aplikacji implementuje obsługi kontenerów OLE znacznie jak OCLIENT tak, z tą różnicą, że odbywa się to w ramach istniejącego programu rysowania zorientowane obiektowo. Przedstawia on sposób może zaimplementować Obsługa kontenerów OLE i zintegrować ją z istniejącej aplikacji.

- [SUPERPAD](../overview/visual-cpp-samples.md) tej aplikacji, a także jest dobrym rozwiązaniem aplikacji autonomicznej, jest również serwerem OLE. Obsługa serwera, który implementuje są minimalist to jeszcze gotowe. Szczególne znaczenie w odniesieniu się, jak używa usług Schowka OLE do kopiowania danych do Schowka, ale używa funkcji wbudowanych w kontrolce Windows "edit" do implementacji funkcji Wklej Schowka. Spowoduje to pokazanie interesujących kombinacji tradycyjnych użycie interfejsu API Windows, a także integrację z nowych OLE interfejsów API.

Aby uzyskać więcej informacji na temat przykładowych aplikacji zobacz "MFC próbki pomoc".

## <a name="case-study-oclient-from-mfc-20"></a>Analiza przypadku: OCLIENT z MFC w wersji 2.0

Jak wspomniano powyżej, [OCLIENT](../overview/visual-cpp-samples.md) została uwzględniona w MFC w wersji 2.0 i wdrażane w OLE z MFC/OLE1. Poniżej opisano kroki, według których ta aplikacja początkowo został skonwertowany do używania klas MFC/OLE 2. Wiele funkcji zostały dodane po początkowej portu zostało ukończone, aby lepiej zilustrować klasy MFC/OLE. Te funkcje nie zostały omówione w tym miejscu; Zobacz na przykład aby uzyskać więcej informacji na temat tych zaawansowanych funkcji.

> [!NOTE]
> Błędy kompilatora i instrukcje krok po kroku proces został utworzony przy użyciu programu Visual C++ wersji 2.0. Określone komunikaty o błędach i lokalizacje mógł ulec zmianie z Visual C++ 4.0, ale informacje koncepcyjne poniżej pozostaje ważny.

## <a name="getting-it-up-and-running"></a>Go i przeprowadzanie

To podejście do portu OCLIENT próbki MFC/OLE na początek wbudowanie jej i naprawianie błędów kompilatora oczywiste, które będą powodować. Jeśli pobierania próbki OCLIENT z MFC w wersji 2.0 i skompilować go w tej wersji MFC, przekonasz się, że nie są to wiele błędów, aby rozwiązać. Błędy w kolejności, w której miały miejsce zostały opisane poniżej.

## <a name="compile-and-fix-errors"></a>Kompilacji i poprawki błędów

```Output
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters
```

Pierwszy dotyczy błąd `COleClientItem::Draw`. MFC/OLE1 zajęło więcej parametrów niż trwa wersji MFC/OLE. Dodatkowe parametry często nie były konieczne i zwykle o wartości NULL (jak w poniższym przykładzie). Tej wersji biblioteki MFC można automatycznie określić wartości lpWBounds po przechwytywania zmian danych, który jest rysowana metaplik kontrolera domeny. Ponadto parametru pFormatDC nie jest już konieczne ponieważ struktura będzie zbudować ją od "atrybut DC" PDC przekazanej. Tak, aby rozwiązać ten problem, po prostu usuń dwa dodatkowe wartości NULL parametrów wywołania rysowania.

```Output
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier
\oclient\mainview.cpp(273) : error C2057: expected constant expression
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
```

Błędy powyżej wynikają z faktu, wszystkie `COleClientItem::CreateXXXX` funkcji MFC/OLE1 wymagane, że unikatową nazwę można przekazać do reprezentowania elementu. Jest to wymaganie bazowego OLE interfejsu API. Jest to konieczne w MFC/OLE 2, ponieważ OLE 2 nie używa DDE jako podstawowy mechanizm komunikacji (nazwa została użyta w konwersacji). Aby rozwiązać ten problem, można usunąć `CreateNewName` funkcji, a także wszystkie odwołania do niego. To proste dowiedzieć się, co każdej funkcji MFC/OLE jest oczekiwana w tej wersji poprzez umieszczenie kursora na wywołanie i naciskając klawisz F1.

Inny obszar, który różni się znacząco jest obsługa Schowka OLE 2. Za pomocą OLE1 użyto Schowka Windows który interfejsów API wchodzić w interakcje ze Schowka. Przy użyciu OLE 2 jest to realizowane przy użyciu innego mechanizmu. Interfejsy API MFC/OLE1 zakłada, że Schowka był otwarty przed skopiowaniem `COleClientItem` obiektu do Schowka. To nie jest już konieczne i spowoduje, że wszystkie operacje na schowku MFC/OLE nie powiedzie się. Podczas edycji kodu, aby usunąć zależności na `CreateNewName`, należy także usunąć kod, który otwiera i zamyka Schowka Windows.

```Output
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function
\oclient\mainview.cpp(344) : error C2057: expected constant expression
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'
```

Te błędy są wynikiem `CMainView::OnInsertObject` programu obsługi. Obsługa polecenia "Wstaw nowy obiekt" jest inny obszar, w którym rzeczy uległy zmianie jeszcze chwilę. W tym przypadku jest najprostszym scalania oryginalnego wdrożenia z podanym przez AppWizard dla nowej aplikacji kontenera OLE. W rzeczywistości jest to technika, który można zastosować do przenoszenia innych aplikacji. W MFC/OLE1 okna dialogowego "Wstawianie obiektu" wyświetlony po wywołaniu `AfxOleInsertDialog` funkcji. W tej wersji można skonstruować `COleInsertObject` obiektu okna dialogowego, a następnie wywołać `DoModal`. Ponadto nowe elementy OLE są tworzone za pomocą **CLSID** zamiast ciągu classname. Wynik końcowy powinien wyglądać mniej więcej tak

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
> Wstaw nowy obiekt mogą być różne dla aplikacji):

Należy również uwzględnić \<afxodlgs.h >, który zawiera deklarację dla `COleInsertObject` klasy okien dialogowych, a także innych standardowych oknach dialogowych dostarczonych przez MFC.

```Output
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters
```

Te błędy są spowodowane przez fakt, że niektóre stałe OLE1 zostały zmienione w wersji OLE 2, mimo że pojęcia są takie same. W tym przypadku `OLEVERB_PRIMARY` została zmieniona na `OLEIVERB_PRIMARY`. OLE1 i OLE 2 primary — zlecenie jest zazwyczaj wykonywane przez kontener po użytkownik kliknie element.

Ponadto `DoVerb` przyjmuje teraz dodatkowy parametr — wskaźnik do widoku (`CView`*). Ten parametr jest używany tylko w celu zaimplementowania "Edycja wizualna" (lub aktywacji w miejscu). Teraz możesz ustawić tego parametru wartości NULL, ponieważ nie wdrażają tej funkcji w tej chwili.

Aby upewnić się, że struktura nigdy nie próbuje w miejscu aktywować, należy zastąpić `COleClientItem::CanActivate` w następujący sposób:

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

W MFC/OLE1 `COleClientItem::GetBounds` i `SetBounds` były używane do wykonywania zapytań i manipulowania w zakresie elementu ( `left` i `top` elementy Członkowskie były zawsze zero). MFC/OLE 2 jest to bardziej bezpośrednio obsługiwane przez `COleClientItem::GetExtent` i `SetExtent`, którego dotyczy **rozmiar** lub `CSize` zamiast tego.

Kod dla Twojego nowego SetItemRectToServer i wywołania UpdateItemRectFromServer wyglądać następująco:

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

W interfejsie API synchroniczne MFC/OLE1 wywołania z kontenera do serwera zostały *symulowane*, ponieważ OLE1 założenia asynchroniczne w wielu przypadkach. Konieczne było pod kątem zaległych wywołania asynchronicznego w toku przed przetworzeniem polecenia przez użytkownika. MFC/OLE1 podane `COleClientItem::InWaitForRelease` funkcji, aby to zrobić. MFC/OLE 2 nie jest to konieczne, aby móc usunąć zastąpienie OnCommand cmainframe — wszystko ze sobą.

W tym momencie OCLIENT kompilacji i połącz.

## <a name="other-necessary-changes"></a>Inne wymagane zmiany

Istnieje kilka kwestii, które nie zostały wykonane, które zapewnią OCLIENT z pracy, jednak. Zaleca się rozwiązać te problemy, teraz zamiast później.

Najpierw należy zainicjować bibliotek OLE. Jest to realizowane przez wywołanie `AfxOleInit` z `InitInstance`:

```cpp
if (!AfxOleInit())
{
    AfxMessageBox("Failed to initialize OLE libraries");
    return FALSE;
}
```

Jest również dobrym pomysłem pod kątem funkcji wirtualnych dla zmiany listy parametrów. Jednej z tych funkcji jest `COleClientItem::OnChange`, zastąpione w każdej aplikacji kontenera MFC/OLE. Patrząc na pomoc online, zobaczysz, czy dodatkowy "DWORD dwParam" został dodany. Nowe CRectItem::OnChange wygląda następująco:

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

W MFC/OLE1 aplikacji kontenerowych pochodne klasy dokumentów z `COleClientDoc`. MFC/OLE 2 ta klasa została usunięta i zastąpiona `COleDocument` (tej nowej organizacji sprawia, że łatwiej tworzyć aplikacje kontenera/serwera). Brak **#define** mapujący `COleClientDoc` do `COleDocument` ułatwiają przenoszenie aplikacji MFC/OLE1 do MFC/OLE 2, takie jak OCLIENT. Jedna z funkcji nie są dostarczane przez `COleDocument` która przekazała `COleClientDoc` jest komunikatem polecenia standardowe wpisy mapy. Odbywa się to przez aplikacje serwera, które także używają `COleDocument` (bezpośrednio), nie pociągają za sobą obciążenie programy obsługi tych poleceń, chyba że są one aplikacji kontenera/serwera. Należy dodać następujące wpisy na mapie komunikatów CMainDoc:

```cpp
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE, OnUpdatePasteMenu)
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK, OnUpdatePasteLinkMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS, OnUpdateEditLinksMenu)
ON_COMMAND(ID_OLE_EDIT_LINKS, COleDocument::OnEditLinks)
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST, OnUpdateObjectVerbMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT, OnUpdateObjectVerbMenu)
ON_COMMAND(ID_OLE_EDIT_CONVERT, OnEditConvert)
```

Trwa wykonania wszystkich poleceń `COleDocument`, która jest klasą bazową dla dokumentu.

W tym momencie OCLIENT jest funkcjonalności aplikacji kontenera OLE. Jest możliwe wstawianie elementów dowolnego typu (OLE1 lub OLE 2). Ponieważ nie zaimplementowano niezbędne kodu w celu włączenia aktywacji w miejscu, w osobnym oknie, jak wiele OLE1 edytowania elementów. W następnej sekcji omówiono niezbędne zmiany, aby umożliwić edycję w miejscu (nazywane czasem "Edycja wizualna").

## <a name="adding-visual-editing"></a>Dodawanie "Edycja wizualna"

Jedną z najbardziej interesujących funkcji OLE jest aktywacja w miejscu (lub "Edycja wizualna"). Ta funkcja umożliwia aplikacji serwera do przejęcia części interfejsu użytkownika kontenera podać więcej edycji interfejs użytkownika. Aby zaimplementować aktywacji w miejscu do OCLIENT, specjalne zasoby, należy dodać oraz dodatkowy kod. Te zasoby i kod zwykle są dostarczane przez AppWizard — w rzeczywistości większość tutaj kod został pobierają bezpośrednio z nowej aplikacji przez kreatora AppWizard z obsługą "Container".

Po pierwsze jest to konieczne, można dodać zasobu menu, który ma być używany, gdy istnieje element, który jest aktywny w miejscu. Kopiowanie zasobów IDR_OCLITYPE i usuwając wszystkie z wyjątkiem plików i okno wyskakujące okienka, można utworzyć tego zasobu dodatkowe menu w programie Visual C++. Dwa pasków separatorów są wstawiane do plików i okno wyskakujące okienka do wskazania rozdzielenie grup (powinien wyglądać podobnie jak: File &#124;&#124; Window). Aby uzyskać więcej informacji na temat znaczenie tych separatory i jak scalania menu serwer i kontener zobacz [menu i zasoby: Scalanie menu](../mfc/menus-and-resources-menu-merging.md).

Po utworzeniu tych menu utworzone, możesz podać tę informację framework wiedzieć o nich. Jest to realizowane przez wywołanie `CDocTemplate::SetContainerInfo` dla szablonu dokumentu, aby można go dodać do listy szablonów dokumentów w elemencie InitInstance. Nowy kod, aby zarejestrować szablon dokumentu, który wygląda następująco:

```cpp
CDocTemplate* pTemplate = new CMultiDocTemplate(
    IDR_OLECLITYPE,
    RUNTIME_CLASS(CMainDoc),
    RUNTIME_CLASS(CMDIChildWnd), // standard MDI child frame
    RUNTIME_CLASS(CMainView));

pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);

AddDocTemplate(pTemplate);
```

Zasób IDR_OLECLITYPE_INPLACE jest specjalnym zasobem w miejscu, utworzone w programie Visual C++.

Aby włączyć aktywacji w miejscu, istnieją pewne elementy, które trzeba zmienić zarówno `CView` klasy pochodnej (CMainView), jak również `COleClientItem` klasy (CRectItem). Wszystkie te zastąpienia są dostarczane przez AppWizard, a większość implementacji pojawią się bezpośrednio z aplikacji przez kreatora AppWizard domyślne.

W pierwszym kroku tego portu, aktywacji w miejscu został wyłączony całkowicie przez zastąpienie `COleClientItem::CanActivate`. To zastąpienie powinny zostać usunięte w celu zezwolenia na aktywację w miejscu. Ponadto NULL została przekazana do wszystkich wywołań `DoVerb` (istnieją dwa z nich) powodu dostarczanie widoku tylko niezbędne do aktywacji w miejscu. Aby w pełni zaimplementować aktywacji w miejscu, należy przekazać prawidłowy widok, w `DoVerb` wywołania. Jeden z tych wywołań `CMainView::OnInsertObject`:

```cpp
pItem->DoVerb(OLEIVERB_SHOW, this);
```

Trwa inny `CMainView::OnLButtonDblClk`:

```cpp
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);
```

Należy zastąpić `COleClientItem::OnGetItemPosition`. Instruuje ona serwer, gdzie umieścić okno względem okna kontenera, gdy element jest aktywowany w miejscu. Aby uzyskać OCLIENT wdrożenie jest proste:

```cpp
void CRectItem::OnGetItemPosition(CRect& rPosition)
{
    rPosition = m_rect;
}
```

Większość serwerów wdrożenia, co jest nazywane "w miejscu zmiany rozmiaru." Dzięki temu okno server o rozmiarze i przenoszone, gdy użytkownik edytuje element. Kontener musi uczestniczyć w tej akcji, ponieważ przenoszenia lub zmieniania rozmiaru okna zazwyczaj ma wpływ na położenie i rozmiar, w obrębie samego dokumentu kontenera. Wykonania na OCLIENT synchronizuje wewnętrznego prostokąt, obsługiwane przez m_rect za pomocą nowego położenia i rozmiaru.

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

W tym momencie jest wystarczająca ilość kodu, aby umożliwić element jest aktywowany w miejscu i zmiany rozmiaru i przenoszenie elementu, gdy będzie aktywny, ale żaden kod nie umożliwi użytkownikowi Zakończ sesję edycji. Mimo że niektóre serwery udostępni tę funkcję samodzielnie dzięki obsłudze klawisz escape, zaleca się, że kontenery zapewniają Dezaktywuj element na dwa sposoby: (1) klikając poza elementu i (2), naciskając klawisz ESC.

Klawisz ESCAPE Dodaj akcelerator z programem Visual C++, która mapuje vk_escape — klawisz do polecenia, ID_CANCEL_EDIT jest dodawany do tych zasobów. Obsługa tego polecenia są następujące:

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

Aby obsłużyć przypadek, gdy użytkownik kliknie poza elementu, Dodaj następujący kod na początku `CMainView::SetSelection`:

```cpp
if (pNewSel != m_pSelection || pNewSel == NULL)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL&& pActiveItem != pNewSel)
        pActiveItem->Close();
}
```

Gdy element jest aktywny w miejscu, powinien mieć fokus. Aby upewnić się, że jest to możliwe Obsługa funkcji OnSetFocus tak, aby fokus zawsze jest przekazywany do aktywnego elementu, gdy widok otrzymuje fokus:

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

Przy zmianie rozmiaru widoku należy powiadomić aktywny element, który zmienił się prostokątny. W tym zapewnia funkcję obsługi `OnSize`:

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

## <a name="case-study-hiersvr-from-mfc-20"></a>Analiza przypadku: HIERSVR z MFC w wersji 2.0

[HIERSVR](../overview/visual-cpp-samples.md) również została uwzględniona w MFC w wersji 2.0 i wdrażane w OLE z MFC/OLE1. Ta uwaga krótko opisano kroki, według których ta aplikacja początkowo został skonwertowany do używania klas MFC/OLE 2. Wiele funkcji zostały dodane po początkowej portu zostało ukończone, aby lepiej zilustrować klas MFC/OLE 2. Te funkcje nie zostały omówione w tym miejscu; Zobacz na przykład aby uzyskać więcej informacji na temat tych zaawansowanych funkcji.

> [!NOTE]
> Błędy kompilatora i instrukcje krok po kroku proces został utworzony przy użyciu programu Visual C++ wersji 2.0. Określone komunikaty o błędach i lokalizacje mógł ulec zmianie z Visual C++ 4.0, ale informacje koncepcyjne poniżej pozostaje ważny.

## <a name="getting-it-up-and-running"></a>Go i przeprowadzanie

To podejście do portu HIERSVR próbki MFC/OLE na początek wbudowanie jej i naprawianie błędów kompilatora oczywiste, które będą powodować. Jeśli pobierania próbki HIERSVR z MFC w wersji 2.0 i skompilować go w tej wersji MFC, przekonasz się, że nie są wiele błędów, aby rozwiązać (mimo że ma więcej niż z przykładem OCLIENT). Błędy w kolejności, w którym występują zwykle są opisane poniżej.

## <a name="compile-and-fix-errors"></a>Kompilacji i poprawki błędów

```Output
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'
```

Ten pierwszy błąd wykazuje znacznie większe problem z `InitInstance` funkcji na serwerach. Inicjowanie wymagane przez serwer OLE jest prawdopodobnie jedną z największych zmiany, które należy wprowadzać w aplikacji MFC/OLE1 jego uruchamiania. Najlepiej, aby zrobić to Przyjrzyj się przez kreatora AppWizard tworzy dla serwera OLE i modyfikować kod zgodnie z potrzebami. Poniżej przedstawiono kilka kwestii, o których należy pamiętać:

Należy zainicjować bibliotek OLE przez wywołanie metody `AfxOleInit`

Wywołaj SetServerInfo obiektu szablonu dokumentu, można ustawić obsługuje zasobów serwera i informacje o klasie czasu wykonywania, nie można ustawić za pomocą `CDocTemplate` konstruktora.

Nie pokazuj okna głównego aplikacji, jeśli/Embedding znajduje się w wierszu polecenia.

Będziesz potrzebować **GUID** dokumentu. Jest to unikatowy identyfikator typu dokumentu (128-bitowy). Kreator AppWizard utworzy go dla Ciebie — Jeśli używasz techniki opisanej w tym miejscu kopiowania nowy kod z nową aplikację serwera generowane przez kreatora AppWizard, użytkownik może po prostu "wykradać" identyfikatora GUID z tej aplikacji. W przeciwnym razie możesz użyć GUIDGEN. Narzędzie EXE w katalogu BIN.

Jest to konieczne "połączyć" usługi `COleTemplateServer` obiektu do szablonu dokumentu, wywołując `COleTemplateServer::ConnectTemplate`.

Gdy aplikacja jest uruchomiona w autonomicznej, należy zaktualizować rejestru systemowego. Dzięki temu, gdy użytkownik przesuwa. EXE dla aplikacji, uruchamiając go z nowej lokalizacji spowoduje zaktualizowanie bazy danych rejestracji systemu Windows do punktu do nowej lokalizacji.

Po zastosowaniu wszystkie te zmiany, w oparciu o AppWizard tworzy dla `InitInstance`, `InitInstance` (i związane z identyfikatorem GUID) dla HIERSVR powinien wyglądać następująco:

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

Zauważysz, że powyższy kod odwołuje się do nowych identyfikatorów zasobów, IDR_HIERSVRTYPE_SRVR_EMB. Jest to zasób menu do użycia podczas edycji dokumentu, który jest osadzony w innym kontenerze. W MFC/OLE1 określonych edytować element osadzony elementów menu zostały zmienione na bieżąco. Przy użyciu struktury menu zupełnie innego, podczas edytowania element osadzony zamiast edytowania dokumentu oparte na plikach w znacznie ułatwia zapewnia różnych interfejsów użytkownika dla te dwa różne tryby. Jak zobaczysz później, zasobu menu całkowicie oddzielona jest używany podczas edytowania osadzonego obiektu w miejscu.

Do tworzenia tego zasobu, ładowania skrypt zasobów Visual C++, a następnie skopiować istniejący zasób IDR_HIERSVRTYPE w menu. Zmień nazwę nowego zasobu IDR_HIERSVRTYPE_SRVR_EMB (jest to tej samej konwencji nazewnictwa, która przez kreatora AppWizard używa). Następnie zmień "Zapisz" na "Aktualizuj plik"; Nadaj mu identyfikator id_file_update — polecenie. Również zmienić "Zapisz plik jako" do "Pliku Zapisz kopię jako"; Nadaj mu identyfikator id_file_save_copy_as — polecenie. Struktura dostarcza implementację oba te polecenia.

```Output
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers
```

Liczba błędów wynikających z zastępowania metody `OnSetData`, ponieważ odwołuje się do **OLESTATUS** typu. **OLESTATUS** było możliwości OLE1 zwrócone błędy. Zostało to zmienione na **HRESULT** OLE 2, mimo że MFC zazwyczaj konwertuje **HRESULT** do `COleException` zawierające błąd. W tym konkretnym przypadku zastępowania metody `OnSetData` nie jest już konieczne, więc jest najłatwiejszym, jej usunięcie.

```Output
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters
```

`COleServerItem` Konstruktor przyjmuje jako dodatkowy parametr "BOOL". Ta flaga Określa, jak zarządzanie pamięcią jest wykonywane na `COleServerItem` obiektów. Ustawiając dla niej wartość true, struktura obsługuje zarządzanie pamięcią tych obiektów — ich usuwania, gdy nie są już wymagane. Używa HIERSVR `CServerItem` (pochodną `COleServerItem`) obiektów w ramach jej danych w trybie macierzystym, więc ta flaga będzie ustawiona na wartość FALSE. Dzięki temu HIERSVR określić, gdy każdy element na serwerze zostanie usunięty.

```Output
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
```

Jak sugerują te błędy są niektóre funkcje "czysto wirtualne", które nie zostały zastąpione CServerItem. Prawdopodobnie przyczyną jest fakt, że lista parametrów OnDraw firmy został zmieniony. Aby naprawić ten błąd, zmień `CServerItem::OnDraw` w następujący sposób (a także deklaracji w svritem.h):

```cpp
BOOL CServerItem::OnDraw(CDC* pDC, CSize& rSize)
{
    // request from OLE to draw node
    pDC->SetMapMode(MM_TEXT); // always in pixels
    return DoDraw(pDC, CPoint(0, 0), FALSE);
}
```

Nowy parametr jest "rSize". Dzięki temu można wpisać rozmiar rysunku, jeśli jest to wygodne. Ten rozmiar musi być w **HIMETRIC**. W tym przypadku go nie jest wygodne wypełnić tę wartość, więc struktura wywołuje `OnGetExtent` do pobrania w zakresie. W tym do pracy, musisz zaimplementować `OnGetExtent`:

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

W funkcji CServerItem::CalcNodeSize rozmiar elementu jest konwertowany na **HIMETRIC** i zapisywane w *m_rectBounds*. Nieudokumentowany "*m_rectBounds*" członkiem `COleServerItem` nie istnieje (go częściowo zastąpiono *m_sizeExtent*, ale w OLE 2 tego elementu członkowskiego ma użycia nieco inne niż *m_rectBounds* w programie OLE1). Zamiast ustawiać **HIMETRIC** rozmiar do tej zmiennej składowej, zostanie zwrócona go. Ta wartość zwracana jest używana w `OnGetExtent`, wcześniej zaimplementowane.

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

Zastępuje również CServerItem `COleServerItem::OnGetTextData`. Ta funkcja jest przestarzała w MFC/OLE i zastępuje innego mechanizmu. Wersja MFC 3.0, MFC OLE próbki [HIERSVR](../overview/visual-cpp-samples.md) implementuje tej funkcji przez zastąpienie `COleServerItem::OnRenderFileData`. Nie jest to ważne w przypadku tego portu podstawowe, dzięki czemu możesz usunąć zastąpienie OnGetTextData.

Istnieje wiele więcej błędów w svritem.cpp, które nie zostały uwzględnione. Nie są one błędy "członu real" — po prostu błędy spowodowane przez poprzednie błędy.

```Output
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters
```

`COleServerItem::CopyToClipboard` nie obsługuje już `bIncludeNative` flagi. Natywne kopiowane są dane (dane zapisywane przez funkcję serializacja element serwera) zawsze, aby usunąć pierwszy parametr. Ponadto `CopyToClipboard` spowoduje zgłoszenie wyjątku, po wystąpieniu błędu zamiast zwracać wartość FALSE. Zmień kod dla CServerView::OnEditCopy w następujący sposób:

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

Mimo że wystąpiły błędy wynikające z kompilacji w wersji MFC 2.0 HIERSVR, niż wystąpiły dla tej samej wersji OCLIENT, wystąpiły faktycznie mniejszej liczby zmian.

W tym momencie HIERSVR będzie skompilować link i działać jako serwer OLE, ale bez funkcji edycji w miejscu, która będzie następnie zaimplementowana.

## <a name="adding-visual-editing"></a>Dodawanie "Edycja wizualna"

Aby dodać "Edycja wizualna" (lub aktywacji w miejscu) do tej aplikacji, istnieje tylko kilka rzeczy, które należy zadbać o:

- Potrzebujesz zasobu menu specjalne ma być używany, gdy element jest aktywny w miejscu.

- Ta aplikacja ma pasek narzędzi, dlatego potrzebujesz narzędzi z podzbiorem normalne narzędzi, aby dopasować polecenia menu dostępny z serwera (odpowiada zasobów menu wymienionymi powyżej).

- Potrzebujesz nową klasę pochodną `COleIPFrameWnd` zapewniający interfejsu użytkownika w miejscu (podobnie jak cmainframe —, pochodzące z `CMDIFrameWnd`, zapewnia interfejs użytkownika MDI).

- Musisz poinformować szablon o tych specjalnych zasobów i klas.

Zasób menu jest łatwo jest tworzyć. Uruchom program Visual C++, Kopiuj zasób menu IDR_HIERSVRTYPE do zasobu menu o nazwie IDR_HIERSVRTYPE_SRVR_IP. Zmodyfikuj menu, tak, aby pozostało tylko edytowanie i pomocy menu wyskakujące okienka. Dodaj separatory, dwóch menu Between menu Edycja i pomocy (powinien wyglądać podobnie jak: Edytuj &#124; &#124; pomocy). Aby uzyskać więcej informacji na temat znaczenie tych separatory i jak scalania menu serwer i kontener, zobacz [menu i zasoby: Scalanie menu](../mfc/menus-and-resources-menu-merging.md).

Mapy bitowe dla paska narzędzi podzbioru można łatwo utworzyć przez skopiowanie jednego z nowej aplikacji wygenerowane przez kreatora AppWizard z zaznaczoną opcją "Server". Następnie można zaimportować tej mapy bitowej do Visual C++. Należy podać identyfikator IDR_HIERSVRTYPE_SRVR_IP mapy bitowej.

Klasa jest pochodną `COleIPFrameWnd` może zostać skopiowany z aplikacji wygenerowane przez kreatora AppWizard przy użyciu również pomoc techniczna dotycząca serwera. Skopiuj obydwa pliki IPFRAME. CPP i IPFRAME. Godz. i dodać je do projektu. Upewnij się, że `LoadBitmap` wywołanie odnosi się do IDR_HIERSVRTYPE_SRVR_IP, mapy bitowej, utworzony w poprzednim kroku.

Teraz, gdy są tworzone nowe zasoby i klasy, należy dodać niezbędny kod tak, aby w ramach wie o tych (i wie, że teraz ta aplikacja obsługuje edycję w miejscu). Jest to realizowane przez dodanie niektórych większą liczbę parametrów, aby `SetServerInfo` wywołania `InitInstance` funkcji:

```cpp
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,
    IDR_HIERSVRTYPE_SRVR_IP,
    RUNTIME_CLASS(CInPlaceFrame));
```

Jest teraz gotowy do uruchomienia w miejscu w dowolnym kontenerze, który również obsługuje aktywacji w miejscu. Istnieje jednak jeden drobny błąd ukryte w kodzie. HIERSVR obsługuje menu kontekstowe, wyświetlane po naciśnięciu prawego przycisku myszy. To menu działa w przypadku, gdy HIERSVR jest w pełni otwarty, ale nie działa podczas edytowania osadzania w miejscu. Przyczyny można przypiąć w dół do tego jednego wiersza kodu w CServerView::OnRButtonDown:

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetApp()->m_pMainWnd);
```

Zwróć uwagę, odwołanie do `AfxGetApp()->m_pMainWnd`. Serwer jest aktywowany w miejscu, ma okno główne i elementu m_pMainWnd jest ustawiona, ale jest zwykle niewidoczne. Ponadto, w tym oknie odnosi się do *głównego* okna aplikacji, Otwórz okno ramek MDI, który jest wyświetlany, gdy serwer jest w pełni lub uruchomić autonomiczną. Nie odwołuje się do okna aktywnej ramki — gdy w miejscu aktywowane czyli ramkę okna pochodzące z `COleIPFrameWnd`. Aby uzyskać poprawny aktywnego okna, nawet wtedy, gdy w miejscu edytowania tej wersji biblioteki MFC dodaje nową funkcję, `AfxGetMainWnd`. Ogólnie rzecz biorąc, należy użyć tej funkcji, zamiast `AfxGetApp()->m_pMainWnd`. Ten kod musi zmienić w następujący sposób:

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetMainWnd());
```

Masz teraz minimalny zestaw jest włączone dla aktywacji w miejscu funkcjonalności serwera OLE. Ale nadal są dostępne z MFC/OLE 2, które nie były dostępne w MFC/OLE1 wiele funkcji. Zobacz przykład HIERSVR więcej pomysłów na temat funkcji, które można zaimplementować. Poniżej wymieniono niektóre funkcje, które implementuje HIERSVR:

- Powiększanie na wartość true, zachowanie WYSIWYG w odniesieniu do kontenera.

- Przeciągania / upuszczania i format schowka niestandardowych.

- Przewijanie okno kontenera jako wybór zostanie zmieniony.

Przykładowe HIERSVR 3.0 MFC używa również nieco inny projekt dla jego elementów serwera. To pomaga zachować pamięci i sprawia, że łącza jest bardziej elastyczna. Za pomocą wersji 2.0 HIERSVR każdy węzeł w drzewie *jest a* `COleServerItem`. `COleServerItem` niesie ze sobą obciążenie nieco więcej, niż jest to absolutnie konieczne dla każdego z tych węzłów, ale `COleServerItem` jest wymagana dla każdego aktywnego łącza. Ale w większości przypadków jest bardzo mało aktywnych łączy w danym momencie. Aby to bardziej wydajne, HIERSVR w tej wersji MFC oddziela węzła z `COleServerItem`. Ma ona zarówno CServerNode i `CServerItem` klasy. `CServerItem` (Pochodną `COleServerItem`) jest tworzony tylko, gdy jest to konieczne. Kontener (lub kontenery) należy zatrzymać przy użyciu określonego łącze, aby dany węzeł, obiekt CServerItem skojarzony z CServerNode skasowanie. Ten projekt jest bardziej wydajne i bardziej elastycznym. Jego elastyczność jest dostępna w podczas pracy z wieloma łączami zaznaczenia. Żadna z tych dwóch wersji HIERSVR nie obsługują wielokrotnego wyboru, ale jest znacznie łatwiejsze do dodania (i obsługują linki do tych opcji) do wersji MFC 3.0 HIERSVR, ponieważ `COleServerItem` są oddzielone od danych natywnych.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
