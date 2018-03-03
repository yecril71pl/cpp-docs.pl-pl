---
title: "TN041: Migracja z MFC — OLE1 do MFC — OLE 2 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.ole
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 894c171c025ef125495faad21dba2a98c08e8b88
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tn041-mfcole1-migration-to-mfcole-2"></a>TN041: migracja z MFC/OLE1 do MFC/OLE 2
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
## <a name="general-issues-relating-to-migration"></a>Ogólne problemy dotyczące migracji  
 Jednym z celów projektu dla klas OLE 2 w MFC 2.5 (lub nowsza) było zachować znacznie taką samą architekturę wprowadzone w MFC 2.0 dla obsługi OLE 1.0. W związku z tym wiele klasy OLE w MFC 2.0 nadal istnieje w tej wersji biblioteki MFC (`COleDocument`, `COleServerDoc`, `COleClientItem`, `COleServerItem`). Ponadto wiele interfejsów API w tych klas są dokładnie takie same. Jednak OLE 2 różni się znacząco od OLE 1.0, można oczekiwać, że niektóre dane zostały zmienione. Jeśli znasz obsługę OLE1 MFC 2.0, będziesz uważasz, że w domu z obsługą 2.0 MFC.  
  
 Jeśli jesteś biorąc istniejącej aplikacji MFC/OLE1 i dodanie do niej funkcji OLE 2, najpierw należy przeczytać tej uwagi. Ogólne problemy mogą wystąpić podczas eksportowanie funkcji z OLE1 do MFC/OLE 2 i następnie omówiono problemów niewykrytych podczas przenoszenia dwóch aplikacji zawarte w MFC 2.0 obejmuje ta Uwaga: przykłady MFC OLE [OCLIENT](../visual-cpp-samples.md) i [HIERSVR](../visual-cpp-samples.md).  
  
## <a name="mfc-documentview-architecture-is-important"></a>Ważne jest, architektury dokument/widok MFC  
 Jeśli aplikacja nie używa architektury dokument/widok MFC i chcesz dodać obsługę OLE 2 do aplikacji, nadszedł czas, aby przenieść dokument/widok. Wiele zalet klasy OLE 2 MFC tylko są realizowane, gdy aplikacja używa wbudowanego architektury i składników MFC.  
  
 Wdrażanie serwera lub kontener bez przy użyciu architektury MFC jest możliwe, ale nie jest zalecane.  
  
## <a name="use-mfc-implementation-instead-of-your-own"></a>Użyj MFC — implementacja zamiast własnych  
 Klasy MFC "puszkach implementację", takie jak `CToolBar`, `CStatusBar`, i `CScrollView` wbudowanych kod przypadków specjalnych obsługi OLE 2. Tak Jeśli używasz tych klas w aplikacji warto skorzystać z ich poddane działań zmierzających do uświadomić im OLE. Ponownie możliwe jest "roll własnej" klas w tym miejscu dla tych celów, ale nie jest zalecane. Jeśli musisz wdrożyć podobne funkcje, MFC kodu źródłowego jest doskonałym odwołania dotyczące niektórych bardziej precyzyjną punktów OLE (szczególnie w przypadku Aktywacja w miejscu).  
  
## <a name="examine-the-mfc-sample-code"></a>Sprawdź przykładowy kod MFC  
 Brak określonej liczby próbek MFC, które obejmują funkcje OLE. Każda z tych aplikacji implementuje OLE z o określony kąt:  
  
- [HIERSVR](../visual-cpp-samples.md) przeznaczone głównie do użytku jako aplikacja serwera. Został uwzględniony w MFC 2.0 jako aplikacji MFC/OLE1 i został przenoszone do MFC/OLE 2 i następnie rozszerzony tak, aby ją implementuje wiele funkcji OLE dostępne w OLE 2.  
  
- [OCLIENT](../visual-cpp-samples.md) to jest aplikacją autonomiczną kontenera, przeznaczone do zaprezentowania wiele funkcji OLE z punktu widzenia kontenera. Zbyt został on przeniesione z MFC 2.0, a następnie rozszerzony do obsługi wielu bardziej zaawansowanych funkcji OLE, takich jak formaty Schowka niestandardowych i łącza do osadzonych elementów.  
  
- [DRAWCLI](../visual-cpp-samples.md) tej aplikacji implementuje Obsługa kontenerów OLE znacznie jak OCLIENT tak, z wyjątkiem tego, że robi to w ramach istniejącego zorientowane obiektowo rysowania programu. Przedstawiono sposób może implementować Obsługa kontenerów OLE i zintegrować ją z istniejącej aplikacji.  
  
- [SUPERPAD](../visual-cpp-samples.md) tej aplikacji, a także są poprawnie aplikacji autonomicznej, jest również serwerem OLE. Obsługa serwera, który implementuje jest minimalist to jeszcze gotowe. Znaczący jest jak używa usługi Schowka OLE skopiować dane do Schowka, ale używa funkcji wbudowanych w formancie systemu Windows "edit" do implementacji funkcji Wklej Schowka. Ta operacja wyświetla interesujące mieszanego tradycyjnych użycia interfejsu API systemu Windows, a także integrację z nowych OLE interfejsów API.  
  
 Aby uzyskać więcej informacji dotyczących przykładowych aplikacji zobacz "MFC próbki pomoc".  
  
## <a name="case-study-oclient-from-mfc-20"></a>Analiza przypadku: OCLIENT z MFC 2.0  
 Jak wspomniano powyżej, [OCLIENT](../visual-cpp-samples.md) została uwzględniona w MFC 2.0 i implementowane OLE z MFC/OLE1. Poniżej opisano kroki, według których ta aplikacja początkowo został przekonwertowany na używać klas MFC/OLE 2. Wiele funkcji zostały dodane po początkowej portu została ukończona, aby lepiej zilustrować klas MFC/OLE. Te funkcje nie zostały omówione w tym miejscu; można znaleźć na przykład aby uzyskać więcej informacji na temat tych zaawansowanych funkcji.  
  
