---
title: Klasa CMFCDesktopAlertWnd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::Create
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetCaptionHeight
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetDialogSize
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetLastPos
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetTransparency
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::HasSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnBeforeShow
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnClickLinkButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnDraw
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::ProcessCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetTransparency
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWnd [MFC], Create
- CMFCDesktopAlertWnd [MFC], GetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], GetAnimationType
- CMFCDesktopAlertWnd [MFC], GetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], GetCaptionHeight
- CMFCDesktopAlertWnd [MFC], GetDialogSize
- CMFCDesktopAlertWnd [MFC], GetLastPos
- CMFCDesktopAlertWnd [MFC], GetTransparency
- CMFCDesktopAlertWnd [MFC], HasSmallCaption
- CMFCDesktopAlertWnd [MFC], OnBeforeShow
- CMFCDesktopAlertWnd [MFC], OnClickLinkButton
- CMFCDesktopAlertWnd [MFC], OnCommand
- CMFCDesktopAlertWnd [MFC], OnDraw
- CMFCDesktopAlertWnd [MFC], ProcessCommand
- CMFCDesktopAlertWnd [MFC], SetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], SetAnimationType
- CMFCDesktopAlertWnd [MFC], SetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], SetSmallCaption
- CMFCDesktopAlertWnd [MFC], SetTransparency
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 728aa39341eb808b2bae178e0a419ec3a2ab46e1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432441"
---
# <a name="cmfcdesktopalertwnd-class"></a>Klasa CMFCDesktopAlertWnd

`CMFCDesktopAlertWnd` Klasa implementuje funkcje niemodalnego okna dialogowego który jest wyświetlany na ekranie, aby poinformować użytkownika o zdarzeniu.

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.
## <a name="syntax"></a>Składnia

