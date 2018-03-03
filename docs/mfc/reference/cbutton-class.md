---
title: Klasa CButton | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CButton
- AFXWIN/CButton
- AFXWIN/CButton::CButton
- AFXWIN/CButton::Create
- AFXWIN/CButton::DrawItem
- AFXWIN/CButton::GetBitmap
- AFXWIN/CButton::GetButtonStyle
- AFXWIN/CButton::GetCheck
- AFXWIN/CButton::GetCursor
- AFXWIN/CButton::GetIcon
- AFXWIN/CButton::GetIdealSize
- AFXWIN/CButton::GetImageList
- AFXWIN/CButton::GetNote
- AFXWIN/CButton::GetNoteLength
- AFXWIN/CButton::GetSplitGlyph
- AFXWIN/CButton::GetSplitImageList
- AFXWIN/CButton::GetSplitInfo
- AFXWIN/CButton::GetSplitSize
- AFXWIN/CButton::GetSplitStyle
- AFXWIN/CButton::GetState
- AFXWIN/CButton::GetTextMargin
- AFXWIN/CButton::SetBitmap
- AFXWIN/CButton::SetButtonStyle
- AFXWIN/CButton::SetCheck
- AFXWIN/CButton::SetCursor
- AFXWIN/CButton::SetDropDownState
- AFXWIN/CButton::SetIcon
- AFXWIN/CButton::SetImageList
- AFXWIN/CButton::SetNote
- AFXWIN/CButton::SetSplitGlyph
- AFXWIN/CButton::SetSplitImageList
- AFXWIN/CButton::SetSplitInfo
- AFXWIN/CButton::SetSplitSize
- AFXWIN/CButton::SetSplitStyle
- AFXWIN/CButton::SetState
- AFXWIN/CButton::SetTextMargin
dev_langs:
- C++
helpviewer_keywords:
- CButton [MFC], CButton
- CButton [MFC], Create
- CButton [MFC], DrawItem
- CButton [MFC], GetBitmap
- CButton [MFC], GetButtonStyle
- CButton [MFC], GetCheck
- CButton [MFC], GetCursor
- CButton [MFC], GetIcon
- CButton [MFC], GetIdealSize
- CButton [MFC], GetImageList
- CButton [MFC], GetNote
- CButton [MFC], GetNoteLength
- CButton [MFC], GetSplitGlyph
- CButton [MFC], GetSplitImageList
- CButton [MFC], GetSplitInfo
- CButton [MFC], GetSplitSize
- CButton [MFC], GetSplitStyle
- CButton [MFC], GetState
- CButton [MFC], GetTextMargin
- CButton [MFC], SetBitmap
- CButton [MFC], SetButtonStyle
- CButton [MFC], SetCheck
- CButton [MFC], SetCursor
- CButton [MFC], SetDropDownState
- CButton [MFC], SetIcon
- CButton [MFC], SetImageList
- CButton [MFC], SetNote
- CButton [MFC], SetSplitGlyph
- CButton [MFC], SetSplitImageList
- CButton [MFC], SetSplitInfo
- CButton [MFC], SetSplitSize
- CButton [MFC], SetSplitStyle
- CButton [MFC], SetState
- CButton [MFC], SetTextMargin
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e6e92efe5b5a99042426dd2e6a7594f2de46f2ce
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="cbutton-class"></a>Klasa CButton
Udostępnia funkcje kontroli przycisku systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CButton : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CButton::CButton](#cbutton)|Konstruuje `CButton` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CButton::Create](#create)|Tworzy kontrolkę przycisku systemu Windows i dołącza go do `CButton` obiektu.|  
|[CButton::DrawItem](#drawitem)|Należy przesłonić, aby narysować rysowanych przez właściciela `CButton` obiektu.|  
|[CButton::GetBitmap](#getbitmap)|Pobiera dojście mapy bitowej wcześniej ustawione z [SetBitmap](#setbitmap).|  
|[CButton::GetButtonStyle](#getbuttonstyle)|Pobiera informacje o stylu formantu przycisku.|  
|[CButton::GetCheck](#getcheck)|Pobiera stan wyboru formantu przycisku.|  
|[CButton::GetCursor](#getcursor)|Pobiera dojście obrazu kursora wcześniej ustawione z [SetCursor](#setcursor).|  
|[CButton::GetIcon](#geticon)|Pobiera dojście wcześniej zestawu z ikon [SetIcon](#seticon).|  
|[CButton::GetIdealSize](#getidealsize)|Pobiera rozmiar idealny formantu przycisku.|  
|[CButton::GetImageList](#getimagelist)|Pobiera listy obrazów formantu przycisku.|  
|[CButton::GetNote](#getnote)|Pobiera składnik Uwaga bieżącego polecenia kontrolki łącza.|  
|[CButton::GetNoteLength](#getnotelength)|Pobiera długość tekstu Uwaga dla kontrolki linku bieżącego polecenia.|  
|[CButton::GetSplitGlyph](#getsplitglyph)|Pobiera skojarzone z bieżącym formantu przycisku podziału w obrębie symboli.|  
|[CButton::GetSplitImageList](#getsplitimagelist)|Pobiera listę obraz dla bieżącego formantu przycisku podziału.|  
|[CButton::GetSplitInfo](#getsplitinfo)|Pobiera informacje, które definiują bieżącego formantu przycisku podziału.|  
|[CButton::GetSplitSize](#getsplitsize)|Pobiera prostokąt ograniczający składnika listy rozwijanej bieżącego formantu przycisku podziału.|  
|[CButton::GetSplitStyle](#getsplitstyle)|Pobiera style przycisku podziału definiujące bieżącego formantu przycisku podziału.|  
|[CButton::GetState](#getstate)|Pobiera stan zaznaczenia, wyróżnij stan i stan aktywny kontrolki przycisku.|  
|[CButton::GetTextMargin](#gettextmargin)|Pobiera margines tekst formantu przycisku.|  
|[CButton::SetBitmap](#setbitmap)|Określa, który będzie wyświetlany na przycisku mapy bitowej.|  
|[CButton::SetButtonStyle](#setbuttonstyle)|Zmienia styl przycisku.|  
|[CButton::SetCheck](#setcheck)|Ustawia stan wyboru formantu przycisku.|  
|[CButton::SetCursor](#setcursor)|Określa obraz kursor, który będzie wyświetlany na przycisku.|  
|[CButton::SetDropDownState](#setdropdownstate)|Ustawia stan listy rozwijanej bieżącego formantu przycisku podziału.|  
|[CButton::SetIcon](#seticon)|Określa ikonę, który będzie wyświetlany na przycisku.|  
|[CButton::SetImageList](#setimagelist)|Ustawia listy obrazów formantu przycisku.|  
|[CButton::SetNote](#setnote)|Ustawia uwagi na bieżący Kontrola łącza polecenia.|  
|[CButton::SetSplitGlyph](#setsplitglyph)|Kojarzy określonego symbolu z bieżącego formantu przycisku podziału.|  
|[CButton::SetSplitImageList](#setsplitimagelist)|Kojarzy listy obrazów z bieżącego formantu przycisku podziału.|  
|[CButton::SetSplitInfo](#setsplitinfo)|Określa informacje, które definiują bieżącego formantu przycisku podziału.|  
|[CButton::SetSplitSize](#setsplitsize)|Ustawia prostokąt ograniczający składnika listy rozwijanej bieżącego formantu przycisku podziału.|  
|[CButton::SetSplitStyle](#setsplitstyle)|Ustawia styl bieżącego formantu przycisku podziału.|  
|[CButton::SetState](#setstate)|Ustawia stan wyróżnienia kontrolki przycisku.|  
|[CButton::SetTextMargin](#settextmargin)|Ustawia margines tekst formantu przycisku.|  
  
## <a name="remarks"></a>Uwagi  
 Kontrolka przycisku jest okno podrzędne małych, prostokątne, które można klikać włączać i wyłączać. Przyciski można użyć pojedynczo lub w grupach i albo mogą zostać oznaczone etykietami lub występują bez tekstu. Przycisk zwykle zmienia wygląd po kliknięciu przez użytkownika.  
  
 Przyciski typowe są pola wyboru, przycisku radiowego i przycisku polecenia. A `CButton` obiektu może być dowolną z tych opcji, zgodnie z [styl przycisku](../../mfc/reference/styles-used-by-mfc.md#button-styles) określony podczas jego inicjowania przez [Utwórz](#create) funkcję elementu członkowskiego.  
  
 Ponadto [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) klasą pochodną `CButton` obsługuje tworzenie kontrolki przycisku etykietą obrazy mapę bitową zamiast tekstu. A `CBitmapButton` może mieć osobne mapy bitowe dla przycisku na, w dół fokus i wyłączone stanów.  
  
 Kontrolka przycisku można utworzyć szablonu okna dialogowego lub bezpośrednio w kodzie. W obu przypadkach należy najpierw wywołać konstruktora `CButton` do skonstruowania `CButton` obiektu; wywoływać **Utwórz** funkcji członkowskiej, aby utworzyć systemu Windows przycisk sterowania i dołącz je do `CButton` obiektu.  
  
 Konstrukcja może być jednoetapowy proces w klasie pochodnej z `CButton`. Zapisywanie konstruktora klasy pochodnej i wywołanie **Utwórz** z wewnątrz konstruktora.  
  
 Jeśli chcesz obsługiwać komunikaty powiadomień systemu Windows, wysyłany przez kontrolkę przycisku do elementu nadrzędnego (zazwyczaj klasą pochodną [cdialog —](../../mfc/reference/cdialog-class.md)), Dodaj funkcji członkowskiej wpisu i program obsługi komunikatów map wiadomości do klasy nadrzędnej dla każdego komunikatu.  
  
 Każdy wpis mapy komunikatów ma następującą postać:  
  
 **ON_**powiadomień **(**`id`, `memberFxn` **)**  
  
 gdzie `id` Określa identyfikator okno podrzędne formantu wysyłania powiadomienia i `memberFxn` jest nazwą funkcji członkowskiej nadrzędnego zostały zapisane do obsługi powiadomień.  
  
 Prototyp funkcji elementu nadrzędnego, jak wygląda następująco:  
  
 **afx_msg** `void` `memberFxn` **();**  
  
 Potencjalne wpisy mapy wiadomości są następujące:  
  
|Wpis w mapie|Wysyłane do nadrzędnego, gdy...|  
|---------------|----------------------------|  
|**ON_BN_CLICKED**|Użytkownik kliknie przycisk.|  
|**ON_BN_DOUBLECLICKED**|Użytkownik kliknie dwukrotnie przycisk.|  
  
 W przypadku utworzenia `CButton` obiektu z zasobem okna dialogowego `CButton` obiekt zostanie zniszczony automatycznie, gdy użytkownik zamyka okno dialogowe.  
  
 W przypadku utworzenia `CButton` obiektów w ramach okna, konieczne może być zniszczenia. W przypadku utworzenia `CButton` obiektów na stercie przy użyciu **nowe** funkcji, należy wywołać **usunąć** obiektu zniszczyć ją, gdy użytkownik zamyka systemu Windows przycisk formantu. W przypadku utworzenia `CButton` obiekt na stosie, lub jest osadzony w obiekcie nadrzędnym okna dialogowego, zostanie zniszczony automatycznie.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CButton`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cbutton"></a>CButton::CButton  
 Konstruuje `CButton` obiektu.  
  
```  
CButton();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]  
  
##  <a name="create"></a>CButton::Create  
 Tworzy kontrolkę przycisku systemu Windows i dołącza go do `CButton` obiektu.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszCaption`  
 Określa tekst formantu przycisku.  
  
 `dwStyle`  
 Określa styl formantu przycisku. Zastosuj dowolną kombinację [style przycisków](../../mfc/reference/styles-used-by-mfc.md#button-styles) do przycisku.  
  
 `rect`  
 Określa rozmiar i położenie formantu przycisku. Może być albo `CRect` obiektu lub `RECT` struktury.  
  
 `pParentWnd`  
 Określa okno nadrzędne kontrolki przycisku, zwykle `CDialog`. Nie może być **NULL**.  
  
 `nID`  
 Określa identyfikator formantu przycisku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CButton` obiektu w dwóch krokach. Najpierw należy wywołać konstruktora, a następnie wywołać **Utwórz**, która tworzy kontrolkę przycisku systemu Windows i dołącza go do `CButton` obiektu.  
  
 Jeśli **ws_visible —** podano stylu, system Windows wysyła formantu przycisku wszystkie komunikaty do aktywowania i wyświetlać przycisk wymagane.  
  
 Zastosuj następujące [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) do formantu przycisku:  
  
- **Ws_child —** zawsze  
  
- **Ws_visible —** zwykle  
  
- **Ws_disabled —** rzadko  
  
- **Ws_group —** na grupowanie formantów  
  
- **Ws_tabstop —** do uwzględnienia przycisku w kolejności tabulacji  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]  
  
##  <a name="drawitem"></a>CButton::DrawItem  
 Wywoływane przez platformę, gdy zmieniono visual aspekt przycisku rysowanych przez właściciela.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Długie wskaźnik do [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) struktury. Struktura zawiera informacje dotyczące elementu, który ma być rysowany i typ rysunku wymagane.  
  
### <a name="remarks"></a>Uwagi  
 Przycisk rysowanych przez właściciela ma **bs_ownerdraw —** styl zestawu. Przesłonić tę funkcję elementu członkowskiego, aby zaimplementować rysunku rysowanych przez właściciela `CButton` obiektu. Aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interfejsu (GDI), wybrane kontekst wyświetlania dostarczane w `lpDrawItemStruct` przed element członkowski kończy funkcji.  
  
 Zobacz też [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) styl wartości.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]  
  
##  <a name="getbitmap"></a>CButton::GetBitmap  
 Wywołanie tej funkcji członkowskich można pobrać uchwytu mapy bitowej wcześniej ustawione z [SetBitmap](#setbitmap), która jest skojarzony z przyciskiem.  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do mapy bitowej. **Wartość NULL** Jeśli nie mapy bitowej jest wcześniej określony.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]  
  
##  <a name="getbuttonstyle"></a>CButton::GetButtonStyle  
 Pobiera informacje o stylu formantu przycisku.  
  
```  
UINT GetButtonStyle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca stylów przycisków dla tej `CButton` obiektu. Ta funkcja zwraca tylko [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) wartości stylu, nie jakiekolwiek inne style okna.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]  
  
##  <a name="getcheck"></a>CButton::GetCheck  
 Pobiera stan wyboru pole wyboru lub przycisku radiowego.  
  
```  
int GetCheck() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość zwrócona przez kontrolkę przycisku utworzone za pomocą **bs_autocheckbox —**, **bs_autoradiobutton —**, **bs_auto3state —**, **bs_checkbox —**, **Bs_radiobutton —**, lub **bs_3state —** styl jest jednym z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|**BST_UNCHECKED**|Stan przycisku jest zaznaczone.|  
|**BST_CHECKED**|Stan przycisku jest zaznaczone.|  
|**BST_INDETERMINATE**|Stan przycisku jest nieokreślony (ma zastosowanie tylko wtedy, gdy przycisk **bs_3state —** lub **bs_auto3state —** styl).|  
  
 Jeśli przycisk ma inny styl, jest zwracana wartość **BST_UNCHECKED**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]  
  
##  <a name="getcursor"></a>CButton::GetCursor  
 Wywołanie tej funkcji członkowskich można pobrać uchwytu kursora, ustaw wcześniej z [SetCursor](#setcursor), która jest skojarzony z przyciskiem.  
  
```  
HCURSOR GetCursor();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do obrazu kursora. **Wartość NULL** Jeśli wcześniej jest określony żaden kursor.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]  
  
##  <a name="geticon"></a>CButton::GetIcon  
 Wywołanie tej funkcji członkowskich można pobrać uchwytu ikony, ustaw wcześniej z [SetIcon](#seticon), która jest skojarzony z przyciskiem.  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do ikony. **Wartość NULL** Jeśli brak wcześniej określonych ikon.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]  
  
##  <a name="getidealsize"></a>CButton::GetIdealSize  
 Pobiera rozmiar idealny dla formantu przycisku.  
  
```  
BOOL GetIdealSize(SIZE* psize);
```  
  
### <a name="parameters"></a>Parametry  
 *psize*  
 Wskaźnik do bieżącego rozmiaru przycisku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcje **BCM_GETIDEALSIZE** komunikatu, zgodnie z opisem w [przyciski](http://msdn.microsoft.com/library/windows/desktop/bb775943) część zestawu Windows SDK.  
  
##  <a name="getimagelist"></a>CButton::GetImageList  
 Wywołanie tej metody można odczytać listy obrazów formantu przycisku.  
  
```  
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```  
  
### <a name="parameters"></a>Parametry  
 `pbuttonImagelist`  
 Wskaźnik do listy obrazów `CButton` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcje **BCM_GETIMAGELIST** komunikatu, zgodnie z opisem w [przyciski](http://msdn.microsoft.com/library/windows/desktop/bb775943) część zestawu Windows SDK.  
  
##  <a name="getnote"></a>CButton::GetNote  
 Pobiera tekst uwagi skojarzony z formantem łącze bieżącego polecenia.  
  
```  
CString GetNote() const;  
  
BOOL GetNote(
    LPTSTR lpszNote,   
    UINT* cchNote) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[out]`lpszNote`|Wskaźnik do buforu, który element wywołujący jest odpowiedzialny za alokowanie i dealokowanie. Jeśli wartość zwracana jest `true`bufor zawiera tekst uwagi, która jest skojarzona z bieżącym formantem łącze polecenia; w przeciwnym razie, bufor jest bez zmian.|  
|[w, out]`cchNote`|Wskaźnik do zmiennej liczby całkowitej bez znaku.<br /><br /> Gdy ta metoda jest wywoływana, zmienna zawiera rozmiar buforu określony przez `lpszNote` parametru.<br /><br /> Gdy metoda zwróci wartość, jeśli jest zwracana wartość `true` zmiennej zawiera rozmiar Uwaga skojarzony z formantem łącze bieżącego polecenia. Jeśli wartość zwracana jest `false`, zmienna zawiera rozmiar buforu, muszą zawierać uwagi.|  
  
### <a name="return-value"></a>Wartość zwracana  
 W pierwszym przeciążenia [cstring —](../../atl-mfc-shared/using-cstring.md) obiekt, który zawiera tekst uwagi skojarzony z formantem łącze bieżącego polecenia.  
  
 —lub—  
  
 W drugim przeciążenia `true` Jeśli ta metoda jest pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można użyć tylko z formantami, którego styl przycisku jest `BS_COMMANDLINK` lub `BS_DEFCOMMANDLINK`.  
  
 Ta metoda wysyła [BCM_GETNOTE](http://msdn.microsoft.com/library/windows/desktop/bb775965) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="getnotelength"></a>CButton::GetNoteLength  
 Pobiera długość tekstu Uwaga dla kontrolki linku bieżącego polecenia.  
  
```  
UINT GetNoteLength() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość tekstu Uwaga, 16-bitowych znaków Unicode, dla bieżącego polecenia kontrolki łącza.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można użyć tylko z formantami, którego styl przycisku jest `BS_COMMANDLINK` lub `BS_DEFCOMMANDLINK`.  
  
 Ta metoda wysyła [BCM_GETNOTELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb775967) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="getsplitglyph"></a>CButton::GetSplitGlyph  
 Pobiera skojarzone z bieżącym formantu przycisku podziału w obrębie symboli.  
  
```  
TCHAR GetSplitGlyph() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Znak symbolu skojarzony z bieżącym formantu przycisku podziału.  
  
### <a name="remarks"></a>Uwagi  
 Symbol jest fizyczna reprezentacja znaku w określonej czcionki. Na przykład kontrolkę przycisku podziału może być oznaczone symbolu znacznika wyboru znaku Unicode (U + 2713).  
  
 Tej metody można użyć tylko z formantami, którego styl przycisku jest `BS_SPLITBUTTON` lub `BS_DEFSPLITBUTTON`.  
  
 Ta metoda inicjuje `mask` członkiem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury z `BCSIF_GLYPH` flagi, a następnie wysyła, które struktury w [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) komunikat, który opisano w systemie Windows SDK. Po powrocie z funkcji wiadomości, ta metoda pobiera symbolu z `himlGlyph` elementu członkowskiego struktury.  
  
##  <a name="getsplitimagelist"></a>CButton::GetSplitImageList  
 Pobiera [listy obrazów](../../mfc/reference/cimagelist-class.md) dla bieżącego formantu przycisku podziału.  
  
```  
CImageList* GetSplitImageList() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można użyć tylko z formantami, którego styl przycisku jest `BS_SPLITBUTTON` lub `BS_DEFSPLITBUTTON`.  
  
 Ta metoda inicjuje `mask` członkiem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury z `BCSIF_IMAGE` flagi, a następnie wysyła, które struktury w [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) komunikat, który opisano w systemie Windows SDK. Po powrocie z funkcji wiadomości, ta metoda pobiera listy obrazów z `himlGlyph` elementu członkowskiego struktury.  
  
##  <a name="getsplitinfo"></a>CButton::GetSplitInfo  
 Pobiera parametry, które określają, jak Windows rysuje bieżącego formantu przycisku podziału.  
  
```  
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[out]`pInfo`|Wskaźnik do [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury, która otrzymuje informacje o bieżącym formantu przycisku podziału. Element wywołujący jest odpowiedzialny za przydzielanie struktury.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można użyć tylko z formantami, którego styl przycisku jest `BS_SPLITBUTTON` lub `BS_DEFSPLITBUTTON`.  
  
 Ta metoda wysyła [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="getsplitsize"></a>CButton::GetSplitSize  
 Pobiera prostokąt ograniczający składnika listy rozwijanej bieżącego formantu przycisku podziału.  
  
```  
BOOL GetSplitSize(LPSIZE pSize) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[out]`pSize`|Wskaźnik do [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) strukturę, która odbiera opis prostokąta.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można użyć tylko z formantami, którego styl przycisku jest `BS_SPLITBUTTON` lub `BS_DEFSPLITBUTTON`.  
  
 Po rozwinięciu formantu przycisku podziału będzie możliwe wyświetlenie składnika listy rozwijanej, na przykład kontrolka listy lub modułu stronicowania. Ta metoda pobiera prostokąt ograniczający, który zawiera składnik listy rozwijanej.  
  
 Ta metoda inicjuje `mask` członkiem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury z `BCSIF_SIZE` flagi, a następnie wysyła, które struktury w [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) komunikat, który opisano w systemie Windows SDK. Po powrocie z funkcji wiadomości, ta metoda pobiera prostokąt ograniczający z `size` elementu członkowskiego struktury.  
  
##  <a name="getsplitstyle"></a>CButton::GetSplitStyle  
 Pobiera style przycisku podziału definiujące bieżącego formantu przycisku podziału.  
  
```  
UINT GetSplitStyle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bitowe połączenie style przycisku podziału. Aby uzyskać więcej informacji, zobacz `uSplitStyle` członkiem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można użyć tylko z formantami, którego styl przycisku jest `BS_SPLITBUTTON` lub `BS_DEFSPLITBUTTON`.  
  
 Style przycisku podziału Określ wyrównanie, współczynnik proporcji i postaci graficznej, z którym Windows rysuje ikonę przycisku podziału.  
  
 Ta metoda inicjuje `mask` członkiem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury z `BCSIF_STYLE` flagi, a następnie wysyła, które struktury w [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) komunikat, który opisano w systemie Windows SDK. Po powrocie z funkcji wiadomości, ta metoda pobiera style przycisku podziału z `uSplitStyle` elementu członkowskiego struktury.  
  
##  <a name="getstate"></a>CButton::GetState  
 Pobiera stan formantu przycisku.  
  
```  
UINT GetState() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pole bitowe zawierającego kombinację wartości, które wskazują bieżący stan formantu przycisku. W poniższej tabeli przedstawiono możliwe wartości.  
  
|Stan przycisku|Wartość|Opis|  
|------------------|-----------|-----------------|  
|`BST_UNCHECKED`|0x0000|Stan początkowy.|  
|`BST_CHECKED`|0X0001|Kontrolka przycisku jest zaznaczone.|  
|`BST_INDETERMINATE`|0X0002|Stan jest nieokreślony (możliwe tylko wtedy, gdy kontrolka przycisku ma trzy stany).|  
|`BST_PUSHED`|0X0004|Formant przycisk jest naciśnięty.|  
|`BST_FOCUS`|0X0008|Button — formant ma fokus.|  
  
### <a name="remarks"></a>Uwagi  
 Formantu przycisku o `BS_3STATE` lub `BS_AUTO3STATE` styl przycisku tworzy pole wyboru, które ma stan trzeci o nazwie Stan nieokreślony. Stan nieokreślony wskazuje, że pole wyboru jest zaznaczone ani niezaznaczone.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]  
  
##  <a name="gettextmargin"></a>CButton::GetTextMargin  
 Wywołanie tej metody można uzyskać tekstu marginesu `CButton` obiektu.  
  
```  
BOOL GetTextMargin(RECT* pmargin);
```  
  
### <a name="parameters"></a>Parametry  
 `pmargin`  
 Wskaźnik do tekstu marginesu `CButton` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca tekst margines.  
  
### <a name="remarks"></a>Uwagi  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcje **BCM_GETTEXTMARGIN** komunikatu, zgodnie z opisem w [przyciski](http://msdn.microsoft.com/library/windows/desktop/bb775943) część zestawu Windows SDK.  
  
##  <a name="setbitmap"></a>CButton::SetBitmap  
 Wywołanie tej funkcji Członkowskich, aby skojarzyć nowe mapy bitowej z przyciskiem.  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 `hBitmap`  
 Dojście mapy bitowej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście mapy bitowej wcześniej skojarzone z przyciskiem.  
  
### <a name="remarks"></a>Uwagi  
 Mapy bitowej zostaną automatycznie umieszczone rachunku przycisk domyślnie wyśrodkowany. Jeśli mapy bitowej jest za duży dla przycisku, zostaną przycięte po obu stronach. Możesz wybrać inne opcje wyrównania, takie jak następujące:  
  
- **BS_TOP —**  
  
- **BS_LEFT —**  
  
- **BS_RIGHT —**  
  
- **BS_CENTER —**  
  
- **BS_BOTTOM —**  
  
- **BS_VCENTER —**  
  
 W przeciwieństwie do [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), która używa czterech map bitowych na przycisku `SetBitmap` używa tylko jeden mapy bitowej na przycisku. Po naciśnięciu przycisku mapy bitowej pojawia się przesunięcie w dół i w prawo.  
  
 Użytkownik jest odpowiedzialny za zwolnienie mapy bitowej, po zakończeniu z nim.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]  
  
##  <a name="setbuttonstyle"></a>CButton::SetButtonStyle  
 Zmienia styl przycisku.  
  
```  
void SetButtonStyle(
    UINT nStyle,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nStyle`  
 Określa [styl przycisku](../../mfc/reference/styles-used-by-mfc.md#button-styles).  
  
 `bRedraw`  
 Określa, czy przycisk jest narysowania. Wartość niezerowa ponownie rysuje przycisku. Wartość 0 nie są odświeżane przycisku. Przycisk zostanie narysowany ponownie domyślnie.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `GetButtonStyle` funkcji członkowskiej pobrać styl przycisku. Word znaczącymi bitami stylu przycisk Zakończ jest styl specyficzne dla przycisku.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]  
  
##  <a name="setcheck"></a>CButton::SetCheck  
 Ustawia lub resetuje stan wyboru pole wyboru lub przycisku radiowego.  
  
```  
void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>Parametry  
 `nCheck`  
 Określa stan wyboru. Ten parametr może mieć jedną z następujących czynności:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|**BST_UNCHECKED**|Ustaw stan przycisku Usuń zaznaczenie.|  
|**BST_CHECKED**|Ustaw stan przycisku kontroli.|  
|**BST_INDETERMINATE**|Ustaw stan przycisku nieokreślony. Ta wartość może być używana tylko wtedy, gdy przycisk **bs_3state —** lub **bs_auto3state —** stylu.|  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska nie ma wpływu na przycisku polecenia.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]  
  
##  <a name="setcursor"></a>CButton::SetCursor  
 Wywołanie tej funkcji Członkowskich, aby skojarzyć nowe kursora z przycisku.  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>Parametry  
 `hCursor`  
 Dojście kursora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście kursora wcześniej skojarzone z przyciskiem.  
  
### <a name="remarks"></a>Uwagi  
 Kursor zostanie umieszczony automatycznie rachunku przycisk domyślnie wyśrodkowany. Jeśli kursor jest za duży dla przycisku, zostaną przycięte po obu stronach. Możesz wybrać inne opcje wyrównania, takie jak następujące:  
  
- **BS_TOP —**  
  
- **BS_LEFT —**  
  
- **BS_RIGHT —**  
  
- **BS_CENTER —**  
  
- **BS_BOTTOM —**  
  
- **BS_VCENTER —**  
  
 W odróżnieniu od [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), która używa czterech map bitowych na przycisku `SetCursor` używa tylko kursor na przycisku. Gdy przycisk jest naciśnięty, pojawi się kursor przesunięcie w dół i w prawo.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]  
  
##  <a name="setdropdownstate"></a>CButton::SetDropDownState  
 Ustawia stan listy rozwijanej bieżącego formantu przycisku podziału.  
  
```  
BOOL SetDropDownState(BOOL fDropDown);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`fDropDown`|`true`Aby ustawić `BST_DROPDOWNPUSHED` stanu; w przeciwnym razie `false`.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Kontrolka przycisku podziału ma styl `BS_SPLITBUTTON` lub `BS_DEFSPLITBUTTON` i składa się z przycisku i strzałkę listy rozwijanej, aby po jego prawej stronie. Aby uzyskać więcej informacji, zobacz [style przycisku](http://msdn.microsoft.com/library/windows/desktop/bb775951). Stan listy rozwijanej określony zazwyczaj, gdy użytkownik kliknie strzałkę listy rozwijanej. Użyj tej metody, można programowo ustawić stan listy rozwijanej formantu. Strzałkę listy rozwijanej jest rysowane przyciemnione do wskazywania stanu.  
  
 Ta metoda wysyła [BCM_SETDROPDOWNSTATE](http://msdn.microsoft.com/library/windows/desktop/bb775973) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_splitButton`, która jest używana do uzyskania programowego dostępu do formantu przycisku podziału. Ta zmienna jest używana w poniższym przykładzie.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu ustawia stan formantu przycisku podziału, aby wskazać, że zostanie przypisany strzałkę listy rozwijanej.  
  
 [!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]  
  
##  <a name="setelevationrequired"></a>CButton::SetElevationRequired  
 Ustawia stan bieżący formantu przycisku `elevation required`, która jest wymagana do formantu, aby wyświetlić ikony z podwyższonym poziomem uprawnień zabezpieczeń.  
  
```  
BOOL SetElevationRequired(BOOL fElevationRequired);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`fElevationRequired`|`true`Aby ustawić `elevation required` stanu; w przeciwnym razie `false`.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Formant łączy przycisk lub polecenie wymaga uprawnień zabezpieczeń z podwyższonym poziomem uprawnień do wykonywania akcji, ustawianie formantu `elevation required` stanu. Następnie system Windows wyświetli ikona tarczy kontroli konta użytkownika (UAC) w formancie. Aby uzyskać więcej informacji, zobacz "Kontrola konta użytkownika" w [MSDN](http://go.microsoft.com/fwlink/p/?linkid=18507).  
  
 Ta metoda wysyła [BCM_SETSHIELD](http://msdn.microsoft.com/library/windows/desktop/bb775979) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="seticon"></a>CButton::SetIcon  
 Wywołanie tej funkcji Członkowskich do skojarzenia z przyciskiem nową ikonę.  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>Parametry  
 `hIcon`  
 Dojście ikony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście ikony wcześniej skojarzone z przyciskiem.  
  
### <a name="remarks"></a>Uwagi  
 Ikona zostaną automatycznie umieszczone rachunku przycisk domyślnie wyśrodkowany. Jeśli ikona jest za duży dla przycisku, zostaną przycięte po obu stronach. Możesz wybrać inne opcje wyrównania, takie jak następujące:  
  
- **BS_TOP —**  
  
- **BS_LEFT —**  
  
- **BS_RIGHT —**  
  
- **BS_CENTER —**  
  
- **BS_BOTTOM —**  
  
- **BS_VCENTER —**  
  
 W przeciwieństwie do [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), która używa czterech map bitowych na przycisku, `SetIcon` używa tylko jeden ikony dla przycisku. Po naciśnięciu przycisku pojawi się ikona przesunięcie w dół i w prawo.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]  
  
##  <a name="setimagelist"></a>CButton::SetImageList  
 Wywołanie tej metody można ustawić na liście obrazów `CButton` obiektu.  
  
```  
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```  
  
### <a name="parameters"></a>Parametry  
 `pbuttonImagelist`  
 Wskaźnik do nowej listy obrazów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcje **BCM_SETIMAGELIST** komunikatu, zgodnie z opisem w [przyciski](http://msdn.microsoft.com/library/windows/desktop/bb775943) część zestawu Windows SDK.  
  
##  <a name="setnote"></a>CButton::SetNote  
 Ustawia tekst uwagi dla kontrolki linku bieżącego polecenia.  
  
```  
BOOL SetNote(LPCTSTR lpszNote);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`lpszNote`|Wskaźnik na ciąg Unicode jest ustawiony jako tekst uwagi dla kontrolki linku polecenia.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można użyć tylko z formantami, którego styl przycisku jest `BS_COMMANDLINK` lub `BS_DEFCOMMANDLINK`.  
  
 Ta metoda wysyła [BCM_SETNOTE](http://msdn.microsoft.com/library/windows/desktop/bb775977) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_cmdLink`, która jest używane do uzyskania programowego dostępu do polecenia kontrolki łącza. Ta zmienna jest używana w poniższym przykładzie.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu ustawia tekst uwagi dla kontrolki linku polecenia.  
  
 [!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]  
  
##  <a name="setsplitglyph"></a>CButton::SetSplitGlyph  
 Kojarzy określonego symbolu z bieżącego formantu przycisku podziału.  
  
```  
BOOL SetSplitGlyph(TCHAR chGlyph);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`chGlyph`|Znak, który określa symbolu do użycia jako strzałkę listy rozwijanej przycisku podziału.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można użyć tylko z formantami, które mają styl przycisku `BS_SPLITBUTTON` lub `BS_DEFSPLITBUTTON`.  
  
 Symbol jest fizyczna reprezentacja znaku w określonej czcionki. `chGlyph` Parametr nie jest używany jako symbolu, ale zamiast tego jest używany do wybierania symbolu z zestawu symboli zdefiniowanych w systemie. Domyślnego symbolu strzałkę listy rozwijanej jest określona przez znak "6" i podobne znak Unicode czarny dół wskazanie TRÓJKĄT (U + 25BC).  
  
 Ta metoda inicjuje `mask` członkiem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury z `BCSIF_GLYPH` flagę i `himlGlyph` element członkowski o `chGlyph` parametr, a następnie wysyła, które struktury w [ BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="setsplitimagelist"></a>CButton::SetSplitImageList  
 Kojarzy [listy obrazów](../../mfc/reference/cimagelist-class.md) z bieżącego formantu przycisku podziału.  
  
```  
BOOL SetSplitImageList(CImageList* pSplitImageList);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`pSplitImageList`|Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiektu można przypisać do bieżącego formantu przycisku podziału.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można użyć tylko z formantami, którego styl przycisku jest `BS_SPLITBUTTON` lub `BS_DEFSPLITBUTTON`.  
  
 Ta metoda inicjuje `mask` członkiem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury z `BCSIF_IMAGE` flagę i `himlGlyph` element członkowski o `pSplitImageList` parametr, a następnie wysyła, które struktury w [ BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="setsplitinfo"></a>CButton::SetSplitInfo  
 Określa parametry, które określają, jak Windows rysuje bieżącego formantu przycisku podziału.  
  
```  
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`pInfo`|Wskaźnik do [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury, który definiuje bieżącego formantu przycisku podziału.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można użyć tylko z formantami, którego styl przycisku jest `BS_SPLITBUTTON` lub `BS_DEFSPLITBUTTON`.  
  
 Ta metoda wysyła [BCM_SETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775981) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_splitButton`, która jest używana do uzyskania programowego dostępu do formantu przycisku podziału.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu zmienia symbolu, służący do strzałkę listy rozwijanej przycisku podziału. Przykład zastępuje symbolu trójkąt skierowany do domyślnego symbolu trójkąt wskazująca w dół. Symbol, który jest wyświetlany jest zależna od znak, który można określić w `himlGlyph` członkiem `BUTTON_SPLITINFO` struktury. Określono symbolu trójkąt wskazująca w dół za pomocą znaku "6"i symbolu trójkąt skierowany jest określona przez znak "5". Porównanie, można znaleźć w artykule metody wygody [CButton::SetSplitGlyph](#setsplitglyph).  
  
 [!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]  
  
##  <a name="setsplitsize"></a>CButton::SetSplitSize  
 Ustawia prostokąt ograniczający składnika listy rozwijanej bieżącego formantu przycisku podziału.  
  
```  
BOOL SetSplitSize(LPSIZE pSize);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`pSize`|Wskaźnik do [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktury, która opisuje prostokąt ograniczający.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można użyć tylko z formantami, którego styl przycisku jest `BS_SPLITBUTTON` lub `BS_DEFSPLITBUTTON`.  
  
 Po rozwinięciu formantu przycisku podziału będzie możliwe wyświetlenie składnika listy rozwijanej, na przykład kontrolka listy lub modułu stronicowania. Ta metoda określa rozmiar prostokątem, który zawiera składnik listy rozwijanej.  
  
 Ta metoda inicjuje `mask` członkiem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury z `BCSIF_SIZE` flagę i `size` element członkowski o `pSize` parametr, a następnie wysyła, które struktury w [ BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_splitButton`, która jest używana do uzyskania programowego dostępu do formantu przycisku podziału. Ta zmienna jest używana w poniższym przykładzie.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu podwaja rozmiar strzałkę listy rozwijanej przycisku podziału.  
  
 [!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]  
  
##  <a name="setsplitstyle"></a>CButton::SetSplitStyle  
 Ustawia styl bieżącego formantu przycisku podziału.  
  
```  
BOOL SetSplitStyle(UINT uSplitStyle);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`uSplitStyle`|Bitowe połączenie style przycisku podziału. Aby uzyskać więcej informacji, zobacz `uSplitStyle` członkiem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można użyć tylko z formantami, którego styl przycisku jest `BS_SPLITBUTTON` lub `BS_DEFSPLITBUTTON`.  
  
 Style przycisku podziału Określ wyrównanie, współczynnik proporcji i postaci graficznej, z którym Windows rysuje ikonę przycisku podziału. Aby uzyskać więcej informacji, zobacz `uSplitStyle` członkiem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury.  
  
 Ta metoda inicjuje `mask` członkiem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury z `BCSIF_STYLE` flagę i `uSplitStyle` element członkowski o `uSplitStyle` parametr, a następnie wysyła, które struktury w [ BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_splitButton`, która jest używana do uzyskania programowego dostępu do formantu przycisku podziału.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu ustawia styl strzałki rozwijanej przycisku podziału. `BCSS_ALIGNLEFT` Styl Wyświetla strzałkę po lewej stronie przycisku i `BCSS_STRETCH` styl zachowuje strzałkę listy rozwijanej proporcje rozmiaru przycisku.  
  
 [!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]  
  
##  <a name="setstate"></a>CButton::SetState  
 Określa, czy formant przycisku zostanie wyróżniona, czy nie.  
  
```  
void SetState(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Parametry  
 *bHighlight*  
 Określa, czy ma być wyróżniony przycisku. Wartość niezerowa wyróżnia przycisk; wartość 0 powoduje wyłączenie żadnych wyróżniania.  
  
### <a name="remarks"></a>Uwagi  
 Wyróżnianie wpływa na zewnątrz kontrolkę przycisku. Go nie ma wpływu na stan wyboru pole wyboru lub przycisku radiowego.  
  
 Kontrolka przycisku automatycznie zostanie wyróżniona, gdy użytkownik kliknie i przechowuje lewego przycisku myszy. Wyróżnianie zostanie usunięta, gdy użytkownik zwolni przycisk myszy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]  
  
##  <a name="settextmargin"></a>CButton::SetTextMargin  
 Wywołanie tej metody można ustawić tekstu marginesu `CButton` obiektu.  
  
```  
BOOL SetTextMargin(RECT* pmargin);
```  
  
### <a name="parameters"></a>Parametry  
 `pmargin`  
 Wskaźnik do nowego tekstu marginesu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcje **BCM_SETTEXTMARGIN** komunikatu, zgodnie z opisem w [przyciski](http://msdn.microsoft.com/library/windows/desktop/bb775943) część zestawu Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Ccombobox — klasa](../../mfc/reference/ccombobox-class.md)   
 [Klasa CEdit](../../mfc/reference/cedit-class.md)   
 [Clistbox — klasa](../../mfc/reference/clistbox-class.md)   
 [Klasa CScrollBar](../../mfc/reference/cscrollbar-class.md)   
 [Klasa CStatic](../../mfc/reference/cstatic-class.md)   
 [Klasa CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)   
 [Klasa CDialog](../../mfc/reference/cdialog-class.md)