> [!NOTE]
>  Błędy kompilatora i krok po kroku proces został utworzony z programem Visual C++ 2.0. Określone komunikaty o błędach i lokalizacje mógł ulec zmianie Visual C++ 4.0, ale informacje koncepcyjne pozostaje ważny.  
  
## <a name="getting-it-up-and-running"></a>Uruchamianie go w i przeprowadzanie  
 Podejście do portu próbki OCLIENT MFC/OLE jest uruchomienie skompilowanie go i naprawienie błędów kompilatora oczywiste, które będą powodować. Jeśli pobrać próbkę OCLIENT z MFC 2.0 i skompiluj go w tej wersji biblioteki MFC, przekonasz się, że nie są to wiele błędów, aby rozwiązać. Poniżej opisano błędy w kolejności, w której miały miejsce.  
  
## <a name="compile-and-fix-errors"></a>Kompilacji i poprawki błędów  
  
```  
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters  
```  
  
 Pierwszy dotyczy błąd `COleClientItem::Draw`. W MFC/OLE1 zajęło więcej parametrów niż wersja MFC/OLE ma. Dodatkowe parametry często nie były wymagane i zazwyczaj NULL (jak w poniższym przykładzie). Ta wersja MFC automatycznie określić wartości lpWBounds, kiedy CDC, który jest rysowana jest metaplik kontrolera domeny. Ponadto parametru pFormatDC nie jest już konieczne ponieważ framework utworzy jedną z "atrybutu kontrolera domeny" PDC przekazany. Tak, aby rozwiązać ten problem, po prostu usuń dwa dodatkowe wartości NULL parametrów wywołania rysowania.  
  
```  
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier  
\oclient\mainview.cpp(273) : error C2057: expected constant expression  
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
```  
  
 Błędy powyżej wyników z faktu, że wszystkie **COleClientItem::CreateXXXX** wymagane funkcje MFC/OLE1 że przekazywane do reprezentowania elementu unikatową nazwę. To wymaganie podstawowej OLE interfejsu API. Nie jest to konieczne w MFC/OLE 2 ponieważ OLE 2 nie używa DDE jako podstawowy mechanizm komunikacji (nazwa został użyty w konwersacji). Aby rozwiązać ten problem, można usunąć **CreateNewName** funkcji oraz wszystkie odwołania do niego. To proste dowiedzieć się, co każdej funkcji MFC/OLE oczekiwana jest w tej wersji za pomocą umieszczając kursor w wywołaniu i naciskając klawisz F1.  
  
 Inny obszar, który różni się znacząco jest obsługa Schowka OLE 2. Z OLE1 są używane przez interakcję interfejsów API schowka systemu Windows ze Schowka. OLE 2 odbywa się za pomocą innego. Interfejsy API MFC/OLE1 zakłada, że Schowka była otwarta przed skopiowaniem `COleClientItem` obiektu do Schowka. To nie jest już konieczne i spowoduje, że wszystkie operacje schowka MFC/OLE się niepowodzeniem. Podczas edytowania kodu, aby usunąć zależności na **CreateNewName**, należy również usunąć kod, który zostanie otwarty i zamyka Schowka systemu Windows.  
  
```  
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier  
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function  
\oclient\mainview.cpp(344) : error C2057: expected constant expression  
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'  
```  
  
 Wynikiem tych błędów **CMainView::OnInsertObject** programu obsługi. Obsługa polecenia "Insert nowy obiekt" jest inny obszar, w którym rzeczy zostały zmienione sobą. W takim przypadku najłatwiej po prostu scalania oryginalnego wdrożenia z informacjami pochodzącymi z kreatorami AppWizard dla nowej aplikacji kontenera OLE. W rzeczywistości jest to technika, którą można zastosować do przenoszenia innych aplikacji. W MFC/OLE1, okno dialogowe "Wstaw obiekt" wyświetlony po wywołaniu **AfxOleInsertDialog** funkcji. W tej wersji można skonstruować **COleInsertObject** obiektu okna dialogowego i wywołania `DoModal`. Ponadto są tworzone nowe elementy OLE z **CLSID** zamiast ciągu classname. W rezultacie powinien wyglądać mniej więcej tak  
  
```  
COleInsertDialog dlg;  
if (dlg.DoModal() != IDOK)  
    return; 
 
BeginWaitCursor();

 
CRectItem* pItem = NULL;  
TRY  
{ *// First create the C++ object  
    pItem = GetDocument()->CreateItem();
ASSERT_VALID(pItem);

 *// Initialize the item from the dialog data.  
    if (!dlg.CreateItem(pItem))  
    AfxThrowMemoryException();
*// any exception will do  
    ASSERT_VALID(pItem);

 *// run the object if appropriate  
    if (dlg.GetSelectionType() == 
    COleInsertDialog::createNewItem) 
    pItem->DoVerb(OLEIVERB_SHOW,
    this);

 *// update right away  
    pItem->UpdateLink();
pItem->UpdateItemRectFromServer();

 *// set selection to newly inserted item  
    SetSelection(pItem);

 pItem->Invalidate();

}  
CATCH (CException,
    e)  
{ *// clean up item  
    if (pItem != NULL)  
    GetDocument()->DeleteItem(pItem);

 
    AfxMessageBox(IDP_FAILED_TO_CREATE);

} 
END_CATCH  
 
EndWaitCursor();
```  
  
> [!NOTE]
>  Wstaw nowy obiekt mogą być różne dla aplikacji):  
  
 Należy również uwzględnić \<afxodlgs.h >, który zawiera deklaracji pod kątem **COleInsertObject** klasy okien dialogowych, a także innych standardowych oknach dialogowych udostępniane przez MFC.  
  
