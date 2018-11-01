---
title: Klasa CMFCMenuButton
ms.date: 11/04/2016
f1_keywords:
- CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::PreTranslateMessage
- AFXMENUBUTTON/CMFCMenuButton::SizeToContent
- AFXMENUBUTTON/CMFCMenuButton::m_bOSMenu
- AFXMENUBUTTON/CMFCMenuButton::m_bRightArrow
- AFXMENUBUTTON/CMFCMenuButton::m_bStayPressed
- AFXMENUBUTTON/CMFCMenuButton::m_hMenu
- AFXMENUBUTTON/CMFCMenuButton::m_nMenuResult
helpviewer_keywords:
- CMFCMenuButton [MFC], CMFCMenuButton
- CMFCMenuButton [MFC], PreTranslateMessage
- CMFCMenuButton [MFC], SizeToContent
- CMFCMenuButton [MFC], m_bOSMenu
- CMFCMenuButton [MFC], m_bRightArrow
- CMFCMenuButton [MFC], m_bStayPressed
- CMFCMenuButton [MFC], m_hMenu
- CMFCMenuButton [MFC], m_nMenuResult
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
ms.openlocfilehash: b2f7b2e5a94329d0d5b0079aaae6eff98ac03911
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577982"
---
# <a name="cmfcmenubutton-class"></a>Klasa CMFCMenuButton

Przycisk, który wyświetla wyskakujące menu, a także sprawozdania wybory menu użytkownika.

## <a name="syntax"></a>Składnia