```
class CMFCDesktopAlertWnd : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDesktopAlertWnd::Create](#create)|Tworzy i inicjuje okno alertu pulpitu.|
|[CMFCDesktopAlertWnd::GetAnimationSpeed](#getanimationspeed)|Zwraca szybkość animacji.|
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|Zwraca typ animacji.|
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|Zwraca wartość limitu czasu automatycznego zamykania.|
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|Zwraca wysokość podpis.|
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|Zwraca ostatni prawidłowy alert okien pulpitu na ekranie.|
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|Zwraca poziom przezroczystości.|
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|Określa, czy okno alertu pulpitu jest wyświetlana przy użyciu małych podpis.|
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|Wywoływane przez platformę, gdy użytkownik kliknie przycisk link znajdujący się w menu alertu pulpitu.|
|[CMFCDesktopAlertWnd::OnCommand](#oncommand)|Struktura wywołuje tej funkcji elementu członkowskiego, gdy użytkownik wybierze element menu, gdy kontrolka podrzędna wysyła komunikat z powiadomieniem lub po naciśnięciu klawisza skrótu jest tłumaczony. (Przesłania [CWnd::OnCommand](../../mfc/reference/cwnd-class.md#oncommand).)|
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||
|[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)|Ustawia nowe szybkość animacji.|
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|Ustawia typ animacji.|
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|Ustawia limit czasu automatycznego zamykania.|
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|Przełącza między małe i normalnym transkrypcji.|
|[CMFCDesktopAlertWnd::SetTransparency](#settransparency)|Ustawia poziom przezroczystości.|

## <a name="remarks"></a>Uwagi

Alert okien pulpitu może być przezroczysty, może wystąpić przy użyciu efektów animacji i może zniknąć, (po określonym czasie opóźnienia lub jeśli użytkownik odrzuci ją, klikając przycisk Zamknij).

Alert okien pulpitu może również zawierać domyślny okna dialogowego, który z kolei zawiera ikonę, tekst komunikatu (etykieta) oraz łącze. Alternatywnie okno alertu pulpitu może zawierać niestandardowe okno dialogowe z zasobów aplikacji.

Utworzysz okno alertu pulpitu w dwóch krokach. Po pierwsze wywołanie konstruktora do konstruowania `CMFCDesktopAlertWnd` obiektu. Po drugie wywołanie [CMFCDesktopAlertWnd::Create](#create) funkcja elementu członkowskiego, aby utworzyć okno i dołączyć go do `CMFCDesktopAlertWnd` obiektu.

`CMFCDesktopAlertWnd` Obiektu tworzy okno dialogowe specjalne podrzędne, które wypełnia obszar kliencki okno alertu pulpitu. Okno dialogowe jest właścicielem wszystkich kontrolek, które są umieszczone na nim.

Aby wyświetlić niestandardowe okno dialogowe, w oknie podręcznym, wykonaj następujące kroki:

1. Wyprowadzić klasę z `CMFCDesktopAlertDialog`.

1. Tworzenie szablonu okna dialogowego podrzędnych w zasobach.

1. Wywołaj [CMFCDesktopAlertWnd::Create](#create) przy użyciu Identyfikatora zasobu szablonu okna dialogowego i wskaźnik do informacji o klasie czasu wykonywania klasy pochodnej.

1. Okno dialogowe niestandardowe do obsługi wszystkich powiadomień pochodzące z hostowanej formanty programu lub program hostowanej służy do obsługi tych powiadomień bezpośrednio.

Aby kontrolować zachowanie okno alertu pulpitu, należy użyć następujących funkcji:

- Ustaw typ animacji, wywołując [CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype). Prawidłowe opcje to rozwijania, Przesuń i zastosowania blaknięcia.

- Ustawia szybkość ramki animacji, wywołując [CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed).

- Ustaw poziom przezroczystości, wywołując [CMFCDesktopAlertWnd::SetTransparency](#settransparency).

- Zmień rozmiar podpisu dla małych, wywołując [CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption). Małe podpis jest 7 pikseli.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób używania różnych metod w `CMFCDesktopAlertWnd` klasa umożliwiająca skonfigurowanie `CMFCDesktopAlertWnd` obiektu. W przykładzie pokazano, jak ustawić typ animacji, ustaw przezroczystość okna podręcznego, określ, czy okno alertu powoduje wyświetlenie małych podpisu i ustawić czas, jaki musi upłynąć, zanim okno alertu zostanie automatycznie zamknięte. W przykładzie pokazano również sposób tworzenia i zainicjować okno alertu pulpitu. Ten fragment kodu jest częścią [próbka Demo alertu pulpitu](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxDesktopAlertWnd.h

##  <a name="create"></a>  CMFCDesktopAlertWnd::Create

Tworzy i inicjuje okno alertu pulpitu.

```
virtual BOOL Create(
    CWnd* pWndOwner,
    UINT uiDlgResID,
    HMENU hMenu = NULL,
    CPoint ptPos = CPoint(-1,-1),
    CRuntimeClass* pRTIDlgBar = RUNTIME_CLASS(CMFCDesktopAlertDialog));


virtual BOOL Create(
    CWnd* pWndOwner,
    CMFCDesktopAlertWndInfo& params,
    HMENU hMenu = NULL,
    CPoint ptPos = CPoint(-1,-1));
