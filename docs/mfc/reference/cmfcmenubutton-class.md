---
title: Klasa CMFCMenuButton
ms.date: 07/15/2019
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
- AFXMENUBUTTON/CMFCMenuButton::m_bDefaultClick
helpviewer_keywords:
- CMFCMenuButton [MFC], CMFCMenuButton
- CMFCMenuButton [MFC], PreTranslateMessage
- CMFCMenuButton [MFC], SizeToContent
- CMFCMenuButton [MFC], m_bOSMenu
- CMFCMenuButton [MFC], m_bRightArrow
- CMFCMenuButton [MFC], m_bStayPressed
- CMFCMenuButton [MFC], m_hMenu
- CMFCMenuButton [MFC], m_nMenuResult
- CMFCMenuButton [MFC], m_bDefaultClick
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
ms.openlocfilehash: 929fc1c8166f249fe3babc724b2c0bcd9cb99676
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369681"
---
# <a name="cmfcmenubutton-class"></a>Klasa CMFCMenuButton

Przycisk wyświetla menu podręczne i raportuje wybór menu użytkownika.

## <a name="syntax"></a>Składnia

```
class CMFCMenuButton : public CMFCButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCMenuButton::CMFCMenuButton](#cmfcmenubutton)|Konstruuje `CMFCMenuButton` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|Wywoływane przez strukturę do tłumaczenia komunikatów okna przed ich wysłaniem. (Przesłania `CMFCButton::PreTranslateMessage`).|
|[CMFCMenuButton::SizeToContent](#sizetocontent)|Zmienia rozmiar przycisku w zależności od jego tekstu i rozmiaru obrazu.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|Określa, czy ma być wyświetlane domyślne menu podręczne systemu, czy też użycie [programu CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).|
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|Określa, czy menu podręczne będzie wyświetlane pod spodem, czy po prawej stronie przycisku.|
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|Określa, czy przycisk menu zmienia swój stan po tym, jak użytkownik zwolni przycisk.|
|[CMFCMenuButton::m_hMenu](#m_hmenu)|Uchwyt do dołączonego menu systemu Windows.|
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|Identyfikator wskazujący, który element użytkownik wybrał z menu podręcznego.|
|[CMFCMenuButton::m_bDefaultClick](#m_bdefaultclick)| Zezwalaj na domyślne przetwarzanie tekstu/obrazu przycisku.|

## <a name="remarks"></a>Uwagi

Klasa `CMFCMenuButton` jest pochodną [CMFCButton Klasa,](../../mfc/reference/cmfcbutton-class.md) która jest z kolei pochodną [CButton Class](../../mfc/reference/cbutton-class.md). W związku z `CMFCMenuButton` tym można użyć w kodzie w taki sam sposób, jaki można użyć `CButton`.

Podczas tworzenia `CMFCMenuButton`, należy przekazać w dojście do skojarzonego menu podręcznego. Następnie zadzwoń do `CMFCMenuButton::SizeToContent`funkcji . `CMFCMenuButton::SizeToContent`sprawdza, czy rozmiar przycisku jest wystarczający, aby uwzględnić strzałkę, która wskazuje lokalizację, w której pojawi się wyskakujące okno - a mianowicie pod lub po prawej stronie przycisku.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak ustawić uchwyt menu dołączonego do przycisku, zmienić rozmiar przycisku zgodnie z jego tekstem i rozmiarem obrazu i ustawić menu podręczne, które jest wyświetlane przez platformę. Ten fragment kodu jest częścią [próbki Nowe formanty](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cbutton](../../mfc/reference/cbutton-class.md)

[Cmfcbutton](../../mfc/reference/cmfcbutton-class.md)

[CMFCMenuButton (CMFCMenuButton)](../../mfc/reference/cmfcmenubutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmenubutton.h

## <a name="cmfcmenubuttoncmfcmenubutton"></a><a name="cmfcmenubutton"></a>CMFCMenuButton::CMFCMenuButton

Tworzy nowy [obiekt CMFCMenuButton.](../../mfc/reference/cmfcmenubutton-class.md)

```
CMFCMenuButton();
```

## <a name="cmfcmenubuttonm_bosmenu"></a><a name="m_bosmenu"></a>CMFCMenuButton::m_bOSMenu

Zmienna elementu członkowskiego logicznego, która wskazuje, które menu podręczne wyświetla framework.

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>Uwagi

Jeśli `m_bOSMenu` jest true, struktura wywołuje `TrackPopupMenu` dziedziczoną metodę dla tego obiektu. W przeciwnym razie struktura wywołuje [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).

## <a name="cmfcmenubuttonm_brightarrow"></a><a name="m_brightarrow"></a>CMFCMenuButton::m_bRightArrow

Zmienna elementu członkowskiego logicznego wskazująca lokalizację menu podręcznego.

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>Uwagi

Gdy użytkownik naciśnie przycisk menu, aplikacja wyświetla wyskakujące menu. Struktura wyświetli menu podręczne pod przyciskiem lub po prawej stronie przycisku. Przycisk ma również małą strzałkę, która wskazuje, gdzie pojawi się wyskakujące menu. Jeśli `m_bRightArrow` jest true, ramach wyświetla menu podręczne po prawej stronie przycisku. W przeciwnym razie wyświetla menu podręczne pod przyciskiem.

## <a name="cmfcmenubuttonm_bstaypressed"></a><a name="m_bstaypressed"></a>CMFCMenuButton::m_bStayPressed

Zmienna logicznego elementu członkowskiego wskazująca, czy przycisk menu jest wciśnięty, gdy użytkownik dokonuje wyboru z wyskakującego menu.

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>Uwagi

Jeśli `m_bStayPressed` element członkowski ma wartość FAŁSZ, przycisk menu nie zostanie naciśnięty, gdy użyje kliknięcia przycisku. W takim przypadku w ramach wyświetla tylko menu podręczne.

Jeśli `m_bStayPressed` element członkowski ma wartość PRAWDA, przycisk menu zostanie naciśnięty po kliknięciu przycisku przez użytkownika. Pozostaje wciśnięty, dopóki użytkownik nie zamknie wyskakującego menu, dokonując wyboru lub anulując.

## <a name="cmfcmenubuttonm_hmenu"></a><a name="m_hmenu"></a>CMFCMenuButton::m_hMenu

Uchwyt do dołączonego menu.

```
HMENU m_hMenu;
```

### <a name="remarks"></a>Uwagi

Struktura wyświetla menu wskazane przez tę zmienną członkowną, gdy użytkownik kliknie przycisk menu.

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult

Liczba całkowita wskazująca, który element użytkownik wybierze z menu podręcznego.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Uwagi

Wartość tej zmiennej członkowskiej wynosi zero, jeśli użytkownik anuluje menu bez dokonywania wyboru lub w przypadku wystąpienia błędu.

## <a name="cmfcmenubuttonm_bdefaultclick"></a><a name="m_bdefaultclick"></a>CMFCMenuButton::m_bDefaultClick

Umożliwia domyślne przetwarzanie tekstu lub obrazów na przycisku.

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>Uwagi

Ustawienie m_bDefaultClick na false powoduje, że przycisk pokazuje menu po kliknięciu dowolnego miejsca na przycisku.

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult

Liczba całkowita wskazująca, który element użytkownik wybierze z menu podręcznego.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubuttonpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCMenuButton::PreTranslateMessage

Wywoływane przez strukturę do tłumaczenia komunikatów okna przed ich wysłaniem.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
[w] Wskazuje strukturę [MSG,](/windows/win32/api/winuser/ns-winuser-msg) która zawiera komunikat do przetworzenia.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wiadomość została przetłumaczona i nie powinny być wysyłane; 0, jeśli wiadomość nie została przetłumaczona i powinna zostać wysłana.

### <a name="remarks"></a>Uwagi

## <a name="cmfcmenubuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCMenuButton::SizeToContent

Zmienia rozmiar przycisku w zależności od jego rozmiaru tekstu i rozmiaru obrazu.

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>Parametry

*bCalcOnly*<br/>
[w] Parametr logiczny wskazujący, czy ta metoda ma rozmiar przycisku .

### <a name="return-value"></a>Wartość zwracana

Obiekt [CSize,](../../atl-mfc-shared/reference/csize-class.md) który określa nowy rozmiar przycisku.

### <a name="remarks"></a>Uwagi

Jeśli wywołasz tę funkcję i *bCalcOnly* jest TRUE, `SizeToContent` obliczy tylko nowy rozmiar przycisku.

Nowy rozmiar przycisku jest obliczany w celu dopasowania do tekstu przycisku, obrazu i strzałki. Struktura dodaje również wstępnie zdefiniowane marginesy 10 pikseli dla krawędzi poziomej i 5 pikseli dla pionowej krawędzi.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCButton](../../mfc/reference/cmfcbutton-class.md)
