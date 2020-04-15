---
title: Klasa CMFCLinkCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl::SetURL
- AFXLINKCTRL/CMFCLinkCtrl::SetURLPrefix
- AFXLINKCTRL/CMFCLinkCtrl::SizeToContent
- AFXLINKCTRL/CMFCLinkCtrl::OnDrawFocusRect
helpviewer_keywords:
- CMFCLinkCtrl [MFC], SetURL
- CMFCLinkCtrl [MFC], SetURLPrefix
- CMFCLinkCtrl [MFC], SizeToContent
- CMFCLinkCtrl [MFC], OnDrawFocusRect
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
ms.openlocfilehash: 1ef4e390d88f81d738d2ee18be6ba02843633011
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374403"
---
# <a name="cmfclinkctrl-class"></a>Klasa CMFCLinkCtrl

Klasa `CMFCLinkCtrl` wyświetla przycisk jako hiperłącze i wywołuje miejsce docelowe łącza po kliknięciu przycisku.

## <a name="syntax"></a>Składnia

```
class CMFCLinkCtrl : public CMFCButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCLinkCtrl::SetURL](#seturl)|Wyświetla określony adres URL jako tekst przycisku.|
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|Ustawia protokół niejawny (na przykład "http:") adresu URL.|
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|Rozmiar przycisku powoduje, że jest on zawierał tekst lub mapę bitową.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|Wywoływana przez strukturę przed prostokątfot fokus przycisku jest rysowana.|

## <a name="remarks"></a>Uwagi

Po kliknięciu przycisku, który `CMFCLinkCtrl` pochodzi z klasy, ramach przekazuje adres URL `ShellExecute` przycisku jako parametr do metody. Następnie `ShellExecute` metoda otwiera miejsce docelowe adresu URL.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCLinkCtrl` ustawić rozmiar obiektu i jak ustawić adres `CMFCLinkCtrl` URL i etykietkę narzędzia w obiekcie. W tym przykładzie jest częścią [new controls próbki](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cbutton](../../mfc/reference/cbutton-class.md)

[Cmfcbutton](../../mfc/reference/cmfcbutton-class.md)

[CMFCLinkCtrl (CMFCLinkCtrl)](../../mfc/reference/cmfclinkctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxlinkctrl.h

## <a name="cmfclinkctrlondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCLinkCtrl::OnDrawFocusRect

Wywoływana przez strukturę przed prostokątfot fokus przycisku jest rysowana.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*rectClient*<br/>
[w] Prostokąt, który ogranicza formant łącza.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, jeśli chcesz użyć własnego kodu, aby narysować prostokąt fokusu przycisku.

## <a name="cmfclinkctrlseturl"></a><a name="seturl"></a>CMFCLinkCtrl::SetURL

Wyświetla określony adres URL jako tekst przycisku.

```
void SetURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Parametry

*lpszURL*<br/>
[w] Tekst przycisku do wyświetlenia.

### <a name="remarks"></a>Uwagi

## <a name="cmfclinkctrlseturlprefix"></a><a name="seturlprefix"></a>CMFCLinkCtrl::SetURLPrefix

Ustawia protokół niejawny (na przykład "http:") adresu URL.

```
void SetURLPrefix(LPCTSTR lpszPrefix);
```

### <a name="parameters"></a>Parametry

*lpszPrefix*<br/>
[w] Prefiks protokołu URL.

### <a name="remarks"></a>Uwagi

Ta metoda służy do ustawiania prefiksu adresu URL. Prefiks nie jest wyświetlany na twarzy przycisku, ale można go użyć, aby ułatwić przeglądanie adresu docelowego adresu URL.

## <a name="cmfclinkctrlsizetocontent"></a><a name="sizetocontent"></a>CMFCLinkCtrl::SizeToContent

Rozmiar przycisku powoduje, że jest on zawierał tekst lub mapę bitową.

```
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,
    BOOL bHCenter=FALSE);
```

### <a name="parameters"></a>Parametry

*bVCentrer*<br/>
[w] PRAWDA, aby wyśrodkować tekst przycisku i mapę bitową w pionie między górną i dolną częścią formantu łącza; w przeciwnym razie FALSE. Wartością domyślną jest FAŁSZ.

*bHCentra*<br/>
[w] PRAWDA, aby wyśrodkować tekst przycisku i mapę bitową w poziomie między lewą i prawą stronami formantu łącza; w przeciwnym razie FALSE. Wartością domyślną jest FAŁSZ.

### <a name="return-value"></a>Wartość zwracana

Obiekt [CSize,](../../atl-mfc-shared/reference/csize-class.md) który zawiera nowy rozmiar formantu łącza.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CLinkCtrl](../../mfc/reference/clinkctrl-class.md)<br/>
[Klasa CMFCButton](../../mfc/reference/cmfcbutton-class.md)
