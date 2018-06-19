---
title: Klasa CMFCPropertySheet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPage
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPageToTree
- AFXPROPERTYSHEET/CMFCPropertySheet::AddTreeCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::EnablePageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::GetHeaderHeight
- AFXPROPERTYSHEET/CMFCPropertySheet::GetLook
- AFXPROPERTYSHEET/CMFCPropertySheet::GetNavBarWidth
- AFXPROPERTYSHEET/CMFCPropertySheet::GetTab
- AFXPROPERTYSHEET/CMFCPropertySheet::InitNavigationControl
- AFXPROPERTYSHEET/CMFCPropertySheet::OnActivatePage
- AFXPROPERTYSHEET/CMFCPropertySheet::OnDrawPageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::OnRemoveTreePage
- AFXPROPERTYSHEET/CMFCPropertySheet::RemoveCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::RemovePage
- AFXPROPERTYSHEET/CMFCPropertySheet::SetIconsList
- AFXPROPERTYSHEET/CMFCPropertySheet::SetLook
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertySheet [MFC], CMFCPropertySheet
- CMFCPropertySheet [MFC], AddPage
- CMFCPropertySheet [MFC], AddPageToTree
- CMFCPropertySheet [MFC], AddTreeCategory
- CMFCPropertySheet [MFC], EnablePageHeader
- CMFCPropertySheet [MFC], GetHeaderHeight
- CMFCPropertySheet [MFC], GetLook
- CMFCPropertySheet [MFC], GetNavBarWidth
- CMFCPropertySheet [MFC], GetTab
- CMFCPropertySheet [MFC], InitNavigationControl
- CMFCPropertySheet [MFC], OnActivatePage
- CMFCPropertySheet [MFC], OnDrawPageHeader
- CMFCPropertySheet [MFC], OnRemoveTreePage
- CMFCPropertySheet [MFC], RemoveCategory
- CMFCPropertySheet [MFC], RemovePage
- CMFCPropertySheet [MFC], SetIconsList
- CMFCPropertySheet [MFC], SetLook
ms.assetid: 01d93573-9698-440f-a6a4-5bebbee879dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b61adc98f6b6e84f5e2ef10f88ae41720e2fbf9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372723"
---
# <a name="cmfcpropertysheet-class"></a>Klasa CMFCPropertySheet
`CMFCPropertySheet` Klasa obsługuje arkusza właściwości, w którym każdej strony właściwości jest wskazywane przez kartę strony, przycisku paska narzędzi, węzeł kontrolny drzewa lub element listy.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCPropertySheet : public CPropertySheet  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCPropertySheet::CMFCPropertySheet](#cmfcpropertysheet)|Konstruuje `CMFCPropertySheet` obiektu.|  
|`CMFCPropertySheet::~CMFCPropertySheet`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCPropertySheet::AddPage](#addpage)|Dodaje strony do arkusza właściwości.|  
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|Dodaje nową stronę właściwości z kontrolką drzewa.|  
|[CMFCPropertySheet::AddTreeCategory](#addtreecategory)|Dodaje nowy węzeł do formantu drzewa.|  
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|Rezerwuje miejsce na początku każdej stronie, aby narysować niestandardowego nagłówka.|  
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|Pobiera wysokość bieżącego nagłówka.|  
|[CMFCPropertySheet::GetLook](#getlook)|Pobiera wartość wyliczenia, który określa wygląd bieżącego arkusza właściwości.|  
|[CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|Ponowne próby szerokości paska nawigacji w pikselach.|  
|[CMFCPropertySheet::GetTab](#gettab)|Pobiera obiekt formantu kartę wewnętrzny, który obsługuje bieżącego formantu arkusza właściwości.|  
|`CMFCPropertySheet::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|Inicjuje wyglądu bieżącego formantu arkusza właściwości.|  
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|Wywoływane przez platformę, gdy jest włączona strony właściwości.|  
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|Wywoływane przez platformę, by narysować nagłówek strony właściwości niestandardowej.|  
|`CMFCPropertySheet::OnInitDialog`|Obsługuje [WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) wiadomości. (Przesłania [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|  
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|Wywoływane przez platformę, by usunąć stronę właściwości z kontrolką drzewa.|  
|`CMFCPropertySheet::PreTranslateMessage`|Wykonuje translację komunikaty okna przed wysłaniem do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) i [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkcje systemu Windows. (Przesłania `CPropertySheet::PreTranslateMessage`.)|  
|[CMFCPropertySheet::RemoveCategory](#removecategory)|Usunięcie węzła z drzewa.|  
|[CMFCPropertySheet::RemovePage](#removepage)|Usuwa stronę właściwości arkusza właściwości.|  
|[CMFCPropertySheet::SetIconsList](#seticonslist)|Określa listę obrazów, które są używane w formancie nawigacji w okienku programu Outlook.|  
|[CMFCPropertySheet::SetLook](#setlook)|Określa wygląd arkusza właściwości.|  
  
## <a name="remarks"></a>Uwagi  
 `CMFCPropertySheet` Klasa reprezentuje arkuszy właściwości, znanej także jako okna dialogowe kart. `CMFCPropertySheet` Klasy można wyświetlić strony właściwości w różny sposób.  
  
 Wykonaj poniższe kroki, aby użyć `CMFCPropertySheet` klasy w aplikacji:  
  
1.  Klasa wyprowadzona z `CMFCPropertySheet` klasy i nazwę klasy, na przykład CMyPropertySheet.  
  
2.  Utworzyć [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md) obiektu dla każdej strony właściwości.  
  
3.  Wywołanie [CMFCPropertySheet::SetLook](#setlook) metody w Konstruktorze CMyPropertySheet. Parametr metody Określa, że strony właściwości są wyświetlane jako karty wzdłuż górnej lub lewej krawędzi arkusza właściwości; karty w stylu programu Microsoft OneNote arkusza właściwości; przycisków w formancie paska narzędzi Microsoft Outlook; węzły w drzewie; lub jako listę elementów po lewej stronie arkusza właściwości.  
  
4.  W przypadku utworzenia arkusza właściwości stylu narzędzi Microsoft Outlook, wywołaj [CMFCPropertySheet::SetIconsList](#seticonslist) do kojarzenia listy obrazów oraz na stronach właściwości.  
  
5.  Wywołanie [CMFCPropertySheet::AddPage](#addpage) metody dla każdej strony właściwości.  
  
6.  Utwórz `CMFCPropertySheet` kontroli i Wywołaj jej `DoModal` metody.  
  
## <a name="illustrations"></a>Ilustracje  
 Na poniższej ilustracji przedstawiono arkusz właściwości w stylu osadzonych narzędzi Microsoft Outlook. Pasek narzędzi programu Outlook pojawia się po lewej stronie arkusza właściwości.  
  
 ![Formanty kolor CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_color.png "cmfcpropertysheet_color")  
  
 Na poniższej ilustracji przedstawiono arkusz właściwości, która zawiera [klasy CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) obiektu. Dany obiekt jest w stylu standardowe arkusza właściwości formantów wspólnych arkusza właściwości.  
  
 ![Formanty listy, a właściwość CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_list.png "cmfcpropertysheet_list")  
  
 Na poniższej ilustracji przedstawiono arkusz właściwości, który znajduje się w stylu formantu drzewa.  
  
 ![Drzewo](../../mfc/reference/media/proptree.png "proptree")  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpropertysheet.h  
  
##  <a name="addpage"></a>  CMFCPropertySheet::AddPage  
 Dodaje strony do arkusza właściwości.  
  
```  
void AddPage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pPage`  
 Wskaźnik do obiektu strony. Ten parametr nie może być `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda dodaje strony określonej właściwości ostania zakładka w arkuszu właściwości. W związku z tym ta metoda umożliwia dodawanie stron w kolejności od lewej do prawej.  
  
 Jeśli arkusz właściwości jest w stylu programu Microsoft Outlook, platformę Wyświetla listę przycisków nawigacji po lewej stronie arkusza właściwości. Po tej metody dodaje strony właściwości, dodaje odpowiedni przycisk do listy. Aby wyświetlić stronę właściwości, kliknij jego odpowiedni przycisk. Aby uzyskać więcej informacji na temat style arkuszy właściwości, zobacz [CMFCPropertySheet::SetLook](#setlook).  
  
##  <a name="addpagetotree"></a>  CMFCPropertySheet::AddPageToTree  
 Dodaje nową stronę właściwości z kontrolką drzewa.  
  
```  
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,  
    CMFCPropertyPage* pPage,  
    int nIconNum=-1,  
    int nSelIconNum=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pCategory`  
 Wskaźnik do węzła drzewa nadrzędnego, lub `NULL` do skojarzenia z tym węzłem najwyższego poziomu określonej strony. Wywołanie [CMFCPropertySheet::AddTreeCategory](#addtreecategory) metodę, aby uzyskać ten wskaźnik.  
  
 [in] `pPage`  
 Wskaźnik do obiektu strony właściwości.  
  
 [in] `nIconNum`  
 Liczony od zera indeks ikony lub -1, jeśli jest używana bez ikony. Ikona jest wyświetlana obok strony właściwości formantu drzewa, gdy strona nie jest zaznaczona. Wartość domyślna wynosi -1.  
  
 [in] `nSelIconNum`  
 Liczony od zera indeks ikony lub -1, jeśli jest używana bez ikony. Ikona jest wyświetlana obok strony właściwości formantu drzewa, po wybraniu strony. Wartość domyślna wynosi -1.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda dodaje strony właściwości liścia formantu drzewa. Aby dodać strony właściwości, należy utworzyć `CMFCPropertySheet` obiekt, należy wywołać [CMFCPropertySheet::SetLook](#setlook) metody z `look` ustawiona `CMFCPropertySheet::PropSheetLook_Tree`, a następnie użyć tej metody można dodać strony właściwości.  
  
##  <a name="addtreecategory"></a>  CMFCPropertySheet::AddTreeCategory  
 Dodaje nowy węzeł do formantu drzewa.  
  
```  
CMFCPropertySheetCategoryInfo* AddTreeCategory(
    LPCTSTR lpszLabel,  
    int nIconNum=-1,  
    int nSelectedIconNum=-1,  
    const CMFCPropertySheetCategoryInfo* pParentCategory=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszLabel`  
 Nazwa węzła.  
  
 [in] `nIconNum`  
 Liczony od zera indeks ikony lub -1, jeśli jest używana bez ikony. Ikona jest wyświetlana obok strony właściwości formantu drzewa, gdy strona nie jest zaznaczona. Wartość domyślna wynosi -1.  
  
 [in] `nSelectedIconNum`  
 Liczony od zera indeks ikony lub -1, jeśli jest używana bez ikony. Ikona jest wyświetlana obok strony właściwości formantu drzewa, po wybraniu strony. Wartość domyślna wynosi -1.  
  
 [in] `pParentCategory`  
 Wskaźnik do węzła drzewa nadrzędnego, lub `NULL` do skojarzenia z tym węzłem najwyższego poziomu określonej strony. Ustaw ten parametr z [CMFCPropertySheet::AddTreeCategory](#addtreecategory) metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowego węzła w drzewie.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby dodać nowy węzeł, który jest również nazywany kategorii, z formantem drzewa. Aby dodać węzeł, Utwórz `CMFCPropertySheet` obiekt, należy wywołać [CMFCPropertySheet::SetLook](#setlook) metody z `look` parametru `CMFCPropertySheet::PropSheetLook_Tree`, a następnie użyć tej metody, aby dodać węzeł.  
  
 Użyj wartości zwracanej tej metody w kolejnych wywołaniach [CMFCPropertySheet::AddPageToTree](#addpagetotree) i [CMFCPropertySheet::AddTreeCategory](#addtreecategory).  
  
##  <a name="cmfcpropertysheet"></a>  CMFCPropertySheet::CMFCPropertySheet  
 Konstruuje `CMFCPropertySheet` obiektu.  
  
```  
CMFCPropertySheet(
    UINT nIDCaption,  
    CWnd* pParentWnd=NULL,  
    UINT iSelectPage=0);

CMFCPropertySheet(
    LPCTSTR pszCaption,  
    CWnd* pParentWnd=NULL,  
    UINT iSelectPage=0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pszCaption`  
 Ciąg, który zawiera podpis arkusza właściwości. Nie może być `NULL`.  
  
 [in] `nIDCaption`  
 Identyfikator zasobu, który zawiera podpis arkusza właściwości.  
  
 [in] `pParentWnd`  
 Wskaźnik do nadrzędnego okna arkusza właściwości lub `NULL` Jeśli okno nadrzędne głównego okna aplikacji. Wartość domyślna to `NULL`.  
  
 [in] `iSelectPage`  
 Liczony od zera indeks strony właściwość top. Wartość domyślna to 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz parametry [CPropertySheet::CPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet) konstruktora.  
  
##  <a name="enablepageheader"></a>  CMFCPropertySheet::EnablePageHeader  
 Rezerwuje miejsce na początku każdej stronie, aby narysować niestandardowego nagłówka.  
  
```  
void EnablePageHeader(int nHeaderHeight);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nHeaderHeight`  
 Wysokość nagłówka, w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Aby użyć wartości `nHeaderHeight` zastąpienie parametru do rysowania niestandardowy nagłówek [CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader) metody.  
  
##  <a name="getheaderheight"></a>  CMFCPropertySheet::GetHeaderHeight  
 Pobiera wysokość bieżącego nagłówka.  
  
```  
int GetHeaderHeight() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wysokość nagłówka, w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie [CMFCPropertySheet::EnablePageHeader](#enablepageheader) metoda przed wywołaniem tej metody.  
  
##  <a name="getlook"></a>  CMFCPropertySheet::GetLook  
 Pobiera wartość wyliczenia, który określa wygląd bieżącego arkusza właściwości.  
  
```  
PropSheetLook GetLook() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jedna z wartości wyliczenia, które określa wygląd arkusza właściwości. Aby uzyskać listę możliwych wartości, zobacz tabelę wyliczenia w sekcji uwag [CMFCPropertySheet::SetLook](#setlook).  
  
##  <a name="getnavbarwidth"></a>  CMFCPropertySheet::GetNavBarWidth  
 Pobiera szerokość paska nawigacyjnego.  
  
```  
int GetNavBarWidth() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość paska nawigacyjnego w pikselach.  
  
##  <a name="gettab"></a>  CMFCPropertySheet::GetTab  
 Pobiera obiekt formantu kartę wewnętrzny, który obsługuje bieżącego formantu arkusza właściwości.  
  
```  
CMFCTabCtrl& GetTab() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wewnętrzna karta obiektu formantu.  
  
### <a name="remarks"></a>Uwagi  
 Arkusz właściwości można ustawić, aby był on wyświetlany w różnych stylach, takich jak Kontrola drzewa, listę przycisków nawigacji lub zestaw stron z kartami.  
  
 Przed wywołaniem tej metody należy wywołać [CMFCPropertySheet::SetLook](#setlook) metodę, aby określić wygląd formantu arkusza właściwości. Następnie wywołaj [CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol) metody do inicjalizacji obiektu kontroli wewnętrznej karty. Użyj tej metody, aby pobrać obiekt formantu karty i użyć obiektu do pracy z kartami na arkuszu właściwości.  
  
 Ta metoda potwierdza w trybie debugowania, jeśli nie ustawiono właściwości formantu arkusza pojawią się w stylu programu Microsoft OneNote.  
  
##  <a name="initnavigationcontrol"></a>  CMFCPropertySheet::InitNavigationControl  
 Inicjuje wyglądu bieżącego formantu arkusza właściwości.  
  
```  
virtual CWnd* InitNavigationControl();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do okna formantu arkusza właściwości.  
  
### <a name="remarks"></a>Uwagi  
 Formant arkusza właściwości może się pojawić na różne sposoby, takie jak zestaw karty, formantu drzewa lub listę przycisków nawigacji. Użyj [CMFCPropertySheet::SetLook](#setlook) metodę, aby określić wygląd formantu arkusza właściwości.  
  
##  <a name="onactivatepage"></a>  CMFCPropertySheet::OnActivatePage  
 Wywoływane przez platformę, gdy jest włączona strony właściwości.  
  
```  
virtual void OnActivatePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pPage`  
 Wskaźnik do obiektu strony właściwości, reprezentujący stronę właściwości włączone.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda gwarantuje, że strona dla właściwości włączone jest wyświetlony w wyniku przewijania. Styl bieżący arkusz właściwości zawiera okienku programu Microsoft Outlook, ta metoda ustawia odpowiedni przycisk Outlook stan zaznaczenia.  
  
##  <a name="ondrawpageheader"></a>  CMFCPropertySheet::OnDrawPageHeader  
 Wywoływane przez platformę, by narysować nagłówka strony właściwości niestandardowej.  
  
```  
virtual void OnDrawPageHeader(
    CDC* pDC,  
    int nPage,  
    CRect rectHeader);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] `nPage`  
 Numer strony właściwości liczony od zera.  
  
 [in] `rectHeader`  
 Prostokąt ograniczający Określa, gdzie ma zostać narysowany nagłówka.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda nie działa. Jeśli przesłonięcia tej metody należy wywołać [CMFCPropertySheet::EnablePageHeader](#enablepageheader) metoda przed struktura wywołuje tę metodę.  
  
##  <a name="onremovetreepage"></a>  CMFCPropertySheet::OnRemoveTreePage  
 Wywoływane przez platformę, by usunąć stronę właściwości z kontrolką drzewa.  
  
```  
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pPage`  
 Wskaźnik do obiektu strony właściwości, reprezentujący stronę właściwości do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`.  
  
##  <a name="removecategory"></a>  CMFCPropertySheet::RemoveCategory  
 Usunięcie węzła z drzewa.  
  
```  
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pCategory`  
 Wskaźnik do kategorii (węzeł) do usunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby usunąć węzeł, który jest również nazywany kategorii z formantem drzewa. Użyj [CMFCPropertySheet::AddTreeCategory](#addtreecategory) metodę, aby dodać węzeł do formantu drzewa.  
  
##  <a name="removepage"></a>  CMFCPropertySheet::RemovePage  
 Usuwa stronę właściwości arkusza właściwości.  
  
```  
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pPage`  
 Wskaźnik do obiektu strony właściwości reprezentujący stronę właściwości do usunięcia. Nie może być `NULL`.  
  
 [in] `nPage`  
 Liczony od zera indeks strony do usunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda usuwa stronę określonej właściwości i niszczy okno skojarzone. Strona właściwości obiektu, który `pPage` określa parametr nie zostanie zniszczony do [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) zamknięcia okna.  
  
##  <a name="seticonslist"></a>  CMFCPropertySheet::SetIconsList  
 Określa listę obrazów, które są używane w formancie nawigacji w okienku programu Outlook.  
  
```  
BOOL SetIconsList(
    UINT uiImageListResID,  
    int cx,  
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `uiImageListResID`  
 Identyfikator zasobu z listy obrazów.  
  
 [in] `cx`  
 Szerokość w pikselach, ikony na liście obrazów.  
  
 [in] `clrTransparent`  
 Kolor przezroczysty obraz. Części obrazu, które to kolor ma być przezroczysty. Wartość domyślna to amarantowy kolorów, RGB(255,0,255).  
  
 [in] `hIcons`  
 Dojście do istniejącej listy obrazów.  
  
### <a name="return-value"></a>Wartość zwracana  
 W pierwszym metoda przeciążenia składni `TRUE` Jeśli ta metoda jest pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli arkusz właściwości jest w stylu programu Microsoft Outlook, platformę Wyświetla listę przycisków nawigacji, nazywany formant okienka programu Outlook, po lewej stronie arkusza właściwości. Użyj tej metody, aby ustawić listy obrazów, który będzie używany przez formant okienka programu Outlook.  
  
 Aby uzyskać więcej informacji na temat metody, które obsługują tę metodę, zobacz [CImageList::Create](../../mfc/reference/cimagelist-class.md#create) i [CImageList::Add](../../mfc/reference/cimagelist-class.md#add). Aby uzyskać więcej informacji na temat ustawiania styl arkusz właściwości, zobacz [CMFCPropertySheet::SetLook](#setlook).  
  
##  <a name="setlook"></a>  CMFCPropertySheet::SetLook  
 Określa wygląd arkusza właściwości.  
  
```  
void SetLook(
    PropSheetLook look,  
    int nNavControlWidth=100);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `look`  
 Jedna z wartości wyliczenia, które określa wygląd arkusza właściwości. Styl domyślny arkusz właściwości jest `CMFCPropertySheet::PropSheetLook_Tabs`. Aby uzyskać więcej informacji zobacz tabelę w sekcji uwag w tym temacie.  
  
 [in] `nNavControlWidth`  
 Szerokość formantu nawigacji w pikselach. Wartość domyślna to 100.  
  
### <a name="remarks"></a>Uwagi  
 Aby wyświetlić arkusz właściwości stylu innej niż domyślna, tę metodę należy wywołać przed utworzeniem okna arkusza właściwości.  
  
 W poniższej tabeli wymieniono wartości wyliczenia, które można określić w `look` parametru.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`CMFCPropertySheet::PropSheetLook_Tabs`|(Ustawienie domyślne) Wyświetla kartę dla każdej strony właściwości. Karty są wyświetlane w górnej części arkusza właściwości i są ułożone, jeśli istnieje więcej kart niż mieści się w jednym wierszu.|  
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|Wyświetla listę przycisków nawigacji w stylu paska Microsoft Outlook, po lewej stronie arkusza właściwości. Każdy przycisk na liście odnosi się do strony właściwości. Platformę Wyświetla strzałki przewijania, jeśli istnieje więcej przycisków nie mieści się w widocznym obszarze listy.|  
|`CMFCPropertySheet::PropSheetLook_Tree`|Wyświetla formant drzewa po lewej stronie arkusza właściwości. Na każdym węźle nadrzędnym lub podrzędnym drzewa odnosi się do strony właściwości. Platformę Wyświetla strzałki przewijania, jeśli istnieje więcej węzłów niż mieści się w widocznym obszarze drzewa.|  
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|Wyświetla kartę w stylu programu Microsoft OneNote dla każdej strony właściwości. Platformę Wyświetla karty u góry arkusz właściwości i strzałki przewijania, jeśli istnieje więcej kart niż mieści się w jednym wierszu.|  
|`CMFCPropertySheet::PropSheetLook_List`|Wyświetla listę po lewej stronie arkusza właściwości. Każdy element tej listy odnosi się do strony właściwości. Platformę Wyświetla strzałki przewijania, jeśli istnieje więcej elementów lista niż mieści się w widocznym obszarze listy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)   
 [Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)
