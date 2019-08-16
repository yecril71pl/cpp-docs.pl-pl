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
ms.openlocfilehash: d7c23cbda0a5af4dc3fa6b2d9f59497acc9bf5ff
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505209"
---
# <a name="cmfcmenubutton-class"></a>Klasa CMFCMenuButton

Przycisk, który wyświetla menu podręczne i raporty w wybranych menu użytkownika.

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
|[CMFCMenuButton::P reTranslateMessage](#pretranslatemessage)|Wywoływane przez platformę w celu tłumaczenia komunikatów okna przed ich wysłaniem. (Przesłania `CMFCButton::PreTranslateMessage`).|
|[CMFCMenuButton::SizeToContent](#sizetocontent)|Zmienia rozmiar przycisku w zależności od jego tekstu i rozmiaru obrazu.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|Określa, czy ma być wyświetlane domyślne menu wyskakujące systemu, czy użyć [CContextMenuManager:: TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).|
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|Określa, czy menu podręczne pojawi się poniżej lub z prawej strony przycisku.|
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|Określa, czy przycisk menu zmienia swój stan po zwolnieniu przycisku przez użytkownika.|
|[CMFCMenuButton::m_hMenu](#m_hmenu)|Uchwyt do dołączonego menu systemu Windows.|
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|Identyfikator wskazujący, który element wybrany przez użytkownika z menu podręcznego.|
|[CMFCMenuButton::m_bDefaultClick](#m_bdefaultclick)| Zezwalaj na domyślne (w przypadku przetwarzania tekstu/obrazu przycisku).|

## <a name="remarks"></a>Uwagi

Klasa pochodzi od klasy [CMFCButton](../../mfc/reference/cmfcbutton-class.md) , która z kolei pochodzi od [klasy CButton.](../../mfc/reference/cbutton-class.md) `CMFCMenuButton` W związku z tym możesz `CMFCMenuButton` użyć w kodzie w taki sam sposób jak w `CButton`przypadku użycia.

Podczas tworzenia `CMFCMenuButton`, należy przekazać uchwyt do powiązanego menu podręcznego. Następnie wywołaj funkcję `CMFCMenuButton::SizeToContent`. `CMFCMenuButton::SizeToContent`sprawdza, czy rozmiar przycisku jest wystarczający do uwzględnienia strzałki wskazującej lokalizację, w której zostanie wyświetlone okno podręczne — mianowicie, poniżej lub po prawej stronie przycisku.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak ustawić uchwyt menu dołączonego do przycisku, zmienić rozmiar przycisku w zależności od jego tekstu i rozmiaru obrazu, a następnie ustawić menu podręczne, które jest wyświetlane przez platformę. Ten fragment kodu jest częścią [nowych formantów przykładowych](../../overview/visual-cpp-samples.md).

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

**Nagłówek:** afxmenubutton. h

##  <a name="cmfcmenubutton"></a>CMFCMenuButton::CMFCMenuButton

Tworzy nowy obiekt [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md) .

```
CMFCMenuButton();
```

##  <a name="m_bosmenu"></a>CMFCMenuButton::m_bOSMenu

Zmienna elementu członkowskiego Boolean, która wskazuje, który menu wyskakujące jest wyświetlane przez strukturę.

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>Uwagi

Jeśli `m_bOSMenu` ma wartość true, struktura wywołuje metodę dziedziczoną `TrackPopupMenu` dla tego obiektu. W przeciwnym razie struktura wywołuje [CContextMenuManager:: TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).

##  <a name="m_brightarrow"></a>CMFCMenuButton::m_bRightArrow

Zmienna elementu członkowskiego Boolean, która wskazuje lokalizację menu podręcznego.

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>Uwagi

Gdy użytkownik naciśnie przycisk menu, aplikacja wyświetli menu podręczne. W strukturze zostanie wyświetlone menu podręczne pod przyciskiem lub po prawej stronie przycisku. Przycisk ma również małą strzałkę wskazującą, gdzie pojawi się menu wyskakujące. Jeśli `m_bRightArrow` ma wartość true, struktura wyświetla menu podręczne z prawej strony przycisku. W przeciwnym razie wyświetla menu podręczne pod przyciskiem.

##  <a name="m_bstaypressed"></a>CMFCMenuButton::m_bStayPressed

Zmienna elementu członkowskiego Boolean wskazująca, czy przycisk menu pojawia się, gdy użytkownik dokonuje wyboru z menu podręcznego.

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>Uwagi

`m_bStayPressed` Jeśli element członkowski ma wartość false, przycisk menu nie zostanie wciśnięty po kliknięciu przycisku. W takim przypadku struktura wyświetla tylko menu podręczne.

`m_bStayPressed` Jeśli element członkowski ma wartość true, przycisk menu zostanie naciśnięty, gdy użytkownik kliknie przycisk. Pozostaje wciśnięty do momentu zamknięcia przez użytkownika menu podręcznego przez wybranie lub anulowanie.

##  <a name="m_hmenu"></a>  CMFCMenuButton::m_hMenu

Uchwyt do dołączonego menu.

```
HMENU m_hMenu;
```

### <a name="remarks"></a>Uwagi

Struktura wyświetla menu wskazywane przez tę zmienną elementu członkowskiego, gdy użytkownik kliknie przycisk menu.

##  <a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult

Liczba całkowita wskazująca, który element wybrany przez użytkownika z menu podręcznego.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Uwagi

Wartość tej zmiennej składowej jest równa zero, jeśli użytkownik anuluje menu bez dokonania wyboru lub jeśli wystąpi błąd.

##  <a name="m_bdefaultclick"></a>CMFCMenuButton::m_bDefaultClick

Umożliwia domyślne przetwarzanie tekstu lub obrazów na przycisku.

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>Uwagi

Ustawienie m_bDefaultClick na false powoduje, że przycisk wyświetla menu po kliknięciu w dowolnym miejscu przycisku.

##  <a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult

Liczba całkowita wskazująca, który element wybrany przez użytkownika z menu podręcznego.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Uwagi

##  <a name="pretranslatemessage"></a>CMFCMenuButton::P reTranslateMessage

Wywoływane przez platformę w celu tłumaczenia komunikatów okna przed ich wysłaniem.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
podczas Wskazuje strukturę [komunikatów](/windows/win32/api/winuser/ns-winuser-msg) , która zawiera komunikat do przetworzenia.

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli wiadomość została przetłumaczona i nie powinna być wysyłana; 0, jeśli komunikat nie został przetłumaczony i powinien zostać wysłany.

### <a name="remarks"></a>Uwagi

##  <a name="sizetocontent"></a>CMFCMenuButton::SizeToContent

Zmienia rozmiar przycisku zgodnie z rozmiarem tekstu i rozmiarem obrazu.

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>Parametry

*bCalcOnly*<br/>
podczas Parametr logiczny, który wskazuje, czy ta metoda zmienia rozmiar przycisku.

### <a name="return-value"></a>Wartość zwracana

Obiekt [CSize](../../atl-mfc-shared/reference/csize-class.md) , który określa nowy rozmiar przycisku.

### <a name="remarks"></a>Uwagi

Jeśli wywołasz tę funkcję, a *bCalcOnly* ma wartość `SizeToContent` true, program obliczy tylko nowy rozmiar przycisku.

Nowy rozmiar przycisku jest obliczany w celu dopasowania do tekstu przycisku, obrazu i strzałki. Struktura dodaje również wstępnie zdefiniowane marginesy (10 pikseli) dla krawędzi poziomej i 5 pikseli dla krawędzi pionowej.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCButton](../../mfc/reference/cmfcbutton-class.md)