```

### <a name="parameters"></a>Parametry

[in] [out] *pWndOwner* Określa właściciela okno alertu. Ten właściciel następnie będą otrzymywać wszystkie powiadomienia dla okno alertu pulpitu. Ta wartość nie może mieć wartości NULL.

*uiDlgResID*<br/>
[in] Określa identyfikator zasobu w oknie alert.

*hMenu*<br/>
[in] Określa menu wyświetlanym po kliknięciu przycisku menu. Jeśli ma wartość NULL, nie jest wyświetlany przycisk menu.

*ptPos*<br/>
[in] Określa położenie początkowe, w którym jest wyświetlana w oknie alert, za pomocą współrzędnych ekranu. Jeśli ten parametr ma (-1, -1), w oknie alert jest wyświetlany w prawym dolnym rogu ekranu.

*pRTIDlgBar*<br/>
[in] Informacje o klasie czasu wykonywania dla klasy pole niestandardowe okno dialogowe, w którym omówiono obszaru klienckiego okna alertu.

*params*<br/>
[in] Określa parametry, które są używane w celu utworzenia alertu okna.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli w oknie alert został utworzony pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę w celu utworzenia alertu okna. Obszar kliencki okno alertu zawiera podrzędne okno dialogowe, który obsługuje wszystkich kontrolek, które są widoczne dla użytkownika.

Pierwsze przeciążenie metody tworzy alert okien, zawierającą podrzędne okno dialogowe, który jest ładowany z zasobów aplikacji. Pierwsze przeciążenie metody można również określić informacje o klasie czasu wykonywania dla klasy pole niestandardowe okno dialogowe.

Drugie przeciążenie metody tworzy alert okien, zawierający kontrolkami domyślnymi. Można określić, która kontroluje, aby wyświetlić, modyfikując [klasa CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md).

##  <a name="getanimationspeed"></a>  CMFCDesktopAlertWnd::GetAnimationSpeed

Zwraca szybkość animacji.

```
UINT GetAnimationSpeed() const;
```

### <a name="return-value"></a>Wartość zwracana

Szybkość animacji okna alertu, w milisekundach.

### <a name="remarks"></a>Uwagi

Szybkość animacji w tym artykule opisano sposób szybkiego otwiera i zamyka w oknie alert.

##  <a name="getanimationtype"></a>  CMFCDesktopAlertWnd::GetAnimationType

Zwraca typ animacji.

```
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```

### <a name="return-value"></a>Wartość zwracana

Jednym z następujących typów animacji:

- NO_ANIMATION

- ROZWIJANIA

- SLAJD

- ZANIKANIE

- SYSTEM_DEFAULT_ANIMATION

##  <a name="getautoclosetime"></a>  CMFCDesktopAlertWnd::GetAutoCloseTime

Zwraca wartość limitu czasu automatycznego zamykania.

```
int GetAutoCloseTime() const;
```

### <a name="return-value"></a>Wartość zwracana

Czas w milisekundach, po czym w oknie alert zostanie automatycznie zamknięte.

### <a name="remarks"></a>Uwagi

Metoda ta jest przydatna w celu określenia, ile czasu powinien upłynąć, zanim alert okno zostanie automatycznie zamknięte.

##  <a name="getcaptionheight"></a>  CMFCDesktopAlertWnd::GetCaptionHeight

Zwraca wysokość podpis.

```
virtual int GetCaptionHeight();
```

### <a name="return-value"></a>Wartość zwracana

Wysokość w pikselach, podpis.

### <a name="remarks"></a>Uwagi

Ta metoda może zostać zastąpiona w klasie pochodnej. Domyślna implementacja albo: zwraca wartość wysokości małych podpisu (7 w pikselach), jeśli wyskakujące powinien być wyświetlany w małych podpis lub uzyskaną z funkcji Windows API `GetSystemMetrics(SM_CYSMCAPTION)`.

##  <a name="getlastpos"></a>  CMFCDesktopAlertWnd::GetLastPos

Zwraca pozycję ostatniego okno alertu pulpitu, na ekranie.

```
CPoint GetLastPos() const;
```

### <a name="return-value"></a>Wartość zwracana

Punkt, w współrzędne ekranu.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca prawidłową ostatniej pozycji w oknie alert na ekranie.

##  <a name="gettransparency"></a>  CMFCDesktopAlertWnd::GetTransparency

Zwraca poziom przezroczystości.

```
BYTE GetTransparency() const;
```

### <a name="return-value"></a>Wartość zwracana

Poziom przezroczystości zakresu od 0 do 255 włącznie. Im większa wartość, więcej nieprzezroczysty okna.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia pobieranie bieżącego poziomu przezroczystości okno alertu.

##  <a name="hassmallcaption"></a>  CMFCDesktopAlertWnd::HasSmallCaption

Określa, czy okno alertu pulpitu, ma mały podpisu lub podpis zwykłych rozmiar.

```
BOOL HasSmallCaption() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli zostanie wyświetlone okno popup, poprzedzoną małych; Wartość FALSE, jeśli wyskakujące jest wyświetlane z tekstem o rozmiarze zwykłych.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia określić, czy okno podręczne małych podpisu lub podpis zwykłych rozmiar. Domyślnie małych podpis jest 7 pikseli. Wysokość podpis zwykłych rozmiar można uzyskać przez wywołanie funkcji interfejsu Windows API `GetSystemMetrics(SM_CYCAPTION)`.

##  <a name="onbeforeshow"></a>  CMFCDesktopAlertWnd::OnBeforeShow


```
virtual BOOL OnBeforeShow(CPoint&);
```

