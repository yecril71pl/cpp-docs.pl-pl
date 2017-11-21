---
title: "Cricheditview — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRichEditView
- AFXRICH/CRichEditView
- AFXRICH/CRichEditView::CRichEditView
- AFXRICH/CRichEditView::AdjustDialogPosition
- AFXRICH/CRichEditView::CanPaste
- AFXRICH/CRichEditView::DoPaste
- AFXRICH/CRichEditView::FindText
- AFXRICH/CRichEditView::FindTextSimple
- AFXRICH/CRichEditView::GetCharFormatSelection
- AFXRICH/CRichEditView::GetDocument
- AFXRICH/CRichEditView::GetInPlaceActiveItem
- AFXRICH/CRichEditView::GetMargins
- AFXRICH/CRichEditView::GetPageRect
- AFXRICH/CRichEditView::GetPaperSize
- AFXRICH/CRichEditView::GetParaFormatSelection
- AFXRICH/CRichEditView::GetPrintRect
- AFXRICH/CRichEditView::GetPrintWidth
- AFXRICH/CRichEditView::GetRichEditCtrl
- AFXRICH/CRichEditView::GetSelectedItem
- AFXRICH/CRichEditView::GetTextLength
- AFXRICH/CRichEditView::GetTextLengthEx
- AFXRICH/CRichEditView::InsertFileAsObject
- AFXRICH/CRichEditView::InsertItem
- AFXRICH/CRichEditView::IsRichEditFormat
- AFXRICH/CRichEditView::OnCharEffect
- AFXRICH/CRichEditView::OnParaAlign
- AFXRICH/CRichEditView::OnUpdateCharEffect
- AFXRICH/CRichEditView::OnUpdateParaAlign
- AFXRICH/CRichEditView::PrintInsideRect
- AFXRICH/CRichEditView::PrintPage
- AFXRICH/CRichEditView::SetCharFormat
- AFXRICH/CRichEditView::SetMargins
- AFXRICH/CRichEditView::SetPaperSize
- AFXRICH/CRichEditView::SetParaFormat
- AFXRICH/CRichEditView::TextNotFound
- AFXRICH/CRichEditView::GetClipboardData
- AFXRICH/CRichEditView::GetContextMenu
- AFXRICH/CRichEditView::IsSelected
- AFXRICH/CRichEditView::OnFindNext
- AFXRICH/CRichEditView::OnInitialUpdate
- AFXRICH/CRichEditView::OnPasteNativeObject
- AFXRICH/CRichEditView::OnPrinterChanged
- AFXRICH/CRichEditView::OnReplaceAll
- AFXRICH/CRichEditView::OnReplaceSel
- AFXRICH/CRichEditView::OnTextNotFound
- AFXRICH/CRichEditView::QueryAcceptData
- AFXRICH/CRichEditView::WrapChanged
- AFXRICH/CRichEditView::m_nBulletIndent
- AFXRICH/CRichEditView::m_nWordWrap
dev_langs: C++
helpviewer_keywords:
- CRichEditView [MFC], CRichEditView
- CRichEditView [MFC], AdjustDialogPosition
- CRichEditView [MFC], CanPaste
- CRichEditView [MFC], DoPaste
- CRichEditView [MFC], FindText
- CRichEditView [MFC], FindTextSimple
- CRichEditView [MFC], GetCharFormatSelection
- CRichEditView [MFC], GetDocument
- CRichEditView [MFC], GetInPlaceActiveItem
- CRichEditView [MFC], GetMargins
- CRichEditView [MFC], GetPageRect
- CRichEditView [MFC], GetPaperSize
- CRichEditView [MFC], GetParaFormatSelection
- CRichEditView [MFC], GetPrintRect
- CRichEditView [MFC], GetPrintWidth
- CRichEditView [MFC], GetRichEditCtrl
- CRichEditView [MFC], GetSelectedItem
- CRichEditView [MFC], GetTextLength
- CRichEditView [MFC], GetTextLengthEx
- CRichEditView [MFC], InsertFileAsObject
- CRichEditView [MFC], InsertItem
- CRichEditView [MFC], IsRichEditFormat
- CRichEditView [MFC], OnCharEffect
- CRichEditView [MFC], OnParaAlign
- CRichEditView [MFC], OnUpdateCharEffect
- CRichEditView [MFC], OnUpdateParaAlign
- CRichEditView [MFC], PrintInsideRect
- CRichEditView [MFC], PrintPage
- CRichEditView [MFC], SetCharFormat
- CRichEditView [MFC], SetMargins
- CRichEditView [MFC], SetPaperSize
- CRichEditView [MFC], SetParaFormat
- CRichEditView [MFC], TextNotFound
- CRichEditView [MFC], GetClipboardData
- CRichEditView [MFC], GetContextMenu
- CRichEditView [MFC], IsSelected
- CRichEditView [MFC], OnFindNext
- CRichEditView [MFC], OnInitialUpdate
- CRichEditView [MFC], OnPasteNativeObject
- CRichEditView [MFC], OnPrinterChanged
- CRichEditView [MFC], OnReplaceAll
- CRichEditView [MFC], OnReplaceSel
- CRichEditView [MFC], OnTextNotFound
- CRichEditView [MFC], QueryAcceptData
- CRichEditView [MFC], WrapChanged
- CRichEditView [MFC], m_nBulletIndent
- CRichEditView [MFC], m_nWordWrap
ms.assetid: bd576b10-4cc0-4050-8f76-e1a0548411e4
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 604e226a903b8cbb518d02cac4230d7d17cc4528
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cricheditview-class"></a>Cricheditview — klasa
Z [cricheditdoc —](../../mfc/reference/cricheditdoc-class.md) i [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), udostępnia funkcje kontrolki zaawansowanej edycji w kontekście architektura widoku dokumentu MFC.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CRichEditView : public CCtrlView  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRichEditView::CRichEditView](#cricheditview)|Konstruuje `CRichEditView` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|Przenosi okno dialogowe, tak aby nie przesłaniać bieżącego zaznaczenia.|  
|[CRichEditView::CanPaste](#canpaste)|Informuje, czy Schowek zawiera dane, które można wkleić do widoku bogatej edycji.|  
|[CRichEditView::DoPaste](#dopaste)|Wkleja element OLE do tego widoku bogatej edycji.|  
|[CRichEditView::FindText](#findtext)|Znajduje określony tekst wywoływania kursora oczekiwania.|  
|[CRichEditView::FindTextSimple](#findtextsimple)|Znajduje określony tekst.|  
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|Pobiera atrybuty dla bieżącego wyboru formatowanie znaków.|  
|[CRichEditView::GetDocument](#getdocument)|Pobiera wskaźnik do pokrewny [cricheditdoc —](../../mfc/reference/cricheditdoc-class.md).|  
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|Pobiera element OLE, który jest obecnie aktywny w miejscu w widoku bogatej edycji.|  
|[CRichEditView::GetMargins](#getmargins)|Pobiera marginesy dla tego widoku bogatej edycji.|  
|[CRichEditView::GetPageRect](#getpagerect)|Pobiera prostokąt strony dla tego widoku bogatej edycji.|  
|[CRichEditView::GetPaperSize](#getpapersize)|Pobiera rozmiar papieru dla tego widoku bogatej edycji.|  
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|Pobiera atrybuty dla bieżącego wyboru formatowania akapitu.|  
|[CRichEditView::GetPrintRect](#getprintrect)|Pobiera prostokąt wydruku dla tego widoku bogatej edycji.|  
|[CRichEditView::GetPrintWidth](#getprintwidth)|Pobiera szerokość wydruku dla tego widoku bogatej edycji.|  
|[CRichEditView::GetRichEditCtrl](#getricheditctrl)|Pobiera kontrolki zaawansowanej edycji.|  
|[CRichEditView::GetSelectedItem](#getselecteditem)|Pobiera wybrany element z widoku bogatej edycji.|  
|[CRichEditView::GetTextLength](#gettextlength)|Pobiera długość tekstu w widoku bogatej edycji.|  
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|Pobiera liczbę znaków lub bajtów w widoku bogatej edycji. Lista rozwinięte flagi dla metody określania długości.|  
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|Wstawia plik jako element OLE.|  
|[CRichEditView::InsertItem](#insertitem)|Wstawia nowy element jako element OLE.|  
|[CRichEditView::IsRichEditFormat](#isricheditformat)|Informuje, czy Schowek zawiera dane zaawansowanej edycji lub w formacie tekstowym.|  
|[CRichEditView::OnCharEffect](#onchareffect)|Włącza/wyłącza znak formatowania dla bieżącego zaznaczenia.|  
|[CRichEditView::OnParaAlign](#onparaalign)|Zmienia położenie akapitów.|  
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|Aktualizuje polecenia interfejsu użytkownika dla funkcji publicznego elementu członkowskiego znaków.|  
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|Aktualizuje polecenia interfejsu użytkownika dla funkcji publicznego elementu członkowskiego akapitu.|  
|[CRichEditView::PrintInsideRect](#printinsiderect)|Formatuje określonego tekstu w prostokącie danego.|  
|[CRichEditView::PrintPage](#printpage)|Formatuje określony tekst w ramach danej strony.|  
|[CRichEditView::SetCharFormat](#setcharformat)|Ustawia znak formatowanie atrybutów dla bieżącego zaznaczenia.|  
|[CRichEditView::SetMargins](#setmargins)|Ustawia marginesów to zaawansowana Edytowanie widoku.|  
|[CRichEditView::SetPaperSize](#setpapersize)|Określa rozmiar papieru dla tego widoku bogatej edycji.|  
|[CRichEditView::SetParaFormat](#setparaformat)|Ustawia atrybuty dla bieżącego wyboru formatowania akapitu.|  
|[CRichEditView::TextNotFound](#textnotfound)|Resetuje stan wewnętrzny wyszukiwania formantu.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRichEditView::GetClipboardData](#getclipboarddata)|Pobiera obiekt Schowka dla zakresu tego widoku bogatej edycji.|  
|[CRichEditView::GetContextMenu](#getcontextmenu)|Pobiera menu kontekstowe do użycia na prawy przycisk myszy w dół.|  
|[CRichEditView::IsSelected](#isselected)|Wskazuje zaznaczenie danego elementu OLE, czy nie.|  
|[CRichEditView::OnFindNext](#onfindnext)|Znajduje następne wystąpienie podciągu.|  
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|Odświeżanie widoku przy pierwszym dołączony do dokumentu.|  
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|Pobiera dane natywne z elementu OLE.|  
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|Ustawia parametry wydruku dla danego urządzenia.|  
|[CRichEditView::OnReplaceAll](#onreplaceall)|Zamienia wszystkie wystąpienia ciągu nowe parametry.|  
|[CRichEditView::OnReplaceSel](#onreplacesel)|Zamienia bieżące zaznaczenie.|  
|[CRichEditView::OnTextNotFound](#ontextnotfound)|Obsługuje powiadomienia użytkownika, który nie znaleziono żądanego tekstu.|  
|[CRichEditView::QueryAcceptData](#queryacceptdata)|Zapytania, aby zobaczyć o danych na `IDataObject`.|  
|[CRichEditView::WrapChanged](#wrapchanged)|Dostosowuje docelowe urządzenie wyjściowe dla tego zaawansowanej edycji widok, w oparciu o wartości `m_nWordWrap`.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|Wskazuje wielkość wcięcie dla punktora list.|  
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|Wskazuje ograniczenia zawijania programu word.|  
  
## <a name="remarks"></a>Uwagi  
 "Kontrolki zaawansowanej edycji" jest oknem, w którym użytkownik może wprowadzić i edytować tekst. Tekst można przypisać formatowanie znaków i akapitów i mogą zawierać osadzonych obiektów OLE. Formanty edycji wzbogaconej udostępniają interfejs programowania do formatowania tekstu. Jednak aplikacja musi implementować wszystkie składniki interfejsu użytkownika należy udostępnić użytkownikowi operacji formatowania.  
  
 `CRichEditView`przechowuje tekst i właściwości formatowania tekstu. `CRichEditDoc`przechowuje listę OLE elementy klienckie, które znajdują się w widoku. `CRichEditCntrItem`udostępnia kontener po stronie klienta elementu OLE.  
  
 Ten formant wspólne systemu Windows (i w związku z tym [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) i związanych z klasy) jest dostępne tylko dla programów w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.  
  
 Na przykład przy użyciu widoku bogatej edycji w aplikacji MFC, zobacz [WORDPAD](../../visual-cpp-samples.md) przykładowej aplikacji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cview —](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CRichEditView`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrich.h  
  
##  <a name="adjustdialogposition"></a>CRichEditView::AdjustDialogPosition  
 Wywołanie tej funkcji, aby przenieść okno dialogowe danego, tak aby nie mogą zasłaniać bieżącego zaznaczenia.  
  
```  
void AdjustDialogPosition(CDialog* pDlg);
```  
  
### <a name="parameters"></a>Parametry  
 *pDlg*  
 Wskaźnik do `CDialog` obiektu.  
  
##  <a name="canpaste"></a>CRichEditView::CanPaste  
 Wywołanie tej funkcji w celu ustalenia, czy Schowka zawiera informacje, które można wkleić do tego widoku bogatej edycji.  
  
```  
BOOL CanPaste() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli Schowek zawiera dane w formacie, który może zaakceptować tego widoku bogatej edycji; w przeciwnym razie wartość 0.  
  
##  <a name="cricheditview"></a>CRichEditView::CRichEditView  
 Wywołanie tej funkcji, aby utworzyć `CRichEditView` obiektu.  
  
```  
CRichEditView();
```  
  
##  <a name="dopaste"></a>CRichEditView::DoPaste  
 Wywołanie tej funkcji można wkleić elementu OLE w `dataobj` do tego dokumentu/widoku edycji wzbogaconej.  
  
```  
void DoPaste(
    COleDataObject& dataobj,  
    CLIPFORMAT cf,  
    HMETAFILEPICT hMetaPict);
```  
  
### <a name="parameters"></a>Parametry  
 `dataobj`  
 [COleDataObject](../../mfc/reference/coledataobject-class.md) zawierające dane, aby wkleić.  
  
 `cf`  
 Żądany format Schowka.  
  
 `hMetaPict`  
 Metaplik, który reprezentuje element, aby można było ją wkleić.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tej funkcji w ramach Domyślna implementacja [QueryAcceptData](#queryacceptdata).  
  
 Ta funkcja określa typ Wklej na podstawie wyników obsługi dla Wklej specjalne. Jeśli `cf` wynosi 0, nowy element używa bieżącej reprezentacja ikony. Jeśli `cf` jest różna od zera i `hMetaPict` nie jest **NULL**, używa nowego elementu `hMetaPict` dla jej reprezentacji.  
  
##  <a name="findtext"></a>CRichEditView::FindText  
 Wywołanie tej funkcji można znaleźć określony tekst i ustaw ją jako bieżącego zaznaczenia.  
  
```  
BOOL FindText(
    LPCTSTR lpszFind,  
    BOOL bCase = TRUE,  
    BOOL bWord = TRUE,  
    BOOL bNext = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Zawiera ciąg do wyszukania.  
  
 `bCase`  
 Wskazuje, czy wyszukiwanie jest uwzględniana wielkość liter.  
  
 `bWord`  
 Wskazuje, czy wyszukiwanie powinien być zgodny tylko całe wyrazy, nie części słowa.  
  
 `bNext`  
 Wskazuje kierunek wyszukiwania. Jeśli **TRUE**, jest skierowany wyszukiwania do końca buforu. Jeśli **FALSE**, kierunek wyszukiwania jest początku buforu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe `lpszFind` zostanie znaleziony tekst; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wyświetla kursor oczekiwania podczas operacji wyszukiwania.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]  
  
##  <a name="findtextsimple"></a>CRichEditView::FindTextSimple  
 Wywołanie tej funkcji można znaleźć określony tekst i ustaw ją jako bieżącego zaznaczenia.  
  
```  
BOOL FindTextSimple(
    LPCTSTR lpszFind,  
    BOOL bCase = TRUE,  
    BOOL bWord = TRUE,  
    BOOL bNext = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Zawiera ciąg do wyszukania.  
  
 `bCase`  
 Wskazuje, czy wyszukiwanie jest uwzględniana wielkość liter.  
  
 `bWord`  
 Wskazuje, czy wyszukiwanie powinien być zgodny tylko całe wyrazy, nie części słowa.  
  
 `bNext`  
 Wskazuje kierunek wyszukiwania. Jeśli **TRUE**, jest skierowany wyszukiwania do końca buforu. Jeśli **FALSE**, kierunek wyszukiwania jest początku buforu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe `lpszFind` zostanie znaleziony tekst; w przeciwnym razie wartość 0.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CRichEditView::FindText](#findtext).  
  
##  <a name="getcharformatselection"></a>CRichEditView::GetCharFormatSelection  
 Wywołanie tej funkcji można pobrać atrybutów bieżącego zaznaczenia formatowania znaków.  
  
```  
CHARFORMAT2& GetCharFormatSelection();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) strukturę, która zawiera znak formatowanie atrybutów bieżącego zaznaczenia.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [EM_GETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb788026) wiadomości i [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) struktury w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]  
  
##  <a name="getclipboarddata"></a>CRichEditView::GetClipboardData  
 Struktura wywołuje tej funkcji w ramach przetwarzania [IRichEditOleCallback::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774315).  
  
```  
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,  
    DWORD dwReco,  
    LPDATAOBJECT lpRichDataObj,  
    LPDATAOBJECT* lplpdataobj);
```  
  
### <a name="parameters"></a>Parametry  
 `lpchrg`  
 Wskaźnik do [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) struktury, określając zakres znaków (i elementy OLE), aby skopiować na obiekt danych określonego przez `lplpdataobj`.  
  
 `dwReco`  
 Flaga operację Schowka. Może być jedną z następujących wartości.  
  
- **RECO_COPY** Kopiuj do Schowka.  
  
- **RECO_CUT** wyciąć do Schowka.  
  
- **RECO_DRAG** przeciągnij operacji (przeciąganie i upuszczanie).  
  
- **RECO_DROP** porzucić operacji (przeciąganie i upuszczanie).  
  
- **RECO_PASTE** Wklej ze Schowka.  
  
 `lpRichDataObj`  
 Wskaźnik do [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) obiekt zawierający dane Schowka z zaawansowanej edycji ( [IRichEditOle::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774341)).  
  
 `lplpdataobj`  
 Wskaźnik do zmiennej wskaźnikowej, który odbiera adres `IDataObject` obiekt reprezentujący zakresu określonego w `lpchrg` parametru. Wartość `lplpdataobj` jest ignorowana, jeśli zostanie zwrócony błąd.  
  
### <a name="return-value"></a>Wartość zwracana  
 `HRESULT` Wartość raportowania powodzenie operacji. Aby uzyskać więcej informacji na temat `HRESULT`, zobacz [struktury COM kody błędów](http://msdn.microsoft.com/library/windows/desktop/ms690088) w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartości zwracanej wskazuje Powodzenie, **IRichEditOleCallback::GetClipboardData** zwraca `IDataObject` uzyskiwał `lplpdataobj`; w przeciwnym razie zwraca jeden z niego `lpRichDataObj`. Zastąp tę funkcję, aby podać własne dane do Schowka. Domyślna implementacja ta funkcja zwraca **E_NOTIMPL**.  
  
 Jest to zaawansowane możliwym do zastąpienia.  
  
 Aby uzyskać więcej informacji, zobacz [IRichEditOle::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774341), [IRichEditOleCallback::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774315), i [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) w zestaw SDK systemu Windows, zobacz [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) w systemie Windows SDK.  
  
##  <a name="getcontextmenu"></a>CRichEditView::GetContextMenu  
 Struktura wywołuje tej funkcji w ramach przetwarzania [IRichEditOleCallback::GetContextMenu](http://msdn.microsoft.com/library/windows/desktop/bb774317).  
  
```  
virtual HMENU GetContextMenu(
    WORD seltyp,  
    LPOLEOBJECT lpoleobj,  
    CHARRANGE* lpchrg);
```  
  
### <a name="parameters"></a>Parametry  
 *seltyp*  
 Typ zaznaczenia. Wybór typu wartości zostały opisane w sekcji uwag.  
  
 `lpoleobj`  
 Wskaźnik do **OLEOBJECT** struktury Określanie pierwszego wybranego obiektu OLE, jeśli zaznaczenie zawiera co najmniej jeden element OLE. Jeśli zaznaczenie nie zawiera elementów, `lpoleobj` jest **NULL**. **OLEOBJECT** struktura zawiera wskaźnik do obiektu OLE v tabeli.  
  
 `lpchrg`  
 Wskaźnik do [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) struktury zawierającej bieżącego zaznaczenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do menu kontekstowego.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest typowy część prawego przycisku myszy w dół do przetwarzania.  
  
 Typ zaznaczenia może być dowolną kombinacją flag następujące:  
  
- `SEL_EMPTY`Wskazuje, że nie ma żadnego bieżącego zaznaczenia.  
  
- `SEL_TEXT`Wskazuje, że bieżące zaznaczenie zawiera tekst.  
  
- `SEL_OBJECT`Wskazuje, że bieżące zaznaczenie zawiera co najmniej jeden element OLE.  
  
- `SEL_MULTICHAR`Wskazuje, że bieżące zaznaczenie zawiera więcej niż jednego znaku tekstu.  
  
- `SEL_MULTIOBJECT`Wskazuje, że bieżące zaznaczenie zawiera więcej niż jeden obiekt OLE.  
  
 Domyślna implementacja zwraca **NULL**. Jest to zaawansowane możliwym do zastąpienia.  
  
 Aby uzyskać więcej informacji, zobacz [IRichEditOleCallback::GetContextMenu](http://msdn.microsoft.com/library/windows/desktop/bb774317) i [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji na temat **OLEOBJECT** typu, zobacz artykuł struktur danych OLE i struktura alokacji w *OLE wiedzy*.  
  
##  <a name="getdocument"></a>CRichEditView::GetDocument  
 Wywołanie tej funkcji, aby uzyskać wskaźnik do `CRichEditDoc` skojarzonego z tym widokiem.  
  
```  
CRichEditDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [cricheditdoc —](../../mfc/reference/cricheditdoc-class.md) obiekt skojarzony z Twojej `CRichEditView` obiektu.  
  
##  <a name="getinplaceactiveitem"></a>CRichEditView::GetInPlaceActiveItem  
 Wywołanie tej funkcji, aby uzyskać OLE elementu, który jest aktywowany w miejscu, w tym `CRichEditView` obiektu.  
  
```  
CRichEditCntrItem* GetInPlaceActiveItem() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pojedynczego, w miejsce aktywne [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) obiektu w tym widoku bogatej edycji; **NULL** Jeśli nie ma elementu OLE obecnie w stanie aktywnym w miejscu.  
  
##  <a name="getmargins"></a>CRichEditView::GetMargins  
 Wywołanie tej funkcji można pobrać bieżącego marginesy używany podczas drukowania.  
  
```  
CRect GetMargins() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Marginesy używane w drukowaniu, mierzony w `MM_TWIPS`.  
  
##  <a name="getpagerect"></a>CRichEditView::GetPageRect  
 Wywołanie tej funkcji można pobrać wymiary strony drukowania.  
  
```  
CRect GetPageRect() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Granice strony drukowanie, mierzony w `MM_TWIPS`.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość zależy od rozmiaru papieru.  
  
##  <a name="getpapersize"></a>CRichEditView::GetPaperSize  
 Wywołanie tej funkcji można pobrać bieżącego rozmiaru papieru.  
  
```  
CSize GetPaperSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar papieru, używane podczas drukowania, mierzony w `MM_TWIPS`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]  
  
##  <a name="getparaformatselection"></a>CRichEditView::GetParaFormatSelection  
 Wywołanie tej funkcji, aby uzyskać atrybuty bieżącego zaznaczenia formatowania akapitu.  
  
```  
PARAFORMAT2& GetParaFormatSelection();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) struktury, który zawiera atrybuty bieżącego zaznaczenia formatowania akapitu.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [EM_GETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774182) wiadomości i [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) struktury w zestawie Windows SDK.  
  
##  <a name="getprintrect"></a>CRichEditView::GetPrintRect  
 Wywołanie tej funkcji można pobrać granice obszar drukowania w prostokącie strony.  
  
```  
CRect GetPrintRect() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Granice obszaru obrazu używane w drukowaniu, mierzony w `MM_TWIPS`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]  
  
##  <a name="getprintwidth"></a>CRichEditView::GetPrintWidth  
 Wywołanie tej funkcji, aby określić szerokość obszaru drukowania.  
  
```  
int GetPrintWidth() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość obszaru drukowania, mierzony w `MM_TWIPS`.  
  
##  <a name="getricheditctrl"></a>CRichEditView::GetRichEditCtrl  
 Wywołanie tej funkcji można pobrać [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) obiekt skojarzony z `CRichEditView` obiektu.  
  
```  
CRichEditCtrl& GetRichEditCtrl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `CRichEditCtrl` Obiekt dla tego widoku.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CRichEditView::FindText](#findtext).  
  
##  <a name="getselecteditem"></a>CRichEditView::GetSelectedItem  
 Wywołanie tej funkcji można pobrać elementu OLE ( `CRichEditCntrItem` obiektu) aktualnie wybranego w tym `CRichEditView` obiektu.  
  
```  
CRichEditCntrItem* GetSelectedItem() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) obiekt wybrany w `CRichEditView` obiekt; **NULL** Jeśli nie wybrano elementów w tym widoku.  
  
##  <a name="gettextlength"></a>CRichEditView::GetTextLength  
 Wywołanie tej funkcji można pobrać długość tekstu w tym `CRichEditView` obiektu.  
  
```  
long GetTextLength() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość tekstu w tym `CRichEditView` obiektu.  
  
##  <a name="gettextlengthex"></a>CRichEditView::GetTextLengthEx  
 Wywołanie tej funkcji Członkowskich do obliczenia długość tekstu w tym `CRichEditView` obiektu.  
  
```  
long GetTextLengthEx(
    DWORD dwFlags,  
    UINT uCodePage = -1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Wartość określającą metoda do użycia przy określaniu długość tekstu. Ten element członkowski może być jeden lub więcej wartości na liście flagi członkiem [GETTEXTLENGTHEX](http://msdn.microsoft.com/library/windows/desktop/bb787915) opisanego w zestawie Windows SDK.  
  
 `uCodePage`  
 Strona kodowa do tłumaczenia (CP_ACP strony kodowej ANSI, 1200 standardu Unicode).  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba znaków lub bajtów w formancie edycyjnym. Jeśli ustawiono flagi niezgodne `dwFlags`, zwraca funkcji członkowskiej `E_INVALIDARG`.  
  
### <a name="remarks"></a>Uwagi  
 `GetTextLengthEx`udostępnia dodatkowe sposoby określania długość tekstu. Obsługuje funkcje zaawansowanej edycji 2.0. Aby uzyskać więcej informacji, zobacz [o zaawansowanej edycji kontrolki](http://msdn.microsoft.com/library/windows/desktop/bb787873) w zestawie Windows SDK.  
  
##  <a name="insertfileasobject"></a>CRichEditView::InsertFileAsObject  
 Wywołanie tej funkcji, aby wstawić określonego pliku (jako [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) obiektu) do wzbogaconej Edytowanie widoku.  
  
```  
void InsertFileAsObject(LPCTSTR lpszFileName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFileName`  
 Ciąg zawierający nazwę pliku do wstawienia.  
  
##  <a name="insertitem"></a>CRichEditView::InsertItem  
 Wywołanie tej funkcji, aby wstawić [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) obiektu do widoku bogatej edycji.  
  
```  
HRESULT InsertItem(CRichEditCntrItem* pItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Wskaźnik do elementu, który ma zostać wstawiony.  
  
### <a name="return-value"></a>Wartość zwracana  
 `HRESULT` Wartość wskazującą, czy wstawiania.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat `HRESULT`, zobacz [struktury COM kody błędów](http://msdn.microsoft.com/library/windows/desktop/ms690088) w zestawie Windows SDK.  
  
##  <a name="isricheditformat"></a>CRichEditView::IsRichEditFormat  
 Wywołanie tej funkcji, aby ustalić, czy `cf` to format schowka tekstu, tekstu sformatowanego lub tekstu sformatowanego z elementami OLE.  
  
```  
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 Format schowka zainteresowań.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe `cf` jest sformatowany tekst lub edycji formatu Schowka.  
  
##  <a name="isselected"></a>CRichEditView::IsSelected  
 Wywołanie tej funkcji w celu określenia, jeśli określony element OLE jest aktualnie wybrane w tym widoku.  
  
```  
virtual BOOL IsSelected(const CObject* pDocItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pDocItem`  
 Wskaźnik do obiektu w widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli obiekt jest zaznaczony; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, jeśli klasy pochodnej widoku ma inną metodę obsługi zaznaczenia elementów OLE.  
  
##  <a name="m_nbulletindent"></a>CRichEditView::m_nBulletIndent  
 Wcięcie dla punktora elementów na liście; Domyślnie 720 jednostki, która jest 1/2 cala.  
  
```  
int m_nBulletIndent;  
```  
  
##  <a name="m_nwordwrap"></a>CRichEditView::m_nWordWrap  
 Wskazuje typ zawijanie wierszy dla tego widoku bogatej edycji.  
  
```  
int m_nWordWrap;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jedna z następujących wartości:  
  
- `WrapNone`Wskazuje nie automatycznego zawijania.  
  
- `WrapToWindow`Wskazuje, na podstawie szerokości okna zawijania wyrazów.  
  
- `WrapToTargetDevice`Wskazuje zawijania wyrazów na podstawie charakterystyk urządzenia docelowego.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CRichEditView::WrapChanged](#wrapchanged).  
  
##  <a name="onchareffect"></a>CRichEditView::OnCharEffect  
 Wywołanie tej funkcji, aby przełączyć znak Formatowanie efektów dla bieżącego zaznaczenia.  
  
```  
void OnCharEffect(
    DWORD dwMask,  
    DWORD dwEffect);
```  
  
### <a name="parameters"></a>Parametry  
 `dwMask`  
 Efekty modyfikowania w bieżącym zaznaczeniu formatowanie znaków.  
  
 `dwEffect`  
 Żądany lista znak efekty Przełącz ustawienie opcji formatowania.  
  
### <a name="remarks"></a>Uwagi  
 Każde wywołanie tej funkcji przełącza określony efekty formatowania dla bieżącego zaznaczenia.  
  
 Aby uzyskać więcej informacji na temat `dwMask` i `dwEffect` parametrów i ich potencjalne wartości, zobacz odpowiednie elementy członkowskie danych z [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]  
  
##  <a name="onfindnext"></a>CRichEditView::OnFindNext  
 Wywoływane przez platformę, gdy przetwarzanie poleceń w oknie dialogowym Znajdowanie i zamienianie.  
  
```  
virtual void OnFindNext(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    BOOL bWord);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Ciąg do znalezienia.  
  
 `bNext`  
 Kierunek wyszukiwania: **TRUE** wskazuje; **FALSE**, nawet.  
  
 `bCase`  
 Wskazuje, czy wyszukiwanie ma uwzględniać wielkość liter.  
  
 `bWord`  
 Wskazuje, czy wyszukiwanie jest dopasowywanie całych wyrazów tylko lub nie.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można znaleźć tekst wewnątrz `CRichEditView`. Należy przesłonić tę funkcję, aby zmienić właściwości wyszukiwania dla klasy pochodnej widoku.  
  
##  <a name="oninitialupdate"></a>CRichEditView::OnInitialUpdate  
 Wywoływane przez platformę po widoku najpierw jest dołączony do dokumentu, ale przed wyświetleniu widoku.  
  
```  
virtual void OnInitialUpdate();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ta funkcja wymaga [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) funkcji członkowskiej bez informacji o wskazówki (oznacza to, za pomocą domyślnej wartości 0 dla `lHint` parametru i **NULL** dla `pHint` parametru). Należy przesłonić tę funkcję, by wykonać jednorazowe inicjowanie, która wymaga informacji na temat dokumentu. Na przykład jeśli aplikacja ma dokumentów o stałym rozmiarze, funkcja ta zainicjować limity przewijania widoku na podstawie rozmiaru dokumentu. Jeśli aplikacja obsługuje dokumenty o zmiennej długości, użyj `OnUpdate` zaktualizować przewijania ogranicza zawsze zmiany w dokumencie.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CRichEditView::m_nWordWrap](#m_nwordwrap).  
  
##  <a name="onpastenativeobject"></a>CRichEditView::OnPasteNativeObject  
 Ta funkcja służy do ładowania danych natywnych z element osadzony.  
  
```  
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```  
  
### <a name="parameters"></a>Parametry  
 *lpStg*  
 Wskaźnik do [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość 0;  
  
### <a name="remarks"></a>Uwagi  
 Zazwyczaj można to zrobić, tworząc [COleStreamFile](../../mfc/reference/colestreamfile-class.md) wokół `IStorage`. `COleStreamFile` Może zostać dołączony do archiwum i [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) o nazwie do ładowania danych.  
  
 Jest to zaawansowane możliwym do zastąpienia.  
  
 Aby uzyskać więcej informacji, zobacz [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) w zestawie Windows SDK.  
  
##  <a name="onparaalign"></a>CRichEditView::OnParaAlign  
 Wywołanie tej funkcji, aby zmienić wyrównania akapitu dla zaznaczonych akapitów.  
  
```  
void OnParaAlign(WORD wAlign);
```  
  
### <a name="parameters"></a>Parametry  
 `wAlign`  
 Żądana wyrównania akapitu. Jedna z następujących wartości:  
  
- `PFA_LEFT`Wyrównywanie akapitów lewego marginesu.  
  
- `PFA_RIGHT`Wyrównywanie akapitów prawego marginesu.  
  
- `PFA_CENTER`Center akapitów między marginesów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]  
  
##  <a name="onprinterchanged"></a>CRichEditView::OnPrinterChanged  
 Należy przesłonić tę funkcję, aby zmienić właściwości dla tego widoku bogatej edycji, gdy zmienia się drukarki.  
  
```  
virtual void OnPrinterChanged(const CDC& dcPrinter);
```  
  
### <a name="parameters"></a>Parametry  
 `dcPrinter`  
 A [CDC](../../mfc/reference/cdc-class.md) obiektu do nowej drukarki.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ustawia rozmiar papieru na fizycznych wysokość i szerokość dla urządzenia wyjściowego (drukarki). W przypadku kontekst urządzenia nie są skojarzone z `dcPrinter`, domyślna implementacja ustawia rozmiar papieru 8.5 na 11 cali.  
  
##  <a name="onreplaceall"></a>CRichEditView::OnReplaceAll  
 Wywoływane przez platformę, podczas przetwarzania Zamień wszystkie polecenia w oknie dialogowym Zamień.  
  
```  
virtual void OnReplaceAll(
    LPCTSTR lpszFind,  
    LPCTSTR lpszReplace,  
    BOOL bCase,  
    BOOL bWord);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Tekst do zastąpienia.  
  
 `lpszReplace`  
 Tekst zastępczy.  
  
 `bCase`  
 Wskazuje, czy wyszukiwanie jest uwzględniana wielkość liter.  
  
 `bWord`  
 Wskazuje, czy wyszukiwanie należy wybrać całe wyrazy lub nie.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby zastąpić wszystkie wystąpienia danego tekst z innego ciągu. Należy przesłonić tę funkcję, aby zmienić właściwości wyszukiwania dla tego widoku.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CRichEditView::FindText](#findtext).  
  
##  <a name="onreplacesel"></a>CRichEditView::OnReplaceSel  
 Wywoływane przez platformę, podczas przetwarzania polecenia Zamień w oknie dialogowym Zamień.  
  
```  
virtual void OnReplaceSel(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    BOOL bWord,  
    LPCTSTR lpszReplace);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Tekst do zastąpienia.  
  
 `bNext`  
 Wskazuje kierunek wyszukiwania: **TRUE** jest wyłączony; **FALSE**, nawet.  
  
 `bCase`  
 Wskazuje, czy wyszukiwanie jest uwzględniana wielkość liter.  
  
 `bWord`  
 Wskazuje, czy wyszukiwanie należy wybrać całe wyrazy lub nie.  
  
 `lpszReplace`  
 Tekst zastępczy.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby zastąpić jedno wystąpienie podanego tekst z innego ciągu. Należy przesłonić tę funkcję, aby zmienić właściwości wyszukiwania dla tego widoku.  
  
##  <a name="ontextnotfound"></a>CRichEditView::OnTextNotFound  
 Wywoływane przez platformę, gdy wyszukiwanie nie powiedzie się.  
  
```  
virtual void OnTextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Tekst, który nie został odnaleziony.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję, aby zmienić powiadomienie dane wyjściowe z [MessageBeep](http://msdn.microsoft.com/library/windows/desktop/ms680356).  
  
 Aby uzyskać więcej informacji, zobacz [MessageBeep](http://msdn.microsoft.com/library/windows/desktop/ms680356) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]  
  
##  <a name="onupdatechareffect"></a>CRichEditView::OnUpdateCharEffect  
 Struktura wywołuje tę funkcję, aby zaktualizować polecenia interfejsu użytkownika dla poleceń efekt znak.  
  
```  
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,  
    DWORD dwMask,  
    DWORD dwEffect);
```  
  
### <a name="parameters"></a>Parametry  
 `pCmdUI`  
 Wskaźnik do [CCmdUI](../../mfc/reference/ccmdui-class.md) obiektu.  
  
 `dwMask`  
 Wskazuje znak formatowania maski.  
  
 `dwEffect`  
 Wskazuje znak formatowania efekt.  
  
### <a name="remarks"></a>Uwagi  
 Maska `dwMask` Określa, który znak atrybuty formatowania do sprawdzenia. Flagi `dwEffect` listę atrybutów do zestawu/Wyczyść formatowanie znaków.  
  
 Aby uzyskać więcej informacji na temat `dwMask` i `dwEffect` parametrów i ich potencjalne wartości, zobacz odpowiednie elementy członkowskie danych z [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]  
  
##  <a name="onupdateparaalign"></a>CRichEditView::OnUpdateParaAlign  
 Struktura wywołuje tę funkcję, aby zaktualizować polecenia interfejsu użytkownika dla poleceń efekt akapitu.  
  
```  
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,  
    WORD wAlign);
```  
  
### <a name="parameters"></a>Parametry  
 `pCmdUI`  
 Wskaźnik do [CCmdUI](../../mfc/reference/ccmdui-class.md) obiektu.  
  
 `wAlign`  
 Wyrównanie akapitu do sprawdzenia. Jedna z następujących wartości:  
  
- `PFA_LEFT`Wyrównywanie akapitów lewego marginesu.  
  
- `PFA_RIGHT`Wyrównywanie akapitów prawego marginesu.  
  
- `PFA_CENTER`Center akapitów między marginesów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]  
  
##  <a name="printinsiderect"></a>CRichEditView::PrintInsideRect  
 Wywołanie tej funkcji do formatowania zakres tekstu w formancie edycji wzbogaconej mieścić się w *rectLayout* dla urządzenia określonego przez `pDC`.  
  
```  
long PrintInsideRect(
    CDC* pDC,  
    RECT& rectLayout,  
    long nIndexStart,  
    long nIndexStop,  
    BOOL bOutput);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Wskaźnik do kontekstu urządzenia do obszaru wyjściowego.  
  
 *rectLayout*  
 [RECT](../../mfc/reference/rect-structure1.md) lub [CRect](../../atl-mfc-shared/reference/crect-class.md) definiujący obszaru wyjściowego.  
  
 `nIndexStart`  
 Liczony od zera indeks pierwszego znaku, który zostanie sformatowany.  
  
 `nIndexStop`  
 Liczony od zera indeks ostatni znak do sformatowania.  
  
 *bOutput*  
 Wskazuje, czy tekst ma być renderowany. Jeśli **FALSE**, po prostu jest mierzony tekst.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks ostatni znak, który pasuje do obszaru wyjściowego plus jeden.  
  
### <a name="remarks"></a>Uwagi  
 Zwykle to wywołanie następuje wywołanie [CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) generująca dane wyjściowe.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CRichEditView::GetPaperSize](#getpapersize).  
  
##  <a name="printpage"></a>CRichEditView::PrintPage  
 Wywołanie tej funkcji do formatowania zakres tekstu w formancie edycji wzbogaconej urządzenia wyjściowego określony przez `pDC`.  
  
```  
long PrintPage(
    CDC* pDC,  
    long nIndexStart,  
    long nIndexStop);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Wskaźnik do kontekstu urządzenia dla danych wyjściowych strony.  
  
 `nIndexStart`  
 Liczony od zera indeks pierwszego znaku, który zostanie sformatowany.  
  
 `nIndexStop`  
 Liczony od zera indeks ostatni znak do sformatowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks ostatni znak, który mieści się na stronie plus jeden.  
  
### <a name="remarks"></a>Uwagi  
 Układ każdej strony jest kontrolowany przez [GetPageRect](#getpagerect) i [GetPrintRect](#getprintrect). Zwykle to wywołanie następuje wywołanie [CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) generująca dane wyjściowe.  
  
 Należy pamiętać, że marginesy są względem strony fizycznej strony logicznej. W związku z tym marginesy zero będzie często Przytnij tekstu, ponieważ wiele drukarek ma obszarów nie do drukowania na stronie. Aby uniknąć przycinanie tekstu, należy wywołać [SetMargins](#setmargins) i Ustaw marginesy uzasadnione przed wydrukowaniem.  
  
##  <a name="queryacceptdata"></a>CRichEditView::QueryAcceptData  
 Wywoływane przez platformę, by wkleić obiekt w zaawansowanej edycji.  
  
```  
virtual HRESULT QueryAcceptData(
    LPDATAOBJECT lpdataobj,  
    CLIPFORMAT* lpcfFormat,  
    DWORD dwReco,  
    BOOL bReally,  
    HGLOBAL hMetaFile);
```  
  
### <a name="parameters"></a>Parametry  
 *lpdataobj*  
 Wskaźnik do [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) do zapytania.  
  
 *lpcfFormat*  
 Wskaźnik do formatu danych.  
  
 `dwReco`  
 Nie używany.  
  
 *bReally*  
 Wskazuje, czy operacja wklejania powinno być kontynuowane, czy nie.  
  
 `hMetaFile`  
 Dojście do metaplik używany do rysowania ikony elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `HRESULT` Wartość raportowania powodzenie operacji.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji do obsługi różnych organizacji elementów modelu COM w klasie pochodnej dokumentu. Jest to zaawansowane możliwym do zastąpienia.  
  
 Aby uzyskać więcej informacji na temat `HRESULT` i `IDataObject`, zobacz [struktury COM kody błędów](http://msdn.microsoft.com/library/windows/desktop/ms690088) i [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)odpowiednio w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]  
  
##  <a name="setcharformat"></a>CRichEditView::SetCharFormat  
 Wywołanie tej funkcji, aby ustawić atrybuty dla nowego tekstu, w tym formatowanie znaków `CRichEditView` obiektu.  
  
```  
void SetCharFormat(CHARFORMAT2 cf);
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) struktury zawierającej znakiem domyślne atrybuty formatowania.  
  
### <a name="remarks"></a>Uwagi  
 Tylko atrybuty, które zostały określone przez **dwMask** członkiem `cf` są zmieniane przez tę funkcję.  
  
 Aby uzyskać więcej informacji, zobacz [EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230) wiadomości i [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) struktury w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]  
  
##  <a name="setmargins"></a>CRichEditView::SetMargins  
 Wywołanie tej funkcji, aby ustawić drukowania marginesy dla tego widoku bogatej edycji.  
  
```  
void SetMargins(const CRect& rectMargin);
```  
  
### <a name="parameters"></a>Parametry  
 *rectMargin*  
 Nowe wartości margines do drukowania, mierzony w `MM_TWIPS`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli [m_nWordWrap](#m_nwordwrap) jest `WrapToTargetDevice`, należy wywołać [WrapChanged](#wrapchanged) po użyciu tej funkcji, aby dostosować ustawienia drukowania.  
  
 Należy pamiętać, że marginesy używane przez [PrintPage](#printpage) są względem strony fizycznej strony logicznej. W związku z tym marginesy zero będzie często Przytnij tekstu, ponieważ wiele drukarek ma obszarów nie do drukowania na stronie. Aby uniknąć przycinanie tekstu, należy wywołać użyj `SetMargins` można ustawić marginesy uzasadnione drukarki przed wydrukowaniem.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CRichEditView::GetPaperSize](#getpapersize).  
  
##  <a name="setpapersize"></a>CRichEditView::SetPaperSize  
 Wywołanie tej funkcji, aby ustawić rozmiar papieru do drukowania tego widoku bogatej edycji.  
  
```  
void SetPaperSize(CSize sizePaper);
```  
  
### <a name="parameters"></a>Parametry  
 *sizePaper*  
 Nowe wartości rozmiaru papieru do drukowania, mierzony w `MM_TWIPS`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli [m_nWordWrap](#m_nwordwrap) jest `WrapToTargetDevice`, należy wywołać [WrapChanged](#wrapchanged) po użyciu tej funkcji, aby dostosować ustawienia drukowania.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]  
  
##  <a name="setparaformat"></a>CRichEditView::SetParaFormat  
 Wywołanie tej funkcji, aby ustawić atrybuty dla bieżącego zaznaczenia w tym formatowania akapitu `CRichEditView` obiektu.  
  
```  
BOOL SetParaFormat(PARAFORMAT2& pf);
```  
  
### <a name="parameters"></a>Parametry  
 `pf`  
 [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) atrybuty formatowania akapitu struktury zawierającej nowym domyślnym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Tylko atrybuty, które zostały określone przez **dwMask** członkiem `pf` są zmieniane przez tę funkcję.  
  
 Aby uzyskać więcej informacji, zobacz [EM_SETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774276) wiadomości i [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) struktury w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]  
  
##  <a name="textnotfound"></a>CRichEditView::TextNotFound  
 Wywołanie tej funkcji do zresetowania stanu wewnętrznego wyszukiwania [cricheditview —](../../mfc/reference/cricheditview-class.md) kontroli po błędnego wywołania [ciąg FindText](#findtext).  
  
```  
void TextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Zawiera ciąg tekstowy, który nie został znaleziony.  
  
### <a name="remarks"></a>Uwagi  
 Zaleca się, że tę metodę można wywołać bezpośrednio po nieudanych wywołań [ciąg FindText](#findtext) tak, aby prawidłowo zresetowania stanu wewnętrznego wyszukiwania formantu.  
  
 `lpszFind` Parametr powinien zawierać tej samej zawartości jako ciągu do [ciąg FindText](#findtext). Po przywróceniu stanu wewnętrznego wyszukiwania, ta metoda wywoła [OnTextNotFound](#ontextnotfound) metody za pomocą podanego ciągu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CRichEditView::FindText](#findtext).  
  
##  <a name="wrapchanged"></a>CRichEditView::WrapChanged  
 Wywołanie tej funkcji, gdy zmieniono ustawienia drukowania ( [SetMargins](#setmargins) lub [SetPaperSize](#setpapersize)).  
  
```  
virtual void WrapChanged();
```  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji, aby zmodyfikować sposób zaawansowanej edycji widoku odpowiada na zmiany w [m_nWordWrap](#m_nwordwrap) lub ustawienia drukowania ( [OnPrinterChanged](#onprinterchanged)).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC WORDPAD](../../visual-cpp-samples.md)   
 [Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cricheditdoc — klasa](../../mfc/reference/cricheditdoc-class.md)   
 [Klasa CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)