```  
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier  
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters  
```  
  
 Te błędy są powodowane przez fakt, że niektóre stałe OLE1 zostały zmienione w OLE 2, mimo że pojęcia są one takie same. W takim przypadku **OLEVERB_PRIMARY** zmieniła się na `OLEIVERB_PRIMARY`. OLE1 i OLE 2 primary — zlecenie jest zazwyczaj wykonywane przez kontener, gdy użytkownik kliknie dwukrotnie w elemencie.  
  
 Ponadto `DoVerb` teraz zajmuje dodatkowy parametr — wskaźnik do widoku (`CView`*). Ten parametr jest używany tylko do zaimplementowania "Edycja wizualna" (lub Aktywacja w miejscu). Teraz można ustawić parametru wartości NULL, ponieważ nie w przypadku implementowania tej funkcji w tej chwili.  
  
 Aby upewnić się, że platformę nigdy nie próbuje w miejscu aktywować, należy zastąpić `COleClientItem::CanActivate` w następujący sposób:  
  
```  
BOOL CRectItem::CanActivate()  
{  
    return FALSE;  
}  
 
\oclient\rectitem.cpp(53) : error C2065: 'GetBounds' : undeclared identifier  
\oclient\rectitem.cpp(53) : error C2064: term does not evaluate to a function  
\oclient\rectitem.cpp(84) : error C2065: 'SetBounds' : undeclared identifier  
\oclient\rectitem.cpp(84) : error C2064: term does not evaluate to a function  
```  
  
 W MFC/OLE1 **COleClientItem::GetBounds** i **SetBounds** były używane do wykonywania zapytań i manipulowania zakres elementu ( **po lewej stronie** i **górnej**członków były zawsze zero). W MFC/OLE 2 jest to bardziej bezpośrednio obsługiwane przez `COleClientItem::GetExtent` i `SetExtent`, który postępowania w przypadku **rozmiar** lub `CSize` zamiast tego.  
  
 Kod dla Twojego nowego SetItemRectToServer i wywołania UpdateItemRectFromServer wyglądać następująco:  
  
```  
BOOL CRectItem::UpdateItemRectFromServer()  
{  
    ASSERT(m_bTrackServerSize);

 CSize size;  
    if (!GetExtent(&size))  
    return FALSE;    // blank  
 *// map from HIMETRIC to screen coordinates  
 {  
    CClientDC screenDC(NULL);

    screenDC.SetMapMode(MM_HIMETRIC);

 screenDC.LPtoDP(&size);

 } *// just set the item size  
    if (m_rect.Size() != size)  
 { *// invalidate the old size/position  
    Invalidate();
m_rect.right = m_rect.left + size.cx;  
    m_rect.bottom = m_rect.top + size.cy; *// as well as the new size/position  
    Invalidate();

 }  
    return TRUE;  
}  
 
BOOL CRectItem::SetItemRectToServer()  
{ *// set the official bounds for the embedded item  
    CSize size = m_rect.Size();

 {  
    CClientDC screenDC(NULL);

    screenDC.SetMapMode(MM_HIMETRIC);

 screenDC.DPtoLP(&size);

 }  
    TRY 
 {  
    SetExtent(size);
*// may do a wait  
 }  
    CATCH(CException, e)  
 {  
    return FALSE;  // links will not allow SetBounds  
 }  
    END_CATCH 
    return TRUE;  
}  
 
\oclient\frame.cpp(50) : error C2039: 'InWaitForRelease' : is not a member of 'COleClientItem'  
\oclient\frame.cpp(50) : error C2065: 'InWaitForRelease' : undeclared identifier  
\oclient\frame.cpp(50) : error C2064: term does not evaluate to a function  
```  
  
 W MFC/OLE1 API synchroniczne wywołania z kontenera do serwera zostały *symulowane*, ponieważ jest z założenia asynchronicznych w wielu przypadkach OLE1. Konieczne było wyszukać wywołanie asynchroniczne oczekujących w toku przed przetworzeniem polecenia od użytkownika. Podany MFC/OLE1 **COleClientItem::InWaitForRelease** funkcji w ten sposób. W MFC/OLE 2 nie jest to konieczne, aby móc usunąć cmainframe — zastąpienie OnCommand wszystkich elementów.  
  
 W tym momencie OCLIENT skompilować i połącz.  
  
## <a name="other-necessary-changes"></a>Inne wymagane zmiany  
 Istnieje kilka czynności, które nie są wykonywane zachowa OCLIENT uruchamianie, jednak. Zaleca się rozwiązać te problemy teraz zamiast później.  
  
 Najpierw należy zainicjować bibliotek OLE. Jest to realizowane przez wywołanie **afxoleinit —** z `InitInstance`:  
  
```  
if (!AfxOleInit())  
{  
    AfxMessageBox("Failed to initialize OLE libraries");

    return FALSE;  
}  
```  
  
 Jest również dobrym rozwiązaniem, aby wyszukać funkcje wirtualne dla parametru Lista zmian. Jednej z tych funkcji jest `COleClientItem::OnChange`, przesłaniania w każdej aplikacji kontenera MFC/OLE. Analizując pomocy online, zobaczysz, czy dodatkowy "DWORD dwParam" został dodany. Nowe CRectItem::OnChange wygląda następująco:  
  
```  
void   
CRectItem::OnChange(OLE_NOTIFICATION wNotification, DWORD dwParam)  
{  
    if (m_bTrackServerSize&& 
 !UpdateItemRectFromServer())  
 { *// Blank object  
    if (wNotification == OLE_CLOSED)  
 { *// no data received for the object - destroy it  
    ASSERT(!IsVisible());

 GetDocument()->DeleteItem(this);

    return; // no update (item is gone now)  
 }  
 }  
    if (wNotification != OLE_CLOSED)  
    Dirty();
Invalidate();
*// any change will cause a redraw  
}  
```  
  
 W MFC/OLE1 aplikacje kontenera pochodnej klasy dokumentu z **COleClientDoc**. W MFC/OLE 2 ta klasa została usunięta i zastępuje `COleDocument` (tej nowej organizacji ułatwia tworzenie aplikacji kontenera/serwera). Brak `#define` mapujący **COleClientDoc** do `COleDocument` uprościć przenoszenie aplikacji MFC/OLE1 do MFC/OLE 2, takich jak OCLIENT. Jedną z funkcji nie dostarczane przez `COleDocument` dostarczone przez **COleClientDoc** jest komunikat standardowe polecenia wpisów map. Odbywa się to przez aplikacje serwera, które także używają `COleDocument` (bezpośrednio), nie pociąga za sobą koszty te programy obsługi poleceń, chyba że są one aplikacji kontenera/serwera. Konieczne jest dodanie do mapy komunikatów CMainDoc następujące wpisy:  
  