```
class CMFCMenuButton : public CMFCButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCMenuButton::CMFCMenuButton](#cmfcmenubutton)|Konstruuje `CMFCMenuButton` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|Metoda wywoływana przez platformę, by tłumaczenie okna komunikatów przed ich wysłaniem. (Przesłania `CMFCButton::PreTranslateMessage`).|
|[CMFCMenuButton::SizeToContent](#sizetocontent)|Zmienia rozmiar przycisku zgodnie z rozmiarem tekstu i obrazów.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|Określa, czy, aby wyświetlić menu podręcznego systemu domyślne lub użyć [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).|
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|Określa, czy menu podręcznym pojawi się poniżej lub po prawej stronie przycisku.|
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|Określa, czy przycisk menu zmienia jego stan po użytkownik zwolni przycisk.|
|[CMFCMenuButton::m_hMenu](#m_hmenu)|Dojście do menu dołączonego Windows.|
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|Identyfikator, który wskazuje element, który użytkownik zaznaczył w menu podręcznym.|

## <a name="remarks"></a>Uwagi

`CMFCMenuButton` Klasa pochodzi od [klasa CMFCButton](../../mfc/reference/cmfcbutton-class.md) który z kolei pochodzi od [klasa CButton](../../mfc/reference/cbutton-class.md). W związku z tym, można użyć `CMFCMenuButton` w kodzie ten sam sposób, należy użyć `CButton`.

Po utworzeniu `CMFCMenuButton`, trzeba przekazać w dojścia do skojarzonego menu podręcznego. Następnie wywołaj funkcję `CMFCMenuButton::SizeToContent`. `CMFCMenuButton::SizeToContent` sprawdza, czy rozmiar przycisku jest wystarczająca uwzględnić strzałki wskazujące miejsce, gdzie okno podręczne pojawią się — to znaczy, poniżej lub po prawej stronie przycisku.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak ustawić uchwyt menu dołączone do przycisku, Zmień rozmiar przycisku zgodnie z rozmiarem tekstu i obrazów i ustawienie menu podręcznego, który jest wyświetlany przez szablon. Ten fragment kodu jest częścią [przykładowe nowych formantów](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmenubutton.h

##  <a name="cmfcmenubutton"></a>  CMFCMenuButton::CMFCMenuButton

Tworzy nowy [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md) obiektu.

```
CMFCMenuButton();
```

##  <a name="m_bosmenu"></a>  CMFCMenuButton::m_bOSMenu

Wyświetla platformę zmienną członkowską logiczna, która wskazuje, które menu podręcznego.

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>Uwagi

Jeśli `m_bOSMenu` ma wartość PRAWDA, struktura wywołuje dziedziczonego `TrackPopupMenu` metody dla tego obiektu. W przeciwnym razie struktura wywołuje [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).

##  <a name="m_brightarrow"></a>  CMFCMenuButton::m_bRightArrow

Zmienna członka z wartość logiczna, która określa lokalizację, w menu podręcznym.

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>Uwagi

Gdy użytkownik naciśnie przycisk menu, aplikacja pokazuje menu podręczne. Struktura wyświetli menu podręcznego pod przyciskiem lub po prawej stronie przycisku. Ten przycisk ma również małą strzałkę, która wskazuje, gdzie pojawią się w menu podręcznym. Jeśli `m_bRightArrow` ma wartość PRAWDA, struktura wyświetla wyskakujące menu po prawej stronie przycisku. W przeciwnym razie wyświetla wyskakujące menu, po kliknięciu przycisku.

##  <a name="m_bstaypressed"></a>  CMFCMenuButton::m_bStayPressed

Zmienną członkowską logiczną, wskazującą, czy pojawi się przycisk menu naciśnięciu, gdy użytkownik dokona wybór z menu podręcznego.

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>Uwagi

Jeśli `m_bStayPressed` element członkowski ma wartość FAŁSZ, przycisk menu stają się nienaciśnięty po użytkownik klika przycisk. W tym przypadku ramach Wyświetla menu podręczne.

Jeśli `m_bStayPressed` element członkowski ma wartość PRAWDA, staje się naciśnięty przycisk menu, gdy użytkownik kliknie przycisk. Pozostaje on po naciśnięciu aż po użytkownik zamknie menu podręcznego, dokonując wyboru lub anulowanie.

##  <a name="m_hmenu"></a>  CMFCMenuButton::m_hMenu

Dojście do menu dołączone.

```
HMENU m_hMenu;
```

### <a name="remarks"></a>Uwagi

Struktura pojawi się menu, wskazane przez tę zmienną elementu członkowskiego, gdy użytkownik kliknie przycisk menu.

##  <a name="m_nmenuresult"></a>  CMFCMenuButton::m_nMenuResult

Liczba całkowita, która wskazuje, który element użytkownik wybiera z menu podręcznego.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Uwagi

Wartość tej zmiennej elementu członkowskiego wynosi zero, jeśli użytkownik anuluje menu bez dokonywania wyboru lub w przypadku wystąpienia błędu.

##  <a name="pretranslatemessage"></a>  CMFCMenuButton::PreTranslateMessage

Metoda wywoływana przez platformę, by tłumaczenie okna komunikatów przed ich wysłaniem.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
[in] Wskazuje [MSG](../../mfc/reference/msg-structure1.md) strukturę, która zawiera komunikat, który ma przetwarzać.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli komunikat został przetłumaczony i nie powinny być wysyłane; 0, jeśli wiadomość nie została przekonwertowana i powinny być wysyłane.

### <a name="remarks"></a>Uwagi

##  <a name="sizetocontent"></a>  CMFCMenuButton::SizeToContent

Zmienia rozmiar przycisku zgodnie z jego rozmiar tekstu i rozmiar obrazu.

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>Parametry

*bCalcOnly*<br/>
[in] Parametr logiczny, który wskazuje, czy ta metoda zmienia rozmiar przycisku.

### <a name="return-value"></a>Wartość zwracana

A [CSize](../../atl-mfc-shared/reference/csize-class.md) obiekt, który określa nowy rozmiar przycisku.

### <a name="remarks"></a>Uwagi

Jeśli wywołanie tej funkcji i *bCalcOnly* ma wartość PRAWDA, `SizeToContent` obliczy nowy rozmiar przycisku.

Nowy rozmiar przycisku jest obliczana do dopasowania tekstu przycisku, obrazu i strzałki. Struktura dodaje również wstępnie zdefiniowanych marginesy 10 pikseli dla poziomej krawędzi i 5 pikseli dla pionowej krawędzi.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCButton](../../mfc/reference/cmfcbutton-class.md)
