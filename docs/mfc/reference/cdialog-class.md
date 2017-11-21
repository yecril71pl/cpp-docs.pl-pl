---
title: "Cdialog — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDialog
- AFXWIN/CDialog
- AFXWIN/CDialog::CDialog
- AFXWIN/CDialog::Create
- AFXWIN/CDialog::CreateIndirect
- AFXWIN/CDialog::DoModal
- AFXWIN/CDialog::EndDialog
- AFXWIN/CDialog::GetDefID
- AFXWIN/CDialog::GotoDlgCtrl
- AFXWIN/CDialog::InitModalIndirect
- AFXWIN/CDialog::MapDialogRect
- AFXWIN/CDialog::NextDlgCtrl
- AFXWIN/CDialog::OnInitDialog
- AFXWIN/CDialog::OnSetFont
- AFXWIN/CDialog::PrevDlgCtrl
- AFXWIN/CDialog::SetDefID
- AFXWIN/CDialog::SetHelpID
- AFXWIN/CDialog::OnCancel
- AFXWIN/CDialog::OnOK
dev_langs: C++
helpviewer_keywords:
- CDialog [MFC], CDialog
- CDialog [MFC], Create
- CDialog [MFC], CreateIndirect
- CDialog [MFC], DoModal
- CDialog [MFC], EndDialog
- CDialog [MFC], GetDefID
- CDialog [MFC], GotoDlgCtrl
- CDialog [MFC], InitModalIndirect
- CDialog [MFC], MapDialogRect
- CDialog [MFC], NextDlgCtrl
- CDialog [MFC], OnInitDialog
- CDialog [MFC], OnSetFont
- CDialog [MFC], PrevDlgCtrl
- CDialog [MFC], SetDefID
- CDialog [MFC], SetHelpID
- CDialog [MFC], OnCancel
- CDialog [MFC], OnOK
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b823d40d4504be0180c3af3a6fb5359bf86725cd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdialog-class"></a>Cdialog — klasa
Klasa podstawowa używana do wyświetlania okien dialogowych na ekranie.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDialog : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDialog::CDialog](#cdialog)|Konstruuje `CDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDialog::Create](#create)|Inicjuje `CDialog` obiektu. Tworzy niemodalne okno dialogowe i dołącza go do `CDialog` obiektu.|  
|[CDialog::CreateIndirect](#createindirect)|Tworzy niemodalne okno dialogowe z szablonu okno dialogowe w pamięci (nie opartych na zasobach).|  
|[CDialog::DoModal](#domodal)|Wywołuje modalne okno dialogowe i zwraca po zakończeniu.|  
|[CDialog::EndDialog](#enddialog)|Zamyka modalne okno dialogowe.|  
|[CDialog::GetDefID](#getdefid)|Pobiera identyfikator formantu łącznik domyślny dla okna dialogowego.|  
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|Przenosi fokus do formantu okno dialogowe, w oknie dialogowym.|  
|[CDialog::InitModalIndirect](#initmodalindirect)|Tworzy modalne okno dialogowe z szablonu okno dialogowe w pamięci (nie opartych na zasobach). Parametry są przechowywane do funkcji `DoModal` jest wywoływana.|  
|[CDialog::MapDialogRect](#mapdialogrect)|Konwertuje jednostki okno dialogowe prostokąta jednostki ekranu.|  
|[CDialog::NextDlgCtrl](#nextdlgctrl)|Przenosi fokus do następnego formantu okno dialogowe, w oknie dialogowym.|  
|[CDialog::OnInitDialog](#oninitdialog)|Należy przesłonić, aby rozszerzyć inicjowania okno dialogowe.|  
|[CDialog::OnSetFont](#onsetfont)|Należy przesłonić, aby określić czcionkę, która jest używana podczas go rysuje tekst formantu okno dialogowe.|  
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|Przenosi fokus do poprzedniego okno dialogowe formantu w oknie dialogowym.|  
|[CDialog::SetDefID](#setdefid)|Zmiany określonego przycisku polecenia kontroli łącznik domyślny dla okna dialogowego.|  
|[CDialog::SetHelpID](#sethelpid)|Ustawia identyfikator pomocy kontekstowej dla okna dialogowego.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDialog::OnCancel](#oncancel)|Należy przesłonić, aby wykonać przycisku Anuluj lub ESC klucza akcji. Domyślnie zamknięcie okna dialogowego i **DoModal** zwraca **IDCANCEL**.|  
|[CDialog::OnOK](#onok)|Przesłoń w celu wykonania akcji przycisku OK w modalne okno dialogowe. Domyślnie zamknięcie okna dialogowego i `DoModal` zwraca **IDOK**.|  
  
## <a name="remarks"></a>Uwagi  
 Okna dialogowe istnieją dwa typy: modalne i niemodalne. Modalne okno dialogowe muszą być zamknięte przez użytkownika, przed kontynuowaniem aplikacji. Niemodalne okno dialogowe umożliwia użytkownikowi zostanie wyświetlone okno dialogowe i wrócić do innego zadania bez anulowanie lub usuwanie okna dialogowego.  
  
 A `CDialog` obiektu jest kombinacją szablonu okna dialogowego i `CDialog`-klasy. Tworzenie szablonu okna dialogowego i zapisze go w zasobie za pomocą edytora okien dialogowych, a następnie utworzyć klasę pochodzącą od za pomocą Kreatora dodawania klasy `CDialog`.  
  
 Okno dialogowe, podobnie jak inne okno odbiera komunikaty z systemu Windows. W oknie dialogowym myślisz szczególnie obsługi komunikatów powiadomień od formantów okna dialogowego, ponieważ to jak użytkownik wchodzi w interakcję z okna dialogowego. Okno właściwości, aby wybrać wiadomości, które mają do dojścia i jego spowoduje dodanie wpisów odpowiednie mapy komunikatów i funkcje Członkowskie obsługi wiadomości do klasy dla Ciebie. Należy napisać kod specyficzne dla aplikacji w funkcji Członkowskich programu obsługi.  
  
 Jeśli wolisz, możesz zawsze zapisywać wpisy mapy wiadomości i funkcje Członkowskie ręcznie.  
  
 Nawet w najbardziej trivial okno dialogowe należy dodać zmienne Członkowskie do klasy pochodnej okien dialogowych do przechowywania danych wprowadzonych w oknie dialogowym formanty przez użytkownika lub, aby wyświetlić dane dla danego użytkownika. Kreator dodawania zmiennej służy do tworzenia zmiennych Członkowskich i skojarzyć je z kontroli. W tym samym czasie wybierz typ zmiennej i dopuszczalny zakres wartości dla każdej zmiennej. Kreator kod dodaje zmienne Członkowskie do klasy pochodnej okien dialogowych.  
  
 Mapowanie danych jest generowany automatycznie obsługi wymiany danych między formantami okno dialogowe i zmiennych Członkowskich. Mapowanie danych udostępnia funkcje, które zainicjować formantów w oknie dialogowym z odpowiednie wartości, pobierania danych i sprawdzić poprawności danych.  
  
 Aby utworzyć modalne okno dialogowe, utworzenia obiektu na stosie za pomocą konstruktora dla klasy pochodnej okien dialogowych, a następnie wywołać `DoModal` Aby utworzyć okno dialogowe i jego formantów. Jeśli chcesz utworzyć niemodalne okno dialogowe, wywołaj **Utwórz** w konstruktorze klasy okien dialogowych.  
  
 Można również utworzyć szablon w pamięci, używając [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) struktury danych, zgodnie z opisem w zestawie Windows SDK. Po utworzymy `CDialog` obiekt, należy wywołać [CreateIndirect](#createindirect) niemodalny utworzyć okno dialogowe lub wywołanie [InitModalIndirect](#initmodalindirect) i [DoModal](#domodal) można utworzyć po zakończeniu instalacji okno dialogowe.  
  
 Wymiana i Walidacja mapowanie danych jest napisany w zastępująca `CWnd::DoDataExchange` dodana do nowej klasy okna dialogowego. Zobacz [DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) funkcji członkowskiej we `CWnd` Aby uzyskać więcej informacji na temat funkcji programu exchange i sprawdzania poprawności.  
  
 Zarówno programistę i wywołanie framework `DoDataExchange` pośrednio poprzez wywołanie [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata).  
  
 Wywołania framework `UpdateData` kiedy użytkownik kliknie przycisk OK, aby zamknąć modalne okno dialogowe. (Dane nie są pobierane po kliknięciu przycisku Anuluj.) Domyślna implementacja [OnInitDialog](#oninitdialog) wymaga także `UpdateData` można ustawić wartości początkowe formantów. Zwykle zastąpienie `OnInitDialog` zainicjować dodatkowe kontrole. `OnInitDialog`jest wywoływana po wszystkich kontrolek w oknie dialogowym są tworzone i bezpośrednio przed okno dialogowe jest wyświetlane okno.  
  
 Możesz wywołać `CWnd::UpdateData` w czasie wykonywania modalne i niemodalne okno dialogowe.  
  
 W przypadku ręcznego tworzenia okno dialogowe, należy dodać zmienne Członkowskie niezbędne do klasy pochodnej okno dialogowe samodzielnie i Dodaj funkcje Członkowskie ustawić lub pobrać te wartości.  
  
 Modalne okno dialogowe zostanie zamknięte automatycznie, gdy użytkownik naciśnie przycisk OK lub Anuluj lub gdy kod wywołuje `EndDialog` funkcję elementu członkowskiego.  
  
 Po zaimplementowaniu niemodalne okno dialogowe zawsze zastępują `OnCancel` funkcji Członkowskich i wywołanie `DestroyWindow` z wewnątrz. Nie wywołuj klasy podstawowej `CDialog::OnCancel`, ponieważ wywołuje `EndDialog`, który spowoduje, że okno dialogowe niewidoczne, ale nie spowoduje zniszczenia. Należy również zastąpić `PostNcDestroy` dla niemodalnych okien dialogowych, aby usunąć **to**, ponieważ Niemodalne okna dialogowe są zazwyczaj przydzielane z **nowe**. Modalne okna dialogowe zwykle są zbudowane na ramce i nie ma potrzeby `PostNcDestroy` oczyszczania.  
  
 Aby uzyskać więcej informacji na temat funkcji `CDialog`, zobacz:  
  
- [Okna dialogowe](../../mfc/dialog-boxes.md)  
  
-   Artykuł bazy wiedzy Q262954: Porada: Tworzenie okna dialogowego Resizeable z paski przewijania  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cdialog"></a>CDialog::CDialog  
 Do tworzenia opartych na zasobach modalne okno dialogowe, wywołaj obu formularzy publicznego konstruktora.  
  
```  
explicit CDialog(
    LPCTSTR lpszTemplateName,  
    CWnd* pParentWnd = NULL);

 
explicit CDialog(
    UINT nIDTemplate,  
    CWnd* pParentWnd = NULL);  
  
CDialog();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTemplateName`  
 Zawiera zerem ciąg określający nazwę zasobu szablon okno dialogowe.  
  
 `nIDTemplate`  
 Zawiera identyfikator zasobu szablon okno dialogowe.  
  
 `pParentWnd`  
 Wskazuje obiekt okna nadrzędnego lub właściciela (typu [CWnd](../../mfc/reference/cwnd-class.md)) do której należy obiektu okna dialogowego. Jeśli jest **NULL**, okna nadrzędnego obiektu okna dialogowego ma ustawioną wartość okna głównego aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Jedna forma konstruktora zapewnia dostęp do zasobu okna dialogowego przez nazwę szablonu. Inne Konstruktor umożliwia dostęp przez identyfikator szablonu, zazwyczaj z **IDD_** prefiksu (na przykład IDD_DIALOG1).  
  
 Do utworzenia modalne okno dialogowe z szablonu w pamięci, najpierw wywołania konstruktora bez parametrów, chroniony, a następnie wywołać `InitModalIndirect`.  
  
 Po z jednej z metod powyżej utworzymy modalne okno dialogowe, wywołaj `DoModal`.  
  
 Do utworzenia niemodalne okno dialogowe, używają formy chronionych `CDialog` konstruktora. Konstruktor jest chroniony, ponieważ musi pochodzić własne okno dialogowe klasy do zaimplementowania niemodalne okno dialogowe. Konstrukcja niemodalne okno dialogowe jest procesem dwuetapowym. Pierwsze wywołanie konstruktora; następnie wywołaj **Utwórz** funkcji członkowskiej, aby utworzyć okno dialogowe oparte na zasobach, lub zadzwoń `CreateIndirect` można utworzyć okna dialogowego z szablonu w pamięci.  
  
##  <a name="create"></a>CDialog::Create  
 Wywołanie **Utwórz** można utworzyć przy użyciu szablonu okno dialogowe z zasobu niemodalne okno dialogowe.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszTemplateName,  
    CWnd* pParentWnd = NULL);

 
virtual BOOL Create(
    UINT nIDTemplate,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTemplateName`  
 Zawiera zerem ciąg określający nazwę zasobu szablon okno dialogowe.  
  
 `pParentWnd`  
 Wskazuje obiekt okna nadrzędnego (typu [CWnd](../../mfc/reference/cwnd-class.md)) do której należy obiektu okna dialogowego. Jeśli jest **NULL**, okna nadrzędnego obiektu okna dialogowego ma ustawioną wartość okna głównego aplikacji.  
  
 `nIDTemplate`  
 Zawiera identyfikator zasobu szablon okno dialogowe.  
  
### <a name="return-value"></a>Wartość zwracana  
 Oba formularze zwracać niezerowy, jeśli okno dialogowe Tworzenie i Inicjowanie zostały pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Możesz też zaznaczyć wywołanie **Utwórz** wewnątrz konstruktora lub wywołania po Konstruktor jest wywoływana.  
  
 Dwie formy **Utwórz** funkcji członkowskiej są udostępniane na potrzeby dostępu do zasobu szablon okno dialogowe szablonu nazwa lub identyfikator szablonu (na przykład IDD_DIALOG1).  
  
 Dla obu formularzy należy przekazać wskaźnik do obiektu okna nadrzędnego. Jeśli `pParentWnd` jest **NULL**, okno dialogowe zostanie utworzony z jej okna nadrzędnego lub właściciela ustawioną w głównym oknie aplikacji.  
  
 **Utwórz** funkcji członkowskiej zwraca natychmiast, po utworzeniu okna dialogowego.  
  
 Użyj **ws_visible —** stylu w szablonie okno dialogowe, jeśli podczas tworzenia okna nadrzędnego, powinny zostać wyświetlone okno dialogowe. W przeciwnym razie należy wywołać `ShowWindow`. Dalsze style okno dialogowe i ich zastosowania, zobacz [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) struktury w zestawie Windows SDK i [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) w *odwołania MFC*.  
  
 Użyj `CWnd::DestroyWindow` funkcji można zniszczyć okno dialogowe utworzone przez **Utwórz** funkcji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]  
  
##  <a name="createindirect"></a>CDialog::CreateIndirect  
 Wywołaj tę funkcję elementu członkowskiego, aby utworzyć niemodalne okno dialogowe na podstawie szablonu okno dialogowe w pamięci.  
  
```  
virtual BOOL CreateIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,  
    CWnd* pParentWnd = NULL,  
    void* lpDialogInit = NULL);

 
virtual BOOL CreateIndirect(
    HGLOBAL hDialogTemplate,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDialogTemplate`  
 Wskazuje pamięci, który zawiera okno dialogowe szablon używany do tworzenia okna dialogowego. Ten szablon jest w formie [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) struktury i kontroli informacji, zgodnie z opisem w zestawie Windows SDK.  
  
 `pParentWnd`  
 Wskazuje obiekt okna nadrzędnego obiektu okna dialogowego (typu [CWnd](../../mfc/reference/cwnd-class.md)). Jeśli jest **NULL**, okna nadrzędnego obiektu okna dialogowego ma ustawioną wartość okna głównego aplikacji.  
  
 `lpDialogInit`  
 Wskazuje **DLGINIT** zasobów.  
  
 `hDialogTemplate`  
 Zawiera dojścia do globalnej pamięci zawierającej szablon okno dialogowe. Ten szablon jest w formie **DLGTEMPLATE** strukturę i dane dla każdego formantu w oknie dialogowym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli okno dialogowe zostało utworzone i zainicjowane pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 `CreateIndirect` Funkcji członkowskiej zwraca natychmiast, po utworzeniu okna dialogowego.  
  
 Użyj **ws_visible —** stylu w szablonie okno dialogowe, jeśli podczas tworzenia okna nadrzędnego, powinny zostać wyświetlone okno dialogowe. W przeciwnym razie należy wywołać `ShowWindow` spowodować się pojawiać. Aby uzyskać więcej informacji dotyczących sposobu można określić inne okno dialogowe Style w szablonie, zobacz [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) struktury w zestawie Windows SDK.  
  
 Użyj `CWnd::DestroyWindow` funkcji można zniszczyć okno dialogowe utworzone przez `CreateIndirect` funkcji.  
  
 Okien dialogowych, które zawierają formantów ActiveX wymagają dodatkowych informacji dostępnych w **DLGINIT** zasobów. Aby uzyskać więcej informacji, zobacz artykuł bazy wiedzy Knowledge Base Q231591, "porady: Tworzenie okna dialogowego MFC z formantu ActiveX za pomocą szablonu okna dialogowego." Artykuły bazy wiedzy są dostępne pod adresem [http://support.microsoft.com](http://support.microsoft.com/).  
  
##  <a name="domodal"></a>CDialog::DoModal  
 Wywołanie tej funkcji Członkowskich do wywołania modalnego okna dialogowego i zwracają wynik okno dialogowe po zakończeniu.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `int` Wartość, która określa wartość `nResult` parametr, który został przekazany do [CDialog::EndDialog](#enddialog) funkcji członkowskiej, który jest używany, aby zamknąć okno dialogowe. Wartość zwracana jest wartość -1, jeśli funkcja nie może utworzyć okno dialogowe lub **IDABORT** Jeśli wystąpił inny błąd, w którym to przypadku w oknie danych wyjściowych będzie zawierał informacje o błędzie z [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska obsługuje wszystkich interakcji z użytkownikiem, gdy okno dialogowe jest aktywne. Jest to, co sprawia, że okno dialogowe modalne; oznacza to, że użytkownik nie mogą oddziaływać na inne okna do czasu zamknięcia okna dialogowego.  
  
 Gdy użytkownik kliknie jeden z przycisków w oknie dialogowym, takich jak OK lub przycisk Anuluj, funkcji członkowskiej obsługi wiadomości, takie jak [OnOK](#onok) lub [OnCancel](#oncancel), jest nazywany próbę zamknąć okno dialogowe. Wartość domyślna `OnOK` funkcji członkowskiej sprawdzania poprawności i aktualizowane dane okno dialogowe i zamknąć okno dialogowe z wynikiem **IDOK**, wartością domyślną `OnCancel` funkcja członkowska zostanie zamknięte okno dialogowe z wynikiem  **IDCANCEL** bez sprawdzania poprawności i aktualizowanie danych okno dialogowe. Można zastąpić te funkcje obsługi wiadomości do zmiany ich zachowania.  
  
> [!NOTE]
> `PreTranslateMessage`teraz jest wywoływana dla przetwarzania komunikatów okna modalnego okna dialogowego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]  
  
##  <a name="enddialog"></a>CDialog::EndDialog  
 Wywołanie tej funkcji Członkowskich zakończenie modalne okno dialogowe.  
  
```  
void EndDialog(int nResult);
```  
  
### <a name="parameters"></a>Parametry  
 `nResult`  
 Zawiera wartość zwracaną z okna dialogowego do wywołującego `DoModal`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego zwraca `nResult` jako wartość zwracaną `DoModal`. Należy użyć `EndDialog` funkcji do ukończenia przetwarzania zawsze, gdy jest tworzony modalne okno dialogowe.  
  
 Możesz wywołać `EndDialog` w dowolnym momencie, nawet w [OnInitDialog](#oninitdialog), w którym to przypadku należy zamknąć okno dialogowe, zanim przedstawiono lub przed skonfigurowaniem fokus wprowadzania.  
  
 `EndDialog`nie natychmiast zamknąć okno dialogowe. Zamiast ustawia Flaga, która określa, że okno dialogowe, aby zamknąć natychmiast zwraca bieżący program obsługi komunikatów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]  
  
##  <a name="getdefid"></a>CDialog::GetDefID  
 Wywołanie `GetDefID` funkcji członkowskiej, aby uzyskać identyfikator formantu łącznik domyślny dla okna dialogowego.  
  
```  
DWORD GetDefID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 32-bitową wartość ( `DWORD`). Jeśli przycisk domyślny ma wartość, zawiera słowo znaczącymi bitami **DC_HASDEFID** i word znaczącymi bitami zawiera wartość Identyfikatora. Jeśli przycisk domyślny nie ma wartość Identyfikatora, zwracana wartość to 0.  
  
### <a name="remarks"></a>Uwagi  
 Jest to zazwyczaj przycisk OK.  
  
##  <a name="gotodlgctrl"></a>CDialog::GotoDlgCtrl  
 Przenosi fokus do określonego formantu w oknie dialogowym.  
  
```  
void GotoDlgCtrl(CWnd* pWndCtrl);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndCtrl`  
 Określa okno (kontrola), który ma fokus.  
  
### <a name="remarks"></a>Uwagi  
 Otrzymywać wskaźnik do formantu (okno podrzędne) do przekazania jako `pWndCtrl`, wywołaj `CWnd::GetDlgItem` funkcji członkowskiej, która zwraca wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiektu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CWnd::GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem).  
  
##  <a name="initmodalindirect"></a>CDialog::InitModalIndirect  
 Wywołanie tej funkcji członkowskich można zainicjować obiektu modalnego okna dialogowego za pomocą szablonu okno dialogowe, które możesz utworzyć w pamięci.  
  
```  
BOOL InitModalIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,  
    CWnd* pParentWnd = NULL,  
    void* lpDialogInit = NULL);

 
    BOOL InitModalIndirect(
    HGLOBAL hDialogTemplate,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDialogTemplate`  
 Wskazuje pamięci, który zawiera okno dialogowe szablon używany do tworzenia okna dialogowego. Ten szablon jest w formie [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) struktury i kontroli informacji, zgodnie z opisem w zestawie Windows SDK.  
  
 `hDialogTemplate`  
 Zawiera dojścia do globalnej pamięci zawierającej szablon okno dialogowe. Ten szablon jest w formie **DLGTEMPLATE** strukturę i dane dla każdego formantu w oknie dialogowym.  
  
 `pParentWnd`  
 Wskazuje obiekt okna nadrzędnego lub właściciela (typu [CWnd](../../mfc/reference/cwnd-class.md)) do której należy obiektu okna dialogowego. Jeśli jest **NULL**, okna nadrzędnego obiektu okna dialogowego ma ustawioną wartość okna głównego aplikacji.  
  
 `lpDialogInit`  
 Wskazuje **DLGINIT** zasobów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli obiektu okna dialogowego zostało utworzone i zainicjowane pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby utworzyć pośrednio modalne okno dialogowe, przydzielić pamięci globalnej bloku i uzupełnij go z szablonem — okno dialogowe. Następnie wywołaj pustych `CDialog` konstruktora do konstruowania obiektu okno dialogowe. Następnie wywołaj `InitModalIndirect` do przechowywania uchwyt do szablonu okno dialogowe w pamięci. Okno dialogowe systemu Windows jest tworzone i wyświetlane później, gdy [DoModal](#domodal) została wywołana funkcja elementu członkowskiego.  
  
 Okien dialogowych, które zawierają formantów ActiveX wymagają dodatkowych informacji dostępnych w **DLGINIT** zasobów. Aby uzyskać więcej informacji, zobacz artykuł bazy wiedzy Knowledge Base Q231591, "porady: Tworzenie okna dialogowego MFC z formantu ActiveX za pomocą szablonu okna dialogowego." Artykuły bazy wiedzy są dostępne pod adresem [http://support.microsoft.com](http://support.microsoft.com/).  
  
##  <a name="mapdialogrect"></a>CDialog::MapDialogRect  
 Wywołanie Konwertuj jednostek okno dialogowe prostokąt na ekranie jednostki.  
  
```  
void MapDialogRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Wskazuje [RECT](../../mfc/reference/rect-structure1.md) struktury lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt, który zawiera okno dialogowe koordynuje do skonwertowania.  
  
### <a name="remarks"></a>Uwagi  
 Okno dialogowe jednostki są wyrażony w postaci bieżące okno dialogowe podstawowa jednostka pochodną średnia wysokość i szerokość znaków czcionki używanej w tekście okno dialogowe. Jedną jednostkę pozioma jest jedna czwarta jednostkę szerokości base okno dialogowe i jedną jednostkę pionową jest ósmego jednej jednostki podstawowej wysokość okno dialogowe.  
  
 **GetDialogBaseUnits** systemu Windows funkcja zwraca informacje o rozmiarze czcionki systemu, ale można określić inną czcionkę dla każdego — okno dialogowe, jeśli używasz **DS_SETFONT** stylu w Plik definicji zasobu. `MapDialogRect` Funkcji systemu Windows używa odpowiednią czcionkę dla tego okna dialogowego.  
  
 `MapDialogRect` Funkcji członkowskiej zastępuje jednostki okno dialogowe `lpRect` z ekranu jednostki (w pikselach), dzięki czemu prostokąt umożliwia tworzenie okna dialogowego lub ustaw kontrolkę w polu.  
  
##  <a name="nextdlgctrl"></a>CDialog::NextDlgCtrl  
 Przenosi fokus do następnego formantu w oknie dialogowym.  
  
```  
void NextDlgCtrl() const;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli koncentruje się na ostatniej formantu w oknie dialogowym, przenosi pierwszego formantu.  
  
##  <a name="oncancel"></a>CDialog::OnCancel  
 Struktura wywołuje tę metodę, gdy użytkownik kliknie **anulować** lub naciśnie klawisz ESC, w oknie dialogowym modalne i niemodalne.  
  
```  
virtual void OnCancel();
```  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę metodę w celu wykonania akcji (na przykład przywracanie stare dane) gdy użytkownik zamyka okno dialogowe, klikając **anulować** lub naciśnięcie klawisza ESC. Domyślnie zamknięcie modalne okno dialogowe przez wywołanie metody [EndDialog](#enddialog) , powodując [DoModal](#domodal) do zwrócenia IDCANCEL.  
  
 W przypadku zastosowania **anulować** przycisk w oknie dialogowym niemodalne, konieczne jest przesłonięcie `OnCancel` — metoda i wywołanie [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) wewnątrz niej. Nie wywołuj metody klasy podstawowej, ponieważ wywołuje `EndDialog`, który będzie niewidoczna okno dialogowe, ale nie zniszczyć.  
  
> [!NOTE]
>  Nie można przesłonić tę metodę, gdy używasz `CFileDialog` obiektu w programie, który ma być kompilowana w systemie Windows XP. Aby uzyskać więcej informacji na temat `CFileDialog`, zobacz [CFileDialog klasy](../../mfc/reference/cfiledialog-class.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]  
  
##  <a name="oninitdialog"></a>CDialog::OnInitDialog  
 Ta metoda jest wywoływana w odpowiedzi na `WM_INITDIALOG` wiadomości.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Określa, czy aplikacja ma fokus wprowadzania formantów w oknie dialogowym. Jeśli `OnInitDialog` zwraca różną od zera, system Windows konfiguruje fokus wprowadzania do domyślnej lokalizacji pierwszego formantu w oknie dialogowym. Aplikacja może zwrócić 0 tylko wtedy, gdy fokus wprowadzania została jawnie ustawiona do formantów w oknie dialogowym.  
  
### <a name="remarks"></a>Uwagi  
 System Windows wysyła `WM_INITDIALOG` wiadomości do okna dialogowego podczas [Utwórz](#create), [CreateIndirect](#createindirect), lub [DoModal](#domodal) wywołań, które występować bezpośrednio przed okno dialogowe zostanie wyświetlona.  
  
 Przesłania tę metodę, jeśli chcesz wykonać specjalnego przetwarzania, gdy okno dialogowe jest zainicjowany. W wersji przesłonięte, najpierw wywołaj klasę bazową `OnInitDialog` ignorowanie jego wartości zwracanej. Zwykle zwróci `TRUE` z przesłoniętą metodę.  
  
 Wywołania Windows `OnInitDialog` funkcji przy użyciu wspólnej procedury standardowe globalne — okno dialogowe do wszystkich okien dialogowych Microsoft Foundation Class Library. Nie wywołuje tej funkcji za pośrednictwem mapy komunikatów, a więc nie trzeba wpisu mapy komunikatów dla tej metody.  
  
> [!NOTE]
>  Nie można przesłonić tę metodę, gdy używasz `CFileDialog` obiektu w programie, który ma być kompilowana w obszarze [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]. Aby uzyskać więcej informacji o zmianach `CFileDialog` w obszarze [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] zobacz [CFileDialog klasy](../../mfc/reference/cfiledialog-class.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]  
  
##  <a name="onok"></a>CDialog::OnOK  
 Wywoływane, gdy użytkownik kliknie **OK** (przycisk z Identyfikatorem IDOK).  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę metodę w celu wykonania akcji po **OK** przycisk jest aktywny. Jeśli okno dialogowe zawiera automatyczne weryfikacji i danych programu exchange, domyślna implementacja tej metody sprawdza poprawność danych okna dialogowego i aktualizuje odpowiednich zmiennych w aplikacji.  
  
 W przypadku zastosowania **OK** przycisk w oknie dialogowym niemodalne, konieczne jest przesłonięcie `OnOK` — metoda i wywołanie [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) wewnątrz niej. Nie wywołuj metody klasy podstawowej, ponieważ wywołuje [EndDialog](#enddialog) który sprawia, że okno dialogowe jest niewidoczny, ale nie zniszczenia.  
  
> [!NOTE]
>  Nie można przesłonić tę metodę, gdy używasz `CFileDialog` obiektu w programie, który ma być kompilowana w systemie Windows XP. Aby uzyskać więcej informacji na temat `CFileDialog`, zobacz [CFileDialog klasy](../../mfc/reference/cfiledialog-class.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]  
  
##  <a name="onsetfont"></a>CDialog::OnSetFont  
 Określa czcionkę używaną przez okno dialogowe formantu ma być używany podczas rysowania tekstu.  
  
```  
Virtual void OnSetFont(CFont* pFont);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pFont`  
 Określa czcionkę, która będzie służyć jako domyślną czcionkę dla wszystkich kontrolek w oknie dialogowym wskaźnik.  
  
### <a name="remarks"></a>Uwagi  
 Okno dialogowe użyje określonej czcionki jako domyślny dla wszystkich jej kontrolek.  
  
 Edytor okien dialogowych zwykle ustawia okno dialogowe czcionki w ramach zasobu szablon okno dialogowe.  
  
> [!NOTE]
>  Nie można przesłonić tę metodę, gdy używasz `CFileDialog` obiektu w programie, który ma być kompilowana w obszarze [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]. Aby uzyskać więcej informacji o zmianach `CFileDialog` w obszarze [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] zobacz [CFileDialog klasy](../../mfc/reference/cfiledialog-class.md).  
  
##  <a name="prevdlgctrl"></a>CDialog::PrevDlgCtrl  
 Ustawia fokus poprzedniego formantu w oknie dialogowym.  
  
```  
void PrevDlgCtrl() const;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli koncentruje się na pierwszą kontrolkę w oknie dialogowym, powoduje przeniesienie do ostatniego formantu w polu.  
  
##  <a name="setdefid"></a>CDialog::SetDefID  
 Zmienia kontroli łącznik domyślny dla okna dialogowego.  
  
```  
void SetDefID(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Określa identyfikator formantu łącznik, który ma zostać domyślny.  
  
##  <a name="sethelpid"></a>CDialog::SetHelpID  
 Ustawia identyfikator pomocy kontekstowej dla okna dialogowego.  
  
```  
void SetHelpID(UINT nIDR);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDR*  
 Określa identyfikator pomoc kontekstową.  
  
## <a name="see-also"></a>Zobacz też  
 [DLGCBR32 próbki MFC](../../visual-cpp-samples.md)   
 [Przykładowe MFC DLGTEMPL](../../visual-cpp-samples.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)

