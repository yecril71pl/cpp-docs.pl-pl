---
title: Klasa CButton | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9932f8814855213f133323f2102e0cacf1e69c8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196714"
---
# <a name="cbutton-class"></a>Klasa CButton
Oferuje funkcje kontrolek przycisku Windows.  
  
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
|[CButton::Create](#create)|Tworzy formant przycisku Windows i dołącza je do `CButton` obiektu.|  
|[CButton::DrawItem](#drawitem)|Należy przesłonić, aby narysować rysowanych przez właściciela `CButton` obiektu.|  
|[CButton::GetBitmap](#getbitmap)|Pobiera uchwyt mapy bitowej ustawione wcześniej przy użyciu [SetBitmap](#setbitmap).|  
|[CButton::GetButtonStyle](#getbuttonstyle)|Pobiera informacje o stylu formantu przycisku.|  
|[CButton::GetCheck](#getcheck)|Pobiera stan wyboru kontrolki przycisku.|  
|[CButton::GetCursor](#getcursor)|Pobiera uchwyt obraz kursora ustawione wcześniej przy użyciu [SetCursor](#setcursor).|  
|[CButton::GetIcon](#geticon)|Pobiera uchwyt ikony ustawione wcześniej przy użyciu [SetIcon](#seticon).|  
|[CButton::GetIdealSize](#getidealsize)|Pobiera rozmiar idealny formantu przycisku.|  
|[CButton::GetImageList](#getimagelist)|Pobranie listy obrazów kontrolki przycisku.|  
|[CButton::GetNote](#getnote)|Pobiera składnik notatki bieżącego polecenia formantu łącza.|  
|[CButton::GetNoteLength](#getnotelength)|Pobiera długość tekstu notatki dla kontrolki linku bieżącego polecenia.|  
|[CButton::GetSplitGlyph](#getsplitglyph)|Pobiera symbol skojarzone z bieżącym kontrolki przycisku podziału.|  
|[CButton::GetSplitImageList](#getsplitimagelist)|Pobiera listę obrazu dla bieżącego kontrolki przycisku podziału.|  
|[CButton::GetSplitInfo](#getsplitinfo)|Pobiera informacje, które definiują bieżącego kontrolki przycisku podziału.|  
|[CButton::GetSplitSize](#getsplitsize)|Pobiera prostokąt otaczający składnika listy rozwijanej bieżącego kontrolki przycisku podziału.|  
|[CButton::GetSplitStyle](#getsplitstyle)|Pobiera style przycisku podziału, definiujące bieżącego kontrolki przycisku podziału.|  
|[CButton::GetState](#getstate)|Pobiera stan zaznaczenia, wyróżnij stanu i skoncentrować się stan kontrolki przycisku.|  
|[CButton::GetTextMargin](#gettextmargin)|Pobiera na marginesie tekstu formantu przycisku.|  
|[CButton::SetBitmap](#setbitmap)|Określa mapy bitowej, który będzie wyświetlany na przycisku.|  
|[CButton::SetButtonStyle](#setbuttonstyle)|Zmienia styl przycisku.|  
|[CButton::SetCheck](#setcheck)|Ustawia stan wyboru kontrolki przycisku.|  
|[CButton::SetCursor](#setcursor)|Określa obraz kursor, który będzie wyświetlany na przycisku.|  
|[CButton::SetDropDownState](#setdropdownstate)|Ustawia stan listy rozwijanej bieżącego kontrolki przycisku podziału.|  
|[CButton::SetIcon](#seticon)|Określa ikonę, która będzie wyświetlana na przycisku.|  
|[CButton::SetImageList](#setimagelist)|Ustawia listy obrazów kontrolki przycisku.|  
|[CButton::SetNote](#setnote)|Ustawia notatki bieżącego polecenia kontrolki łącza.|  
|[CButton::SetSplitGlyph](#setsplitglyph)|Kojarzy określonego symbolu z bieżącym kontrolki przycisku podziału.|  
|[CButton::SetSplitImageList](#setsplitimagelist)|Kojarzy listy obrazów z bieżącym kontrolki przycisku podziału.|  
|[CButton::SetSplitInfo](#setsplitinfo)|Określa informacje, które definiują bieżącego kontrolki przycisku podziału.|  
|[CButton::SetSplitSize](#setsplitsize)|Ustawia prostokąt otaczający składnika listy rozwijanej bieżącego kontrolki przycisku podziału.|  
|[CButton::SetSplitStyle](#setsplitstyle)|Ustawia styl bieżący formant przycisku podziału.|  
|[CButton::SetState](#setstate)|Ustawia stan wyróżniania kontrolki przycisku.|  
|[CButton::SetTextMargin](#settextmargin)|Ustawia margines tekstu kontrolki przycisku.|  
  
## <a name="remarks"></a>Uwagi  
 Formant przycisku jest oknem podrzędnym małe, prostokątne, które można kliknąć włączać i wyłączać. Przyciski można samodzielnie lub w grupach i albo może być oznaczony jako lub są wyświetlane bez tekstu. Przycisk zazwyczaj zmienia wygląd, gdy użytkownik kliknie przycisk.  
  
 Typowe przyciski są pola wyboru, przycisk radiowy, a przycisk. A `CButton` obiektu może stać się dowolną z tych opcji, zgodnie z opisem w [przycisk stylu](../../mfc/reference/styles-used-by-mfc.md#button-styles) określony podczas jego inicjowania przez [Utwórz](#create) funkcja elementu członkowskiego.  
  
 Ponadto [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) klasą pochodną `CButton` obsługuje tworzenie przycisk kontrolek oznaczonych obrazów mapę bitową zamiast tekstu. Element `CBitmapButton` może mieć osobne mapy bitowe dla przycisku w, w dół, fokus i wyłączone stanów.  
  
 Kontrolka przycisku można utworzyć z szablonu okna dialogowego lub bezpośrednio w kodzie. W obu przypadkach należy najpierw wywołać konstruktora `CButton` do konstruowania `CButton` obiektu; następnie wywołać `Create` funkcji elementu członkowskiego, aby utworzyć Windows przycisku sterowania i dołącz je do `CButton` obiektu.  
  
 Konstrukcja może być jednoetapowy proces w klasę pochodną `CButton`. Zapisywanie konstruktora dla klasy pochodnej i wywołanie `Create` z w konstruktorze.  
  
 Jeśli chcesz obsługiwać komunikaty powiadomień Windows wysyłany przez kontrolkę przycisku do elementu nadrzędnego (zazwyczaj klasą pochodną [CDialog](../../mfc/reference/cdialog-class.md)), dodanie funkcji składowej wejścia i program obsługi komunikatów mapy komunikatów do klasy nadrzędnej dla każdego komunikatu.  
  
 Każdy wpis mapy komunikatów ma następującą postać:  
  
 **ON_** powiadomień **(**`id`, `memberFxn` **)**  
  
 gdzie `id` Określa identyfikator okna elementu podrzędnego kontrolki wysyłania powiadomienia i `memberFxn` nazywa się nadrzędny element członkowski funkcji zostały napisane do obsługi powiadomień.  
  
 Prototyp funkcji elementu nadrzędnego jest następująca:  
  
 **afx_msg** `void` `memberFxn` **();**  
  
 Potencjalne wpisy mapy komunikatów są następujące:  
  
|Wpis mapy|Wysyłane do elementu nadrzędnego, gdy...|  
|---------------|----------------------------|  
|ON_BN_CLICKED|Użytkownik klika przycisk.|  
|ON_BN_DOUBLECLICKED|Użytkownik kliknie dwukrotnie przycisku.|  
  
 Jeśli tworzysz `CButton` obiekt z zasobem okna dialogowego `CButton` obiektu automatycznie jest niszczony, kiedy użytkownik zamknie okno dialogowe.  
  
 Jeśli tworzysz `CButton` obiekt w tym oknie, konieczne może być zniszczenia. Jeśli tworzysz `CButton` obiektów na stosie przy użyciu **nowe** funkcji, należy wywołać **Usuń** obiektu zniszczyć ją, gdy użytkownik zamknie Windows kontrolka przycisku. Jeśli tworzysz `CButton` obiekt na stosie, albo jest osadzony w nadrzędnego obiektu okna dialogowego, zostanie zniszczony automatycznie.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CButton`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cbutton"></a>  CButton::CButton  
 Konstruuje `CButton` obiektu.  
  
```  
CButton();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]  
  
##  <a name="create"></a>  CButton::Create  
 Tworzy formant przycisku Windows i dołącza je do `CButton` obiektu.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszCaption*  
 Określa tekst kontrolki przycisku.  
  
 *dwStyle*  
 Określa styl kontrolki przycisku. Zastosuj dowolną kombinację [style przycisków](../../mfc/reference/styles-used-by-mfc.md#button-styles) do przycisku.  
  
 *Rect*  
 Określa rozmiar i położenie kontrolki przycisku. Może być albo `CRect` obiektu lub `RECT` struktury.  
  
 *pParentWnd*  
 Określa okno nadrzędne kontrolki przycisku, zwykle `CDialog`. Nie może być równa NULL.  
  
 *nID*  
 Określa identyfikator kontrolki przycisku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Konstruowanie `CButton` obiektu w dwóch krokach. Po pierwsze wywołanie konstruktora, a następnie wywołać `Create`, który tworzy formant przycisku Windows i dołącza go do `CButton` obiektu.  
  
 Jeśli zostanie określony styl WS_VISIBLE, Windows wysyła kontrolki przycisku wszystkie komunikaty, które są wymagane do aktywowania i wyświetlać przycisk.  
  
 Zastosuj następujące [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles) do kontrolki przycisku:  
  
- WS_CHILD zawsze  
  
- WS_VISIBLE zwykle  
  
- WS_DISABLED rzadko  
  
- WS_GROUP kontrolek grupy  
  
- WS_TABSTOP aby umieścić przycisk w kolejności tabulacji  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]  
  
##  <a name="drawitem"></a>  CButton::DrawItem  
 Wywoływane przez platformę, gdy zmieni się wizualny aspekt przycisku rysowanych przez właściciela została zmieniona.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 *lpDrawItemStruct*  
 Długie wskaźnik do [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) struktury. Struktura zawiera informacje dotyczące elementu do rysowania i typ rysunku, wymagane.  
  
### <a name="remarks"></a>Uwagi  
 Przycisk rysowania przez właściciela zawiera zestaw stylów BS_OWNERDRAW. Zastąpienie tej funkcji elementu członkowskiego, aby zaimplementować rysunku rysowanych przez właściciela `CButton` obiektu. Aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interface (GDI), wybrany dla kontekstu wyświetlana podana w *lpDrawItemStruct* przed element członkowski funkcja kończy.  
  
 Zobacz też [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) stylu wartości.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]  
  
##  <a name="getbitmap"></a>  CButton::GetBitmap  
 Wywołaj tę funkcję elementu członkowskiego, można pobrać uchwytu mapy bitowej ustawione wcześniej przy użyciu [SetBitmap](#setbitmap), która jest skojarzony z przyciskiem.  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do mapy bitowej. Wartość NULL, jeśli nie bitmapy jest wcześniej określony.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]  
  
##  <a name="getbuttonstyle"></a>  CButton::GetButtonStyle  
 Pobiera informacje o stylu formantu przycisku.  
  
```  
UINT GetButtonStyle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dla tej klasy stylów przycisków `CButton` obiektu. Ta funkcja zwraca tylko [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) wartości stylu, nie żadnego innymi stylami okna.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]  
  
##  <a name="getcheck"></a>  CButton::GetCheck  
 Pobiera stan wyboru pole wyboru lub przycisku radiowego.  
  
```  
int GetCheck() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość zwrócona przez kontrolkę przycisku utworzony za pomocą BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON lub stylu BS_3STATE jest jednym z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|BST_UNCHECKED|Stan klawisza nie jest zaznaczone.|  
|BST_CHECKED|Stan przycisk jest sprawdzane.|  
|BST_INDETERMINATE|Stan przycisku jest nieokreślony (ma zastosowanie tylko wtedy, gdy przycisk stylu BS_3STATE lub BS_AUTO3STATE).|  
  
 Jeśli przycisk ma inne stylu, wartość zwracana jest BST_UNCHECKED.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]  
  
##  <a name="getcursor"></a>  CButton::GetCursor  
 Wywołaj tę funkcję elementu członkowskiego, można pobrać uchwytu kursora, ustawione wcześniej przy użyciu [SetCursor](#setcursor), która jest skojarzony z przyciskiem.  
  
```  
HCURSOR GetCursor();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do obrazu kursora. Wartość NULL, jeśli brak kursora jest wcześniej określony.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]  
  
##  <a name="geticon"></a>  CButton::GetIcon  
 Wywołaj tę funkcję elementu członkowskiego, można pobrać uchwytu ikony ustawione wcześniej przy użyciu [SetIcon](#seticon), która jest skojarzony z przyciskiem.  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do ikony. Wartość NULL, jeśli wcześniej określono żadnej ikony.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]  
  
##  <a name="getidealsize"></a>  CButton::GetIdealSize  
 Pobiera rozmiar idealny dla formantu button.  
  
```  
BOOL GetIdealSize(SIZE* psize);
```  
  
### <a name="parameters"></a>Parametry  
 *psize*  
 Wskaźnik na bieżący rozmiar przycisku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcjonalność komunikat BCM_GETIDEALSIZE zgodnie z opisem w [przyciski](https://msdn.microsoft.com/library/windows/desktop/bb775943) część zestawu Windows SDK.  
  
##  <a name="getimagelist"></a>  CButton::GetImageList  
 Wywołaj tę metodę można pobrać listy obrazów z kontrolki przycisku.  
  
```  
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```  
  
### <a name="parameters"></a>Parametry  
 *pbuttonImagelist*  
 Wskaźnik do listy obrazu `CButton` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcjonalność komunikat BCM_GETIMAGELIST zgodnie z opisem w [przyciski](https://msdn.microsoft.com/library/windows/desktop/bb775943) część zestawu Windows SDK.  
  
##  <a name="getnote"></a>  CButton::GetNote  
 Pobiera skojarzone z kontrolą bieżącą link polecenie tekstu Uwaga.  
  
```  
CString GetNote() const;  
  
BOOL GetNote(
    LPTSTR lpszNote,   
    UINT* cchNote) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[out] *lpszNote*|Wskaźnik do buforu, który obiekt wywołujący jest odpowiedzialny za alokowanie i dealokowanie. Jeśli wartość zwracana jest wartość TRUE, buforu zawiera tekst notatki, który jest skojarzony z bieżącą kontroli łącza polecenia; w przeciwnym razie bufor jest bez zmian.|  
|[out w] *cchNote*|Wskaźnik do zmiennej liczby całkowitej bez znaku.<br /><br /> Gdy ta metoda jest wywoływana, zmienna zawiera rozmiar buforu określony przez *lpszNote* parametru.<br /><br /> Gdy ta metoda zwraca, jeśli wartość zwracana jest wartość TRUE w zmiennej zawiera rozmiar Uwaga skojarzone z kontrolą bieżącą łącze polecenia. Jeśli wartość zwracana jest wartość FALSE, zmienna zawiera rozmiar buforu, muszą zawierać uwagi.|  
  
### <a name="return-value"></a>Wartość zwracana  
 W pierwsze przeciążenie [CString](../../atl-mfc-shared/using-cstring.md) obiekt, który zawiera tekst notatki skojarzone z kontrolą bieżącą łącze polecenia.  
  
 —lub—  
  
 Drugie przeciążenie wartość TRUE jeśli ta metoda się powiedzie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody tylko w przypadku którego styl przycisku jest BS_COMMANDLINK lub BS_DEFCOMMANDLINK kontrolki.  
  
 Ta metoda wysyła [BCM_GETNOTE](/windows/desktop/Controls/bcm-getnote) komunikat, który jest opisany w zestawie Windows SDK.  
  
##  <a name="getnotelength"></a>  CButton::GetNoteLength  
 Pobiera długość tekstu notatki dla kontrolki linku bieżącego polecenia.  
  
```  
UINT GetNoteLength() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość tekstu notatki, 16-bitowych znaków Unicode, dla kontrolki linku bieżącego polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody tylko w przypadku którego styl przycisku jest BS_COMMANDLINK lub BS_DEFCOMMANDLINK kontrolki.  
  
 Ta metoda wysyła [BCM_GETNOTELENGTH](/windows/desktop/Controls/bcm-getnotelength) komunikat, który jest opisany w zestawie Windows SDK.  
  
##  <a name="getsplitglyph"></a>  CButton::GetSplitGlyph  
 Pobiera symbol skojarzone z bieżącym kontrolki przycisku podziału.  
  
```  
TCHAR GetSplitGlyph() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Glif skojarzone z bieżącym kontrolki przycisku podziału.  
  
### <a name="remarks"></a>Uwagi  
 Glif jest fizyczna reprezentacja znaku w określonej czcionki. Na przykład formant przycisku podziału może posiadać symbol znaku Unicode znacznik wyboru (U + 2713).  
  
 Użyj tej metody tylko w przypadku którego styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON kontrolki.  
  
 Ta metoda inicjuje `mask` członkiem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktury z flagą BCSIF_GLYPH, a następnie wysyła, które struktury w [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) komunikat, który jest opisany w Windows SDK. Po powrocie z funkcji komunikatów ta metoda pobiera symbol z `himlGlyph` elementu członkowskiego struktury.  
  
##  <a name="getsplitimagelist"></a>  CButton::GetSplitImageList  
 Pobiera [listy obrazów](../../mfc/reference/cimagelist-class.md) dla bieżącego kontrolki przycisku podziału.  
  
```  
CImageList* GetSplitImageList() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody tylko w przypadku którego styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON kontrolki.  
  
 Ta metoda inicjuje `mask` członkiem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktury z flagą BCSIF_IMAGE, a następnie wysyła, które struktury w [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) komunikat, który jest opisany w Windows SDK. Po powrocie z funkcji komunikatów ta metoda umożliwia pobranie listy obrazów z `himlGlyph` elementu członkowskiego struktury.  
  
##  <a name="getsplitinfo"></a>  CButton::GetSplitInfo  
 Pobiera parametry, które określają, jak Windows pobiera bieżący formant przycisku podziału.  
  
```  
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[out] *pInfo*|Wskaźnik do [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) strukturę, która otrzymuje informacje o bieżącym kontrolki przycisku podziału. Obiekt wywołujący jest odpowiedzialny za przydzielanie struktury.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody tylko w przypadku którego styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON kontrolki.  
  
 Ta metoda wysyła [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) komunikat, który jest opisany w zestawie Windows SDK.  
  
##  <a name="getsplitsize"></a>  CButton::GetSplitSize  
 Pobiera prostokąt otaczający składnika listy rozwijanej bieżącego kontrolki przycisku podziału.  
  
```  
BOOL GetSplitSize(LPSIZE pSize) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[out] *pSize*|Wskaźnik do [rozmiar](https://msdn.microsoft.com/library/windows/desktop/dd145106) struktury, która odbiera opis prostokąt.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody tylko w przypadku którego styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON kontrolki.  
  
 Po rozwinięciu formant przycisku podziału umożliwia wyświetlanie składnika listy rozwijanej, takiego jak kontrolka listy lub kontroli pagera. Ta metoda pobiera prostokąt otaczający, który zawiera składnik listy rozwijanej.  
  
 Ta metoda inicjuje `mask` członkiem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktury z flagą BCSIF_SIZE, a następnie wysyła, które struktury w [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) komunikat, który jest opisany w Windows SDK. Po powrocie z funkcji komunikatów ta metoda pobiera prostokąt otaczający z `size` elementu członkowskiego struktury.  
  
##  <a name="getsplitstyle"></a>  CButton::GetSplitStyle  
 Pobiera style przycisku podziału, definiujące bieżącego kontrolki przycisku podziału.  
  
```  
UINT GetSplitStyle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bitowa kombinacja style przycisku podziału. Aby uzyskać więcej informacji, zobacz `uSplitStyle` członkiem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktury.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody tylko w przypadku którego styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON kontrolki.  
  
 Style przycisku podziału Określ wyrównanie, współczynnik proporcji i w postaci graficznej za pomocą którego Windows rysuje ikonę przycisku podziału.  
  
 Ta metoda inicjuje `mask` członkiem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktury z flagą BCSIF_STYLE, a następnie wysyła, które struktury w [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) komunikat, który jest opisany w Windows SDK. Po powrocie z funkcji komunikatów ta metoda pobiera style przycisku podziału z `uSplitStyle` elementu członkowskiego struktury.  
  
##  <a name="getstate"></a>  CButton::GetState  
 Pobiera stan kontrolki przycisku.  
  
```  
UINT GetState() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pola bitowe, które zawiera kombinację wartości, które wskazują bieżący stan kontrolki przycisku. Poniższa tabela zawiera listę możliwych wartości.  
  
|Stan przycisku|Wartość|Opis|  
|------------------|-----------|-----------------|  
|BST_UNCHECKED|0x0000|Stan początkowy.|  
|BST_CHECKED|0x0001|Kontrolka przycisku jest sprawdzana.|  
|BST_INDETERMINATE|0x0002|Stan jest nieokreślony (możliwe tylko wtedy, gdy formant przycisku ma trzy stany).|  
|BST_PUSHED|0x0004|Użytkownik naciśnie kontrolkę przycisku.|  
|BST_FOCUS|0x0008|Kontrolka przycisku ma fokus.|  
  
### <a name="remarks"></a>Uwagi  
 Kontrolki przycisku w stylu przycisk BS_3STATE lub BS_AUTO3STATE tworzy pole wyboru, które ma stan trzeci, który nosi nazwę Stan nieokreślony. Nieokreślony stan wskazuje, że pole wyboru jest zaznaczone ani niezaznaczone.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]  
  
##  <a name="gettextmargin"></a>  CButton::GetTextMargin  
 Wywołanie tej metody można pobrać tekstu marginesu `CButton` obiektu.  
  
```  
BOOL GetTextMargin(RECT* pmargin);
```  
  
### <a name="parameters"></a>Parametry  
 *pmargin*  
 Wskaźnik do tekstu marginesu `CButton` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca margines tekstu.  
  
### <a name="remarks"></a>Uwagi  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcjonalność komunikat BCM_GETTEXTMARGIN zgodnie z opisem w [przyciski](https://msdn.microsoft.com/library/windows/desktop/bb775943) część zestawu Windows SDK.  
  
##  <a name="setbitmap"></a>  CButton::SetBitmap  
 Wywołaj tę funkcję elementu członkowskiego, aby skojarzyć nowej mapy bitowej przy użyciu przycisku.  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 *hBitmap*  
 Uchwyt mapy bitowej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Uchwyt mapy bitowej była poprzednio skojarzona z przyciskiem.  
  
### <a name="remarks"></a>Uwagi  
 Mapy bitowej zostaną automatycznie umieszczone rachunku przycisku, a ich tematyka domyślnie. W przypadku zbyt duże, aby przycisk mapy bitowej zostaną przycięte po obu stronach. Możesz wybrać inne opcje wyrównania, w tym następujące:  
  
- BS_TOP  
  
- BS_LEFT  
  
- BS_RIGHT  
  
- BS_CENTER  
  
- BS_BOTTOM  
  
- BS_VCENTER  
  
 W odróżnieniu od [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), cztery map bitowych na przycisku, który używa `SetBitmap` używa tylko jednej mapy bitowej na przycisku. Po naciśnięciu przycisku, aby przenieść w dół, a po prawej stronie pojawi się mapy bitowej.  
  
 Odpowiedzialność za zwalniając mapy bitowej, gdy są z nią zrobić.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]  
  
##  <a name="setbuttonstyle"></a>  CButton::SetButtonStyle  
 Zmienia styl przycisku.  
  
```  
void SetButtonStyle(
    UINT nStyle,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *nStyle*  
 Określa [przycisk stylu](../../mfc/reference/styles-used-by-mfc.md#button-styles).  
  
 *bRedraw*  
 Określa, czy przycisk ma być narysowany ponownie. Wartość różną od zera odrysowuje przycisku. Wartość 0 nie są odświeżane przycisku. Ten przycisk jest odświeżana, domyślnie.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `GetButtonStyle` funkcję elementu członkowskiego, aby pobrać styl przycisku. Word niskiego rzędu stylu przycisk kończenia jest styl specyficzne dla przycisku.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]  
  
##  <a name="setcheck"></a>  CButton::SetCheck  
 Ustawia lub resetuje stan wyboru pole wyboru lub przycisku radiowego.  
  
```  
void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>Parametry  
 *nSprawdź*  
 Określa stan zaznaczenia. Ten parametr może być jedną z następujących czynności:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|BST_UNCHECKED|Ustaw stan klawisza niezaznaczone.|  
|BST_CHECKED|Ustaw stan klawisza sprawdzony.|  
|BST_INDETERMINATE|Ustaw stan klawisza nieokreślony. Ta wartość może służyć tylko wtedy, gdy przycisk BS_3STATE lub BS_AUTO3STATE stylu.|  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego nie ma wpływu na przycisk.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]  
  
##  <a name="setcursor"></a>  CButton::SetCursor  
 Wywołaj tę funkcję elementu członkowskiego, aby skojarzyć nowe kursora z przycisku.  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>Parametry  
 *hCursor*  
 Uchwyt kursora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Uchwyt kursora była poprzednio skojarzona z przyciskiem.  
  
### <a name="remarks"></a>Uwagi  
 Kursor zostanie automatycznie umieszczony rachunku przycisku, a ich tematyka domyślnie. Jeśli kursor znajduje się zbyt duży dla przycisku, zostaną przycięte po obu stronach. Możesz wybrać inne opcje wyrównania, w tym następujące:  
  
- BS_TOP  
  
- BS_LEFT  
  
- BS_RIGHT  
  
- BS_CENTER  
  
- BS_BOTTOM  
  
- BS_VCENTER  
  
 W odróżnieniu od [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), która używa czterech map bitowych na przycisku `SetCursor` używa tylko kursor na przycisku. Po naciśnięciu przycisku, aby przenieść w dół, a po prawej stronie pojawi się kursor.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]  
  
##  <a name="setdropdownstate"></a>  CButton::SetDropDownState  
 Ustawia stan listy rozwijanej bieżącego kontrolki przycisku podziału.  
  
```  
BOOL SetDropDownState(BOOL fDropDown);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *fDropDown*|Wartość TRUE, aby ustawić stan BST_DROPDOWNPUSHED; w przeciwnym razie wartość FALSE.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Kontrolka przycisku podziału ma styl BS_SPLITBUTTON lub BS_DEFSPLITBUTTON i składa się z przycisku i strzałkę listy rozwijanej, po jego prawej stronie. Aby uzyskać więcej informacji, zobacz [style przycisku](/windows/desktop/Controls/button-styles). Zazwyczaj stan listy rozwijanej jest ustawiony, kiedy użytkownik kliknie strzałkę listy rozwijanej. Aby programowo ustawić stan listy rozwijanej kontrolki, należy użyć tej metody. Strzałki listy rozwijanej jest rysowana przyciemnione do wskazywania stanu.  
  
 Ta metoda wysyła [BCM_SETDROPDOWNSTATE](/windows/desktop/Controls/bcm-setdropdownstate) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną, *m_splitButton*, która jest używana do uzyskania programowego dostępu formant przycisku podziału. Ta zmienna jest używana w następującym przykładzie.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu ustawia stan formantu przycisku podziału, aby wskazać, że spoczywa strzałki listy rozwijanej.  
  
 [!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]  
  
##  <a name="setelevationrequired"></a>  CButton::SetElevationRequired  
 Ustawia stan bieżącej kontrolki przycisk umożliwia `elevation required`, który jest niezbędny dla formantu, aby wyświetlić ikonę z podwyższonym poziomem uprawnień zabezpieczeń.  
  
```  
BOOL SetElevationRequired(BOOL fElevationRequired);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *fElevationRequired*|Wartość true, zestaw `elevation required` stanu; w przeciwnym razie wartość FALSE.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli formant łącza przycisk lub polecenie wymaga uprawnień zabezpieczeń z podwyższonym poziomem uprawnień do wykonania akcji, ustaw kontrolkę `elevation required` stanu. Następnie Windows wyświetla ikona tarczy kontroli konta użytkownika (UAC) w kontrolce. Aby uzyskać więcej informacji, zobacz "Kontrola konta użytkownika" w [MSDN](http://go.microsoft.com/fwlink/p/?linkid=18507).  
  
 Ta metoda wysyła [BCM_SETSHIELD](/windows/desktop/Controls/bcm-setshield) komunikat, który jest opisany w zestawie Windows SDK.  
  
##  <a name="seticon"></a>  CButton::SetIcon  
 Wywołaj tę funkcję elementu członkowskiego, aby skojarzyć ikonę Nowy przycisk.  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>Parametry  
 *hIcon*  
 Uchwyt ikony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Uchwyt ikony była poprzednio skojarzona z przyciskiem.  
  
### <a name="remarks"></a>Uwagi  
 Ikona zostaną automatycznie umieszczone rachunku przycisku, a ich tematyka domyślnie. Jeśli ikona jest zbyt duży dla przycisku, zostaną przycięte po obu stronach. Możesz wybrać inne opcje wyrównania, w tym następujące:  
  
- BS_TOP  
  
- BS_LEFT  
  
- BS_RIGHT  
  
- BS_CENTER  
  
- BS_BOTTOM  
  
- BS_VCENTER  
  
 W odróżnieniu od [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), cztery map bitowych na przycisku, który używa `SetIcon` używa tylko jedną ikonę na przycisku. Po naciśnięciu przycisku, pojawi się ikona Przenieś w dół, a po prawej stronie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]  
  
##  <a name="setimagelist"></a>  CButton::SetImageList  
 Wywołanie tej metody do ustawiania listy obrazu `CButton` obiektu.  
  
```  
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```  
  
### <a name="parameters"></a>Parametry  
 *pbuttonImagelist*  
 Wskaźnik do nowej listy obrazów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcjonalność komunikat BCM_SETIMAGELIST zgodnie z opisem w [przyciski](https://msdn.microsoft.com/library/windows/desktop/bb775943) część zestawu Windows SDK.  
  
##  <a name="setnote"></a>  CButton::SetNote  
 Ustawia tekst notatki dla kontrolki linku bieżącego polecenia.  
  
```  
BOOL SetNote(LPCTSTR lpszNote);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *lpszNote*|Wskaźnik do ciągu Unicode, który jest ustawiony jako tekstu Uwaga dla kontrolki linku polecenia.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody tylko w przypadku którego styl przycisku jest BS_COMMANDLINK lub BS_DEFCOMMANDLINK kontrolki.  
  
 Ta metoda wysyła [BCM_SETNOTE](/windows/desktop/Controls/bcm-setnote) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną, *m_cmdLink*, która jest używana do uzyskania programowego dostępu formant łącza polecenia. Ta zmienna jest używana w następującym przykładzie.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu ustawia tekst notatki dla kontrolki linku polecenia.  
  
 [!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]  
  
##  <a name="setsplitglyph"></a>  CButton::SetSplitGlyph  
 Kojarzy określonego symbolu z bieżącym kontrolki przycisku podziału.  
  
```  
BOOL SetSplitGlyph(TCHAR chGlyph);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *chGlyph*|Znak, który określa symbol do użycia jako strzałki listy rozwijanej przycisku podziału.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Metoda ta jest przydatna tylko w przypadku formantów, które mają styl przycisku BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.  
  
 Glif jest fizyczna reprezentacja znaku w określonej czcionki. *ChGlyph* parametru nie jest używana jako symbol, ale zamiast tego jest używany do wybierania glif z zestawu symboli zdefiniowanych w systemie. Domyślnego symbolu strzałki listy rozwijanej jest określona przez znak '6' i przypomina znak Unicode TRÓJKĄT czarny dół WSKAZUJE (U + 25BC).  
  
 Ta metoda inicjuje `mask` członkiem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktury z flagą BCSIF_GLYPH i `himlGlyph` element członkowski o *chGlyph* parametru, a następnie wysyła go struktury w [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) komunikat, który jest opisany w zestawie Windows SDK.  
  
##  <a name="setsplitimagelist"></a>  CButton::SetSplitImageList  
 Kojarzy [listy obrazów](../../mfc/reference/cimagelist-class.md) z kontrolą bieżącą przycisku podziału.  
  
```  
BOOL SetSplitImageList(CImageList* pSplitImageList);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *pSplitImageList*|Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiekt można przypisać do bieżącego kontrolki przycisku podziału.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody tylko w przypadku którego styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON kontrolki.  
  
 Ta metoda inicjuje `mask` członkiem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktury z flagą BCSIF_IMAGE i `himlGlyph` element członkowski o *pSplitImageList* parametru, a następnie wysyła tej struktury w [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) komunikat, który jest opisany w zestawie Windows SDK.  
  
##  <a name="setsplitinfo"></a>  CButton::SetSplitInfo  
 Określa parametry, które określają, jak Windows pobiera bieżący formant przycisku podziału.  
  
```  
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *pInfo*|Wskaźnik do [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) strukturę, która definiuje bieżącego kontrolki przycisku podziału.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody tylko w przypadku którego styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON kontrolki.  
  
 Ta metoda wysyła [BCM_SETSPLITINFO](/windows/desktop/Controls/bcm-setsplitinfo) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną, `m_splitButton`, która jest używana do uzyskania programowego dostępu formant przycisku podziału.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu zmienia glif, który jest używany dla strzałkę listy rozwijanej przycisku podziału. Przykład glif skierowany trójkąt dla domyślnego symbolu trójkąt wskazująca w dół. Symbol, który jest wyświetlany jest zależna od znaku, który określisz w `himlGlyph` członkiem `BUTTON_SPLITINFO` struktury. Symbol trójkątem wskazującym w dół jest określona przez znak "6"i symbol trójkąt skierowany jest określona przez znak "5". Porównanie, można znaleźć w artykule wygodna metoda, [CButton::SetSplitGlyph](#setsplitglyph).  
  
 [!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]  
  
##  <a name="setsplitsize"></a>  CButton::SetSplitSize  
 Ustawia prostokąt otaczający składnika listy rozwijanej bieżącego kontrolki przycisku podziału.  
  
```  
BOOL SetSplitSize(LPSIZE pSize);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *pSize*|Wskaźnik do [rozmiar](https://msdn.microsoft.com/library/windows/desktop/dd145106) strukturę, która opisuje prostokąt otaczający.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody tylko w przypadku którego styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON kontrolki.  
  
 Po rozwinięciu formant przycisku podziału umożliwia wyświetlanie składnika listy rozwijanej, takiego jak kontrolka listy lub kontroli pagera. Ta metoda określa rozmiar prostokąt otaczający, który zawiera składnik listy rozwijanej.  
  
 Ta metoda inicjuje `mask` członkiem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktury z flagą BCSIF_SIZE i `size` element członkowski o *pSize* parametru, a następnie wysyła, które struktury w [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną, `m_splitButton`, która jest używana do uzyskania programowego dostępu formant przycisku podziału. Ta zmienna jest używana w następującym przykładzie.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu podwaja się rozmiar strzałki listy rozwijanej przycisku podziału.  
  
 [!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]  
  
##  <a name="setsplitstyle"></a>  CButton::SetSplitStyle  
 Ustawia styl bieżący formant przycisku podziału.  
  
```  
BOOL SetSplitStyle(UINT uSplitStyle);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *uSplitStyle*|Bitowa kombinacja style przycisku podziału. Aby uzyskać więcej informacji, zobacz `uSplitStyle` członkiem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktury.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody tylko w przypadku którego styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON kontrolki.  
  
 Style przycisku podziału Określ wyrównanie, współczynnik proporcji i w postaci graficznej za pomocą którego Windows rysuje ikonę przycisku podziału. Aby uzyskać więcej informacji, zobacz `uSplitStyle` członkiem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktury.  
  
 Ta metoda inicjuje `mask` członkiem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktury z flagą BCSIF_STYLE i `uSplitStyle` element członkowski o *uSplitStyle* parametru, a następnie wysyła go struktury w [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną, `m_splitButton`, która jest używana do uzyskania programowego dostępu formant przycisku podziału.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu ustawia styl strzałki listy rozwijanej przycisku podziału. Styl BCSS_ALIGNLEFT Wyświetla strzałkę po lewej stronie przycisku, a styl BCSS_STRETCH zachowuje strzałkę listy rozwijanej proporcje podczas zmiany rozmiaru przycisku.  
  
 [!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]  
  
##  <a name="setstate"></a>  CButton::SetState  
 Określa, czy formant przycisku zostanie wyróżniona, czy nie.  
  
```  
void SetState(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Parametry  
 *bHighlight*  
 Określa, czy ma być wyróżniony przycisku. Wartość różną od zera wyróżnia przycisku; wartość 0 powoduje wyłączenie wszelkich wyróżniania.  
  
### <a name="remarks"></a>Uwagi  
 Wyróżnianie ma wpływ na zewnątrz kontrolki przycisku. Nie ma wpływu na stan wyboru pole wyboru lub przycisku radiowego.  
  
 Kontrolka przycisku automatycznie zostanie wyróżniona, gdy użytkownik kliknie i przechowuje lewego przycisku myszy. Wyróżnianie jest usuwany, gdy użytkownik zwolni przycisk myszy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]  
  
##  <a name="settextmargin"></a>  CButton::SetTextMargin  
 Wywołanie tej metody można ustawić na marginesie tekstu `CButton` obiektu.  
  
```  
BOOL SetTextMargin(RECT* pmargin);
```  
  
### <a name="parameters"></a>Parametry  
 *pmargin*  
 Wskaźnik do nowego tekstu marginesu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcjonalność komunikat BCM_SETTEXTMARGIN zgodnie z opisem w [przyciski](https://msdn.microsoft.com/library/windows/desktop/bb775943) część zestawu Windows SDK.  
  
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