```  
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE,
    OnUpdatePasteMenu)  
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK,
    OnUpdatePasteLinkMenu)  
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS,
    OnUpdateEditLinksMenu)  
ON_COMMAND(ID_OLE_EDIT_LINKS,
    COleDocument::OnEditLinks)  
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST,
    OnUpdateObjectVerbMenu)  
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT,
    OnUpdateObjectVerbMenu)  
ON_COMMAND(ID_OLE_EDIT_CONVERT,
    OnEditConvert)  
```  
  
 Implementacja wszystkich tych poleceń jest w `COleDocument`, która jest klasą bazową dla dokumentu.  
  
 W tym momencie OCLIENT jest funkcjonalności aplikacji kontenera OLE. Istnieje możliwość wstawić elementów dowolnego typu (OLE1 lub OLE 2). Ponieważ nie zaimplementowano niezbędne kodu w celu włączenia aktywacji w miejscu, w osobnym oknie, taki jak OLE1 edytowania elementów. W następnej sekcji omówiono niezbędne zmiany, aby włączyć edycji w miejscu (nazywane czasem "Edycja wizualna").  
  
## <a name="adding-visual-editing"></a>Dodawanie "Edycja wizualna"  
 Jedną z najbardziej interesujących funkcji OLE jest aktywacja w miejscu (lub "Edycja wizualna"). Ta funkcja umożliwia aplikacji serwera do przejęcia części kontenera interfejsu użytkownika do określonych więcej edycji interfejs użytkownika. Aby zaimplementować Aktywacja w miejscu do OCLIENT, niektóre specjalne zasoby należy dodać oraz dodatkowy kod. Te zasoby oraz kod zwykle są dostarczane przez kreatorami AppWizard — w rzeczywistości większość tutaj kod został pobierają bezpośrednio z aplikacją kreatorami AppWizard świeże z obsługą "Kontener".  
  
 Przede wszystkim należy dodać zasób menu można użyć, gdy istnieje element, który jest aktywny w miejscu. Kopiowanie zasobów IDR_OCLITYPE i usuwając wszystkie oprócz wyskakujące okno i plików, można utworzyć tego zasobu dodatkowe menu w programie Visual C++. Dwa pasków separatorów są wstawiane plików i okno wyskakujące okienka wskazująca rozdzielenie grup (powinna wyglądać: plik &#124; &#124; Okno). Aby uzyskać więcej informacji na temat tych separatorów oznacza i jak scalania menu serwera i kontener zobacz "Menu i zasoby: scalanie Menu" w *klasy OLE 2*.  
  
 Po utworzeniu tych menu utworzone, należy powiadomić framework wiedzieć o nich. Jest to realizowane przez wywołanie `CDocTemplate::SetContainerInfo` dla szablonu dokumentów przed dodaniem go do listy szablonów dokumentów w InitInstance użytkownika. Nowy kod, aby zarejestrować szablonu dokumentu wygląda następująco:  
  
```  
CDocTemplate* pTemplate = new CMultiDocTemplate(
    IDR_OLECLITYPE, 
    RUNTIME_CLASS(CMainDoc), 
    RUNTIME_CLASS(CMDIChildWnd), // standard MDI child frame  
    RUNTIME_CLASS(CMainView));

pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);

AddDocTemplate(pTemplate);
```   
  
 Zasób IDR_OLECLITYPE_INPLACE jest specjalnym zasobem w miejscu utworzone w programie Visual C++.  
  
 Aby włączyć aktywacji w miejscu, są niektóre elementy, które należy zmienić w obu `CView` (CMainView) pochodnej klasy, jak również `COleClientItem` klasy (CRectItem). Wszystkie te zastąpienia są dostarczane przez kreatorami AppWizard i większość implementacji rozpocznie się bezpośrednio z kreatorami AppWizard domyślnej aplikacji.  
  
 W pierwszym kroku tego portu, aktywacja w miejscu został wyłączony całkowicie przez zastąpienie `COleClientItem::CanActivate`. To zastąpienie powinien zostać usunięty w celu zezwolenia na aktywację w miejscu. Ponadto NULL została przekazana do wszystkich wywołań `DoVerb` (występują dwa z nich) powodu udostępnia widok tylko niezbędne do aktywacji w miejscu. Do pełnego wdrożenia Aktywacja w miejscu, należy przekazać poprawnego widoku w `DoVerb` wywołania. Jeden z tych wywołań jest **CMainView::OnInsertObject**:  
  
```  
pItem->DoVerb(OLEIVERB_SHOW, this);
```  
  
 Trwa inny **CMainView::OnLButtonDblClk**:  
  
```  
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);
```  
  
 Należy zastąpić `COleClientItem::OnGetItemPosition`. Ta wartość informuje serwer gdzie umieścić okna względem kontenera okna, gdy element jest aktywowany na miejscu. Dla OCLIENT wdrożenie jest proste:  
  
```  
void CRectItem::OnGetItemPosition(CRect& rPosition)  
{  
    rPosition = m_rect;  
}  
```  
  
 Większość serwerów wdrożenia, co jest nazywane "w miejscu zmiany rozmiaru." Dzięki temu okna serwera o rozmiarze i przenieść, gdy użytkownik edytuje element. Kontener muszą należeć do tej akcji, ponieważ przeniesienie lub zmiana rozmiaru okna zwykle wpływa na położenie i rozmiar w samym dokumencie kontenera. Implementację OCLIENT synchronizuje prostokąt wewnętrznego obsługiwanego przez m_rect z nowego położenia i rozmiaru.  
  
```  
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
  
 W tym momencie Brak wystarczającej ilości kodu, aby umożliwić elementu w miejscu aktywowana i postępowania w przypadku zmiany rozmiaru i przenoszenia elementu, gdy będzie aktywny, ale żaden kod nie zezwoli użytkownikowi zamknąć sesji edytowania. Mimo że niektóre serwery będą tę funkcjonalność zapewniają się dzięki obsłudze klawisz escape, sugeruje się, że kontenery udostępnia dwa sposoby dezaktywować elementu: (1), klikając poza element i (2), naciskając klawisz ESC.  
  
 Klawisz ESCAPE Dodaj akceleratora z programem Visual C++ mapowanego vk_escape — klawisz polecenia, ID_CANCEL_EDIT zostanie dodany do zasobów. Program obsługi dla tego polecenia są następujące:  
  
```  
// The following command handler provides the standard  
// keyboard user interface to cancel an in-place  
// editing session.void CMainView::OnCancelEdit()  
{ *// Close any in-place active item on this view.  
    COleClientItem* pActiveItem = 
    GetDocument()->GetInPlaceActiveItem(this);

 if (pActiveItem != NULL)  
    pActiveItem->Close();
ASSERT(GetDocument()->GetInPlaceActiveItem(this) == NULL);

}  
```  
  
 Aby obsługiwać w przypadku, gdy użytkownik kliknie poza elementu, Dodaj następujący kod do początku **CMainView::SetSelection**:  
  
```  
if (pNewSel != m_pSelection || pNewSel == NULL)  
{  
    COleClientItem* pActiveItem = 
    GetDocument()->GetInPlaceActiveItem(this);

 if (pActiveItem != NULL&& pActiveItem != pNewSel)  
    pActiveItem->Close();

} 
 
```  
  
 Gdy element jest aktywny w miejscu, ma fokus. Aby upewnić się, że jest to obsłużyć klasy OnSetFocus tak, aby fokus zawsze jest przenoszona do aktywnego elementu, gdy widok otrzymuje fokus:  
  
```  
// Special handling of OnSetFocus and OnSize are required   
// when an object is being edited in-place.  
void CMainView::OnSetFocus(CWnd* pOldWnd)  
{  
    COleClientItem* pActiveItem = 
    GetDocument()->GetInPlaceActiveItem(this);

 if (pActiveItem != NULL&& 
    pActiveItem->GetItemState() == COleClientItem::activeUIState)  
 { *// need to set focus to this item if it is same view  
    CWnd* pWnd = pActiveItem->GetInPlaceWindow();
if (pWnd != NULL)  
 {  
    pWnd->SetFocus();
*// don't call the base class  
    return; 
 }  
 }  
 
    CView::OnSetFocus(pOldWnd);

} 
```  
  
 Gdy zmieniany jest rozmiar widoku, należy powiadomić aktywnego elementu Prostokątny wycinek o zmianie. W tym zapewniają obsługę `OnSize`:  
  
```  
void CMainView::OnSize(UINT nType,
    int cx,
    int cy)  
{  
    CView::OnSize(nType,
    cx,
    cy);

    COleClientItem* pActiveItem = 
    GetDocument()->GetInPlaceActiveItem(this);

 if (pActiveItem != NULL)  
    pActiveItem->SetItemRects();

} 
```  
  
## <a name="case-study-hiersvr-from-mfc-20"></a>Analiza przypadku: HIERSVR z MFC 2.0  
 [HIERSVR](../visual-cpp-samples.md) również została uwzględniona w MFC 2.0 i implementowane OLE z MFC/OLE1. Ta uwaga krótko opisano kroki, według których ta aplikacja początkowo został przekonwertowany na używać klas MFC/OLE 2. Wiele funkcji zostały dodane po początkowej portu została ukończona, aby lepiej zilustrować klas MFC/OLE 2. Te funkcje nie zostały omówione w tym miejscu; można znaleźć na przykład aby uzyskać więcej informacji na temat tych zaawansowanych funkcji.  
  
> [!NOTE]
>  Błędy kompilatora i krok po kroku proces został utworzony z programem Visual C++ 2.0. Określone komunikaty o błędach i lokalizacje mógł ulec zmianie Visual C++ 4.0, ale informacje koncepcyjne pozostaje ważny.  
  
## <a name="getting-it-up-and-running"></a>Uruchamianie go w i przeprowadzanie  
 Podejście do portu próbki HIERSVR MFC/OLE jest uruchomienie skompilowanie go i naprawienie błędów kompilatora oczywiste, które będą powodować. Jeśli pobrać próbkę HIERSVR z MFC 2.0 i skompiluj go w tej wersji biblioteki MFC, przekonasz się, że nie ma wiele błędów, aby rozpoznać (choć więcej niż próbką OCLIENT). Poniżej opisano w kolejności, w których zwykle występują błędy.  
  
## <a name="compile-and-fix-errors"></a>Kompilacji i poprawki błędów  
  
```  
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'  
```  
  
 Ten błąd wskazuje znacznie większe problem z `InitInstance` funkcja dla serwerów. Inicjowanie wymagane przez serwer OLE prawdopodobnie jest jednym z największych zmiany, które należy wprowadzić w aplikacji MFC/OLE1 do pobrania będzie działać. Najlepiej, aby zrobić to przyjrzeć się kreatorami AppWizard tworzy dla serwera OLE i zmodyfikuj odpowiednio kod. Oto kilka kwestii, które należy wziąć pod uwagę:  
  
 Należy zainicjować bibliotek OLE wywołując **afxoleinit —**  
  
 Wywołanie SetServerInfo w obiekcie szablonu dokumentu, można ustawić uchwytów zasobów serwera i informacje o klasie czasu wykonywania, nie można ustawić z `CDocTemplate` konstruktora.  
  
 Nie pokazuj okna głównego aplikacji, jeśli Embedding znajduje się w wierszu polecenia.  
  
 Będziesz potrzebować **GUID** dokumentu. Jest to unikatowy identyfikator typu dokumentu (128 bitów). Kreatorami AppWizard zostanie utworzona przez — tak więc jeśli używasz techniki opisane tutaj kopiowania nowy kod z nową aplikację serwera kreatorami AppWizard generowany, użytkownik może po prostu "wykradać" identyfikatora GUID z tej aplikacji. Jeśli nie używasz GUIDGEN. Narzędzie EXE w katalogu BIN.  
  
 Konieczne jest "Połącz" Twoje `COleTemplateServer` obiekt w szablonie dokumentu przez wywołanie metody `COleTemplateServer::ConnectTemplate`.  
  
 Gdy aplikacja jest uruchamiana autonomicznej, należy zaktualizować rejestru systemu. Dzięki temu w przypadku przejścia użytkownika. EXE dla aplikacji, uruchamiając go z nowej lokalizacji spowoduje zaktualizowanie bazy danych rejestracji systemu Windows aby wskazywał nową lokalizację.  
  
 Po zastosowaniu wszystkich tych zmian na kreatorami AppWizard tworzy na podstawie `InitInstance`, `InitInstance` (i związane z identyfikatorem GUID) dla HIERSVR powinien wyglądać następująco:  
  
```  
// this is the GUID for HIERSVR documents  
static const GUID BASED_CODE clsid = 
 { 0xA0A16360L,
    0xC19B,
    0x101A, { 0x8C,
    0xE5,
    0x00,
    0xDD,
    0x01,
    0x11,
    0x3F,
    0x12 } };  
 
/////////////////////////////////////////////////////////////////////////////  
// COLEServerApp initialization  
 
BOOL COLEServerApp::InitInstance()  
{ *// OLE 2 initialization  
    if (!AfxOleInit())  
 {  
    AfxMessageBox("Initialization of the OLE failed!");

    return FALSE;  
 }  
 *// Standard initialization  
    LoadStdProfileSettings();

// Load standard INI file options   
 *// Register document templates  
    CDocTemplate* pDocTemplate;  
    pDocTemplate = new CMultiDocTemplate(IDR_HIERSVRTYPE,  
    RUNTIME_CLASS(CServerDoc), 
    RUNTIME_CLASS(CMDIChildWnd), 
    RUNTIME_CLASS(CServerView));

 pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB);

    AddDocTemplate(pDocTemplate);

 *// create main MDI Frame window  
    CMainFrame* pMainFrame = new CMainFrame;  
    if (!pMainFrame->LoadFrame(IDR_MAINFRAME))  
    return FALSE;  
    m_pMainWnd = pMainFrame;  
 
    SetDialogBkColor();
*// gray look  
 *// enable file manager drag/drop and DDE Execute open  
    m_pMainWnd->DragAcceptFiles();
EnableShellOpen();

 
    m_server.ConnectTemplate(clsid,
    pDocTemplate,
    FALSE);

    COleTemplateServer::RegisterAll();

 *// try to launch as an OLE server  
    if (RunEmbedded())  
 { *// "short-circuit" initialization -- run as server!  
    return TRUE;  
 }  
    m_server.UpdateRegistry();
RegisterShellFileTypes();

 *// not run as OLE server,
    so show the main window  
    if (m_lpCmdLine[0] == '\0')  
 { *// create a new (empty) document  
    OnFileNew();

 }  
    else 
 { *// open an existing document  
    OpenDocumentFile(m_lpCmdLine);

 }  
 
    pMainFrame->ShowWindow(m_nCmdShow);

 pMainFrame->UpdateWindow();

 
    return TRUE;  
}  
```  
  
 Można zauważyć, że powyższy kod odwołuje się do nowego Identyfikatora zasobu IDR_HIERSVRTYPE_SRVR_EMB. Jest to zasobów menu ma być używany podczas edytowania dokumentu, który jest osadzony w innym kontenerze. W MFC/OLE1 określonych edytować element osadzony elementów menu zostały zmienione na bieżąco. Przy użyciu struktury zupełnie innego menu podczas edytowania element osadzony zamiast edytowania dokumentu opartych na plikach ułatwia zapewnienie różnych interfejsów użytkownika dla tych dwa różne tryby. Pojawi się później, zasobów rozłączne menu jest używane podczas edytowania osadzonego w miejscu.  
  
 Aby utworzyć tego zasobu, ładowanie skryptu zasobu w programie Visual C++ i skopiuj istniejący zasób IDR_HIERSVRTYPE w menu. Zmień nazwę nowego zasobu na IDR_HIERSVRTYPE_SRVR_EMB (jest to tej samej konwencji nazewnictwa, która korzysta z kreatorami AppWizard). Następna zmiana "Zapisz plik" do "Plik Update"; Nadaj mu identyfikator polecenia **id_file_update —**. Również zmienić "Zapisz plik jako" do "Pliku Zapisz kopię jako"; Nadaj mu identyfikator polecenia **id_file_save_copy_as —**. Framework zapewnia implementacji oba te polecenia.  
  
```  
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations  
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers  
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'  
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'  
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers  
```  
  
 Liczba błędów wynikających z zastąpienia z `OnSetData`, ponieważ odwołuje się do **OLESTATUS** typu. **OLESTATUS** możliwości OLE1 zwrócone błędy. Ta została zmieniona na `HRESULT` OLE 2, chociaż zazwyczaj konwertuje MFC `HRESULT` do `COleException` zawierające błąd. W tym przypadku zastąpienia z `OnSetData` nie jest już konieczne, tak aby najłatwiejszym go usunąć.  
  
```  
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters  
```  
  
 `COleServerItem` Konstruktor ma dodatkowy parametr "BOOL". Ta flaga Określa, jak zarządzanie pamięcią jest wykonywane na `COleServerItem` obiektów. Przez ustawienie dla niego wartość true, platformę obsługuje zarządzanie pamięcią tych obiektów, usuwając je, gdy nie są już wymagane. Używa HIERSVR **CServerItem** (pochodną `COleServerItem`) obiektów w ramach jego danych w trybie macierzystym, dlatego ta flaga będzie ustawiony na wartość FALSE. Dzięki temu HIERSVR określić usunięcia każdego elementu serwera.  
  
```  
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class  
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class  
```  
  
 Jak te błędy oznacza istnieją niektóre funkcje "czysty wirtualnym", które nie zostały zastąpione w CServerItem. Najbardziej prawdopodobną przyczyną jest fakt, że lista parametrów w OnDraw została zmieniona. Aby naprawić ten błąd, należy zmienić **CServerItem::OnDraw** w następujący sposób (a także deklaracji w svritem.h):  
  
```  
BOOL CServerItem::OnDraw(CDC* pDC,
    CSize& rSize)  
{ *// request from OLE to draw node  
    pDC->SetMapMode(MM_TEXT);

// always in pixels  
    return DoDraw(pDC,
    CPoint(0,
    0),
    FALSE);

}  
```  
  
 Nowy parametr jest "rSize". Dzięki temu można wpisać rozmiar rysunku, jeśli jest to wygodny. Ten rozmiar musi być w **HIMETRIC**. W takim przypadku nie jest wygodne wypełnić tę wartość, więc struktura wywołuje `OnGetExtent` do pobrania w zakresie. W tym do pracy, musisz zaimplementować `OnGetExtent`:  
  
```  
BOOL CServerItem::OnGetExtent(DVASPECT dwDrawAspect,
    CSize& rSize)  
{  
    if (dwDrawAspect != DVASPECT_CONTENT)  
    return COleServerItem::OnGetExtent(dwDrawAspect,
    rSize);

 
    rSize = CalcNodeSize();
return TRUE;  
}  
 
