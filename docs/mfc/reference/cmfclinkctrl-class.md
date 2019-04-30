---
title: CMFCLinkCtrl Class
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
ms.openlocfilehash: 839448694cee17f5bc1a1e47f7c113026a1a4006
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346208"
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl Class

`CMFCLinkCtrl` Klasy Wyświetla przycisk jako hiperłącze i wywołuje cel łącza po kliknięciu przycisku.

## <a name="syntax"></a>Składnia

```
class CMFCLinkCtrl : public CMFCButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCLinkCtrl::SetURL](#seturl)|Wyświetla wybrany adres URL w postaci tekstu przycisku.|
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|Ustawia protokół niejawne (na przykład "http:") adresu URL.|
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|Zmienia rozmiar przycisku, które zawierają tekst przycisku lub mapy bitowej.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|Wywoływane przez platformę przed narysowaniem prostokąt fokusu przycisku.|

## <a name="remarks"></a>Uwagi

Po kliknięciu przycisku, który jest tworzony na podstawie `CMFCLinkCtrl` klasa, struktura przekazanie adresu URL przycisku jako parametr do `ShellExecute` metody. A następnie `ShellExecute` metoda zostanie otwarty obiekt docelowy adresu URL.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak ustawić rozmiar `CMFCLinkCtrl` obiektu i jak ustawić adres url i etykietka narzędzia w `CMFCLinkCtrl` obiektu. W tym przykładzie jest częścią [przykładowe nowych formantów](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxlinkctrl.h

##  <a name="ondrawfocusrect"></a>  CMFCLinkCtrl::OnDrawFocusRect

Wywoływane przez platformę przed narysowaniem prostokąt fokusu przycisku.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia.

*rectClient*<br/>
[in] Prostokąt, który granic kontrolki łącza.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę, jeśli chcesz użyć własnego kodu, aby narysować prostokąt fokusu na przycisku.

##  <a name="seturl"></a>  CMFCLinkCtrl::SetURL

Wyświetla wybrany adres URL w postaci tekstu przycisku.

```
void SetURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Parametry

*lpszURL*<br/>
[in] Tekst przycisku do wyświetlenia.

### <a name="remarks"></a>Uwagi

##  <a name="seturlprefix"></a>  CMFCLinkCtrl::SetURLPrefix

Ustawia protokół niejawne (na przykład "http:") adresu URL.

```
void SetURLPrefix(LPCTSTR lpszPrefix);
```

### <a name="parameters"></a>Parametry

*lpszPrefix*<br/>
[in] Prefiks Protokół adresu URL.

### <a name="remarks"></a>Uwagi

Użyj tej metody można ustawić prefiks adresu URL. Prefiks nie jest wyświetlany na powierzchni przycisku, ale służy do pomocy, przejdź do docelowego adresu URL.

##  <a name="sizetocontent"></a>  CMFCLinkCtrl::SizeToContent

Zmienia rozmiar przycisku, które zawierają tekst przycisku lub mapy bitowej.

```
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,
    BOOL bHCenter=FALSE);
```

### <a name="parameters"></a>Parametry

*bVCenter*<br/>
[in] Wartość TRUE, aby wyśrodkować przycisku tekstu i mapy bitowej w pionie między górą a dołem kontroli łącza. w przeciwnym razie wartość FALSE. Wartość domyślna to FALSE.

*bHCenter*<br/>
[in] Wartość TRUE, aby wyśrodkować przycisku tekstu i mapy bitowej w poziomie od lewej i prawej stronie kontroli łącza. w przeciwnym razie wartość FALSE. Wartość domyślna to FALSE.

### <a name="return-value"></a>Wartość zwracana

A [CSize](../../atl-mfc-shared/reference/csize-class.md) obiekt, który zawiera nowy rozmiar kontrolki łącza.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CLinkCtrl](../../mfc/reference/clinkctrl-class.md)<br/>
[Klasa CMFCButton](../../mfc/reference/cmfcbutton-class.md)