### <a name="parameters"></a>Parametry

[in] *CPoint &*

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="onclicklinkbutton"></a>  CMFCDesktopAlertWnd::OnClickLinkButton

Wywoływane przez platformę, gdy użytkownik kliknie przycisk link znajdujący się w menu alertu pulpitu.

```
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```

### <a name="parameters"></a>Parametry

*uiCmdID*<br/>
[in] Ten parametr nie jest używany.

### <a name="return-value"></a>Wartość zwracana

Zawsze wartość FALSE.

### <a name="remarks"></a>Uwagi

Przesłonić tę metodę w klasie pochodnej, jeśli chcesz otrzymywać powiadomienia, gdy użytkownik kliknie link w oknie alert.

##  <a name="oncommand"></a>  CMFCDesktopAlertWnd::OnCommand


```
virtual BOOL OnCommand(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*wParam*<br/>
[in] [in] *lParam*

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ondraw"></a>  CMFCDesktopAlertWnd::OnDraw


```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[in] *podstawowego kontrolera domeny*

### <a name="remarks"></a>Uwagi

##  <a name="processcommand"></a>  CMFCDesktopAlertWnd::ProcessCommand


```
BOOL ProcessCommand(HWND hwnd);
```

### <a name="parameters"></a>Parametry

[in] *hwnd*

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="setanimationspeed"></a>  CMFCDesktopAlertWnd::SetAnimationSpeed

Ustawia nowe szybkość animacji.

```
void SetAnimationSpeed(UINT nSpeed);
```

### <a name="parameters"></a>Parametry

*nSpeed*<br/>
[in] Określa nowe szybkość animacji w milisekundach.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby ustawić szybkość animacji okno alertu. Szybkość animacji domyślny to 30 milisekund.

##  <a name="setanimationtype"></a>  CMFCDesktopAlertWnd::SetAnimationType

Ustawia typ animacji.

```
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
[in] Określa typ animacji.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby ustawić typ animacji. Można określić jedną z następujących wartości:

- NO_ANIMATION

- ROZWIJANIA

- SLAJD

- ZANIKANIE

- SYSTEM_DEFAULT_ANIMATION

##  <a name="setautoclosetime"></a>  CMFCDesktopAlertWnd::SetAutoCloseTime

Ustawia limit czasu automatycznego zamykania.

```
void SetAutoCloseTime(int nTime);
```

### <a name="parameters"></a>Parametry

*nTime*<br/>
[in] Czas w milisekundach, który musi upłynąć, zanim okno alertu zostanie automatycznie zamknięte.

### <a name="remarks"></a>Uwagi

W oknie alert zostaje automatycznie zamknięty po określonym czasie, jeśli użytkownik nie wchodzi w interakcję z oknem.

##  <a name="setsmallcaption"></a>  CMFCDesktopAlertWnd::SetSmallCaption

Przełącza między małe i rozmiar zwykłych transkrypcji.

```
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```

### <a name="parameters"></a>Parametry

*bSmallCaption*<br/>
[in] Wartość TRUE, aby określić, czy okno alertu powoduje wyświetlenie małych podpis; w przeciwnym razie wartość FALSE, aby określić, czy okno alertu powoduje wyświetlenie podpis zwykłych rozmiar.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby wyświetlić podpis małe lub rozmiar zwykłych. Domyślnie małych podpis jest 7 pikseli. Rozmiar podpisu regularnych można uzyskać przez wywołanie funkcji interfejsu Windows API `GetSystemMetrics(SM_CYCAPTION)`.

##  <a name="settransparency"></a>  CMFCDesktopAlertWnd::SetTransparency

Ustawia poziom przezroczystości w oknie podręcznym.

```
void SetTransparency(BYTE nTransparency);
```

### <a name="parameters"></a>Parametry

*nTransparency*<br/>
[in] Określa poziom przezroczystości. Ta wartość musi być z zakresu od 0 do 255 włącznie. Im większa wartość, więcej nieprzezroczysty okna.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby ustawić poziom przezroczystości w oknie podręcznym.

##  <a name="getdialogsize"></a>  CMFCDesktopAlertWnd::GetDialogSize


```
virtual CSize GetDialogSize();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[Klasa CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)