\hiersvr\svritem.cpp(104) : error C2065: 'm_rectBounds' : undeclared identifier  
\hiersvr\svritem.cpp(104) : error C2228: left of '.SetRect' must have class/struct/union type  
\hiersvr\svritem.cpp(106) : error C2664: 'void __pascal __far DPtoLP(struct ::tagPOINT __far *,
    int)__far const ' : cannot convert parameter 1 from 'int __far *' to 'struct ::tagPOINT __far *'  
```  
  
 W funkcji CServerItem::CalcNodeSize rozmiar elementu jest konwertowana na **HIMETRIC** i przechowywane w **m_rectBounds**. Nieudokumentowanej "**m_rectBounds**" członek `COleServerItem` nie istnieje (ma częściowo zastępowany przez `m_sizeExtent`, ale w OLE 2 ten element członkowski ma użycie nieco inne niż **m_rectBounds**w OLE1). Zamiast ustawienie **HIMETRIC** rozmiar do tej zmiennej członkowskiej, zostanie zwrócona go. Zwrócona wartość jest używana w `OnGetExtent`, wcześniej zaimplementowane.  
  
```  
CSize CServerItem::CalcNodeSize()  
{  
    CClientDC dcScreen(NULL);

 
    m_sizeNode = dcScreen.GetTextExtent(m_strDescription,  
    m_strDescription.GetLength());

 m_sizeNode += CSize(CX_INSET* 2,
    CY_INSET* 2);

 *// set suggested HIMETRIC size  
    CSize size(m_sizeNode.cx,
    m_sizeNode.cy);

    dcScreen.SetMapMode(MM_HIMETRIC);

 dcScreen.DPtoLP(&size);

    return size;  
}  
```  
  
 Zastępuje również CServerItem **COleServerItem::OnGetTextData**. Ta funkcja jest przestarzała w MFC/OLE i zostało zastąpione przez inny mechanizm. Wersja MFC 3.0 próbki MFC OLE [HIERSVR](../visual-cpp-samples.md) implementuje tę funkcję przez zastąpienie `COleServerItem::OnRenderFileData`. Ta funkcja nie jest ważne dla tego portu podstawowych, aby usunąć zastąpienie OnGetTextData.  
  
 Istnieje wiele więcej błędów w svritem.cpp, które nie zostały uwzględnione. Nie są one błędy "rzeczywiste" — po prostu błędów spowodowanych przez poprzednie błędy.  
  
```  
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters  
```  
  
 `COleServerItem::CopyToClipboard`nie obsługuje już flagi "bIncludeNative". Danych natywnych (dane zapisywane przez funkcję serializacja elementu serwera) zawsze jest kopiowana, więc usunąć pierwszym parametrem. Ponadto `CopyToClipboard` po wystąpieniu błędu zamiast zwrócenie wartości FALSE spowoduje zgłoszenie wyjątku. Zmień kod dla CServerView::OnEditCopy w następujący sposób:  
  
```  
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
  
 Mimo że wystąpiły błędy więcej wynikające z kompilacji w wersji MFC 2.0 HIERSVR niż wystąpiły dla tej samej wersji OCLIENT, zostały faktycznie mniej zmiany.  
  
 W tym momencie HIERSVR będzie skompilować i połączyć i działać jako serwer OLE, ale bez funkcji edycji w miejscu, która będzie następnie zaimplementowana.  
  
## <a name="adding-visual-editing"></a>Dodawanie "Edycja wizualna"  
 Aby dodać "Edycja wizualna" (lub Aktywacja w miejscu) do tej aplikacji serwera, istnieje tylko kilka rzeczy, które użytkownik musi uwzględniać:  
  
-   Potrzebujesz zasobu menu specjalne do użycia, gdy element jest aktywny w miejscu.  
  
-   Ta aplikacja ma paska narzędzi, dlatego potrzebujesz narzędzi z tylko podzestaw normalne narzędzi do dopasowania polecenia menu dostępny z serwera (zgodna zasobów menu wymienionych powyżej).  
  
-   Należy nową klasę pochodną `COleIPFrameWnd` zapewnia interfejsu użytkownika w miejscu (podobnie jak cmainframe —, pochodną `CMDIFrameWnd`, udostępnia interfejs użytkownika MDI).  
  
-   Musisz Opisz platformę tych specjalnych zasobów i klasy.  
  
 Zasób menu jest łatwo utworzyć. Uruchom program Visual C++, kopiowanie zasobów menu IDR_HIERSVRTYPE do menu zasób o nazwie IDR_HIERSVRTYPE_SRVR_IP. Zmodyfikuj menu, tak, aby pozostało tylko okienek menu Edycja i uzyskać pomoc. Dodaj dwa separatory do menu Between menu Edycja i pomocy (powinna wyglądać: Edytuj &#124; &#124; Pomoc). Aby uzyskać więcej informacji o tych separatorów oznacza i jak scalania menu serwera i kontener, zobacz "Menu i zasoby: scalanie Menu" w *klasy OLE 2*.  
  
 Mapy bitowej dla narzędzi podzestawu można łatwo tworzyć przez skopiowanie z pierwszą aplikację kreatorami AppWizard wygenerowane z zaznaczoną opcją "Server". Ta mapa bitowa można następnie zaimportować do programu Visual C++. Należy podać identyfikator IDR_HIERSVRTYPE_SRVR_IP mapy bitowej.  
  
 Klasy pochodne `COleIPFrameWnd` mogą zostać skopiowane z kreatorami AppWizard wygenerowany aplikacji z obsługą serwera, jak również. Skopiuj oba pliki IPFRAME. I IPFRAME CPP. H i dodaj je do projektu. Upewnij się, że `LoadBitmap` wywołanie odwołuje się do IDR_HIERSVRTYPE_SRVR_IP, mapy bitowej utworzony w poprzednim kroku.  
  
 Teraz, kiedy są tworzone nowe zasoby i klasy, Dodaj wymagany kod, tak aby platformę zna te (i wie, że tej aplikacji teraz obsługuje edycji w miejscu). Jest to realizowane przez dodanie niektórych więcej parametrów, aby `SetServerInfo` wywołanie w `InitInstance` funkcji:  
  
```  
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,  
    IDR_HIERSVRTYPE_SRVR_IP,
    RUNTIME_CLASS(CInPlaceFrame));
```  
  
 Jest teraz gotowy do uruchomienia w miejscu w dowolnym kontenerze, który również obsługuje aktywacji w miejscu. Jest jednak jeden drobny błąd ukryte w kodzie. HIERSVR obsługuje menu kontekstowe wyświetlane po naciśnięciu prawego przycisku myszy. W tym menu działa w przypadku, gdy HIERSVR jest całkowicie otwarte, ale nie działa w przypadku edycji osadzenia w miejscu. Powód można przypiąć w dół do jednego wiersza kodu w CServerView::OnRButtonDown:  
  
```  
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,  
    point.x,
    point.y,
    AfxGetApp()->m_pMainWnd);
```  
  
 Zwróć uwagę, odwołanie do **AfxGetApp() -> m_pMainWnd**. Gdy serwer jest aktywowana w miejscu, składa się z głównego okna i m_pMainWnd jest ustawiona, ale jest zwykle niewidoczne. Ponadto odwołuje się do tego okna *głównego* okna aplikacji, Otwórz okno ramowe MDI, który jest wyświetlany, gdy serwer jest w pełni lub uruchom autonomiczne. Nie odwołuje się do okna aktywną ramkę — które w miejscu aktywowana po ramki okna pochodną `COleIPFrameWnd`. Aby uzyskać poprawny aktywne okno nawet wtedy, gdy w miejscu edycji, ta wersja MFC dodaje nową funkcję `AfxGetMainWnd`. Ogólnie rzecz biorąc, należy użyć tej funkcji, zamiast **AfxGetApp() -> m_pMainWnd**. Ten kod musi zmienić w następujący sposób:  
  
```  
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,  
    point.x,
    point.y,
    AfxGetMainWnd());
```  
  
 Teraz masz serwer OLE minimalny włączone dla funkcjonalności Aktywacja w miejscu. Ale nadal są dostępne z MFC/OLE 2, które nie były dostępne w MFC/OLE1 wiele funkcji. Zobacz przykład HIERSVR więcej pomysłów na funkcje, które można zaimplementować. Poniżej wymieniono niektóre funkcje, które implementuje HIERSVR:  
  
-   Powiększanie true zachowania WYSISYG względem kontenera.  
  
-   Przeciągnij / upuść i format schowka niestandardowych.  
  
-   Przewijanie okno kontenera jako zaznaczenie zostanie zmieniona.  
  
 Przykładowe HIERSVR 3.0 MFC używa również nieco inny projekt dla jego elementów serwera. Pomaga zachować pamięci i zapewnia bardziej elastyczne łącza. Przy użyciu wersji 2.0 HIERSVR każdy węzeł w drzewie *jest a* `COleServerItem`. `COleServerItem`Przenosi nieco większe obciążenie, niż jest to niezbędne dla każdego z tych węzłów, ale `COleServerItem` jest wymagany dla każdego aktywnego łącza. Jednak w większości przypadków istnieje bardzo niewiele aktywnych łączy w danym momencie. Aby osiągnąć większą wydajność, HIERSVR w tej wersji programu MFC oddziela węzła z `COleServerItem`. Ma ona zarówno CServerNode i **CServerItem** klasy. **CServerItem** (pochodną `COleServerItem`) jest tylko w razie potrzeby utworzone. Po kontenera (lub kontenery) Zatrzymaj przy użyciu tej określonej łącze, aby dany węzeł, do obiektu CServerItem skojarzonego z CServerNode są usuwane. Ten projekt jest bardziej wydajny i elastyczny. Jego elastyczność polega na podczas pracy nad wiele łączy zaznaczenia. Żadna z tych dwóch wersji HIERSVR nie obsługuje wyboru wielokrotnego, ale jest znacznie łatwiejsze do dodania (i obsługuje łącza do takich opcji) z wersji MFC 3.0 HIERSVR, ponieważ `COleServerItem` jest oddzielony od danych natywnych.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

