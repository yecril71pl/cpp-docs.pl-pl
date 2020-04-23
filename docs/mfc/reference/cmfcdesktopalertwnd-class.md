---
title: Klasa CMFCDesktopAlertWnd
ms.date: 10/18/2018
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
ms.openlocfilehash: cf453b6e69f012bedaf0bd91b5eaf11f7caffa12
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752457"
---
# <a name="cmfcdesktopalertwnd-class"></a>Klasa CMFCDesktopAlertWnd

Klasa `CMFCDesktopAlertWnd` implementuje funkcjonalność niemodalne okno dialogowe, które pojawia się na ekranie, aby poinformować użytkownika o zdarzeniu.

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCDesktopAlertWnd : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDesktopAlertWnd::Tworzenie](#create)|Tworzy i inicjuje okno alertów pulpitu.|
|[CMFCDesktopAlertWnd::GetAnimationSpeed](#getanimationspeed)|Zwraca szybkość animacji.|
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|Zwraca typ animacji.|
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|Zwraca limit czasu automatycznego zamykania.|
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|Zwraca wysokość podpisu.|
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|Zwraca ostatnią prawidłową pozycję okna alertu pulpitu na ekranie.|
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|Zwraca poziom przezroczystości.|
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|Określa, czy okno alertu pulpitu jest wyświetlane z małym podpisem.|
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|Wywoływana przez strukturę, gdy użytkownik kliknie przycisk łącza znajdujący się w menu alertów na pulpicie.|
|[CMFCDesktopAlertWnd::OnCommand](#oncommand)|Struktura wywołuje tę funkcję elementu członkowskiego, gdy użytkownik wybiera element z menu, gdy formant podrzędny wysyła komunikat powiadomienia lub gdy naciśnięcie klawisza akceleratora jest tłumaczone. (Zastępuje [CWnd::OnCommand](../../mfc/reference/cwnd-class.md#oncommand).)|
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||
|[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)|Ustawia nową szybkość animacji.|
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|Ustawia typ animacji.|
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|Ustawia limit czasu automatycznego zamykania.|
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|Przełącza między małymi i normalnymi podpisami.|
|[CMFCDesktopAlertWnd::SetTransparency](#settransparency)|Ustawia poziom przezroczystości.|

## <a name="remarks"></a>Uwagi

Okno alertu pulpitu może być przezroczyste, może pojawić się z efektami animacji i może zniknąć (po określonym opóźnieniu lub gdy użytkownik odrzuci je, klikając przycisk zamknij).

Okno alertu na pulpicie może również zawierać domyślne okno dialogowe, które z kolei zawiera ikonę, tekst wiadomości (etykietę) i łącze. Alternatywnie okno alertu pulpitu może zawierać niestandardowe okno dialogowe z zasobów aplikacji.

Okno alertu pulpitu tworzy się w dwóch krokach. Najpierw wywołać konstruktora `CMFCDesktopAlertWnd` do konstruowania obiektu. Po drugie, wywołać [CMFCDesktopAlertWnd::Create](#create) funkcji elementu członkowskiego, `CMFCDesktopAlertWnd` aby utworzyć okno i dołączyć go do obiektu.

Obiekt `CMFCDesktopAlertWnd` tworzy specjalne okno dialogowe podrzędne, które wypełnia obszar klienta okna alertu pulpitu. Okno dialogowe jest właścicielem wszystkich formantów, które są umieszczone na nim.

Aby wyświetlić niestandardowe okno dialogowe w oknie podręcznym, wykonaj następujące czynności:

1. Wywodź `CMFCDesktopAlertDialog`klasę z pliku .

1. Tworzenie szablonu okna dialogowego podrzędnego w zasobach.

1. Wywołanie [CMFCDesktopAlertWnd::Utwórz](#create) przy użyciu identyfikatora zasobu szablonu okna dialogowego i wskaźnika do informacji o klasie środowiska uruchomieniowego klasy pochodnej.

1. Zaprogramuj niestandardowe okno dialogowe do obsługi wszystkich powiadomień pochodzących z hostowanych formantów lub zaprogramuj hostowane formanty do obsługi tych powiadomień bezpośrednio.

Aby kontrolować zachowanie okna alertów na pulpicie, należy użyć następujących funkcji:

- Ustaw typ animacji, wywołując [polecenie CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype). Prawidłowe opcje obejmują rozwijanie, przesuwanie i zanikanie.

- Ustaw szybkość klatki animacji, wywołując [polecenie CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed).

- Ustaw poziom przezroczystości, wywołując [polecenie CMFCDesktopAlertWnd::SetTransparency](#settransparency).

- Zmień rozmiar podpisu na mały, wywołując [POLECENIE CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption). Mały podpis ma wysokość 7 pikseli.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje, jak `CMFCDesktopAlertWnd` używać różnych metod `CMFCDesktopAlertWnd` w klasie, aby skonfigurować obiekt. W przykładzie pokazano, jak ustawić typ animacji, ustawić przezroczystość okna podręcznego, określić, że okno alertu wyświetla mały podpis, i ustawić czas, jaki upłynie, zanim okno alertu zostanie automatycznie zamknięte. W przykładzie pokazano również, jak utworzyć i zainicjować okno alertu pulpitu. Ten fragment kodu jest częścią [przykładu demo alertów pulpitu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cmfcdesktopalertwnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxDesktopAlertWnd.h

## <a name="cmfcdesktopalertwndcreate"></a><a name="create"></a>CMFCDesktopAlertWnd::Tworzenie

Tworzy i inicjuje okno alertów pulpitu.

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

*pWndOwner*<br/>
[w, na zewnątrz] Określa właściciela okna alertu. Ten właściciel otrzyma wtedy wszystkie powiadomienia dotyczące okna alertów na pulpicie. Ta wartość nie może być null.

*identyfikator uiDlgResID*<br/>
[w] Określa identyfikator zasobu okna alertu.

*Hmenu*<br/>
[w] Określa menu wyświetlane po kliknięciu przez użytkownika przycisku menu. Jeśli null, przycisk menu nie jest wyświetlany.

*ptPos (polski)*<br/>
[w] Określa początkową pozycję wyświetlania okna alertu przy użyciu współrzędnych ekranu. Jeśli ten parametr jest (-1, -1), okno alertu jest wyświetlane w prawym dolnym rogu ekranu.

*pRTIDlgBar*<br/>
[w] Informacje o klasie środowiska uruchomieniowego dla niestandardowej klasy okna dialogowego obejmującej obszar klienta okna alertu.

*params*<br/>
[w] Określa parametry używane do tworzenia okna alertu.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno alertu zostało utworzone pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby utworzyć okno alertu. Obszar klienta okna alertu zawiera okno dialogowe podrzędne, w którym znajdują się wszystkie formanty wyświetlane użytkownikowi.

Przeciążenie pierwszej metody tworzy okno alertu, które zawiera okno dialogowe podrzędne, które jest ładowane z zasobów aplikacji. Przeciążenie pierwszej metody można również określić informacje o klasie środowiska uruchomieniowego dla niestandardowej klasy okna dialogowego.

Przeciążenie drugiej metody tworzy okno alertu, które zawiera domyślne formanty. Można określić, które formanty mają być wyświetlane, modyfikując [klasę CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md).

## <a name="cmfcdesktopalertwndgetanimationspeed"></a><a name="getanimationspeed"></a>CMFCDesktopAlertWnd::GetAnimationSpeed

Zwraca szybkość animacji.

```
UINT GetAnimationSpeed() const;
```

### <a name="return-value"></a>Wartość zwracana

Szybkość animacji okna alertu w milisekundach.

### <a name="remarks"></a>Uwagi

Szybkość animacji opisuje szybkość otwarcia i zamknięcia okna alertu.

## <a name="cmfcdesktopalertwndgetanimationtype"></a><a name="getanimationtype"></a>CMFCDesktopAlertWnd::GetAnimationType

Zwraca typ animacji.

```
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```

### <a name="return-value"></a>Wartość zwracana

Jeden z następujących typów animacji:

- NO_ANIMATION

- Rozwijać

- Slajdów

- Fade

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndgetautoclosetime"></a><a name="getautoclosetime"></a>CMFCDesktopAlertWnd::GetAutoCloseTime

Zwraca limit czasu automatycznego zamykania.

```
int GetAutoCloseTime() const;
```

### <a name="return-value"></a>Wartość zwracana

Czas w milisekundach, po którym okno alertu zostanie automatycznie zamknięte.

### <a name="remarks"></a>Uwagi

Ta metoda służy do określenia, ile czasu powinno uginąć, zanim okno alertu zostanie automatycznie zamknięte.

## <a name="cmfcdesktopalertwndgetcaptionheight"></a><a name="getcaptionheight"></a>CMFCDesktopAlertWnd::GetCaptionHeight

Zwraca wysokość podpisu.

```
virtual int GetCaptionHeight();
```

### <a name="return-value"></a>Wartość zwracana

Wysokość, w pikselach, podpisu.

### <a name="remarks"></a>Uwagi

Ta metoda może zostać zastąpiona w klasie pochodnej. Domyślna implementacja: zwraca małą wartość wysokości podpisu (7 pikseli), jeśli w oknie podręcznym powinien być `GetSystemMetrics(SM_CYSMCAPTION)`wyświetlany mały podpis lub wartość uzyskana z funkcji interfejsu API systemu Windows .

## <a name="cmfcdesktopalertwndgetlastpos"></a><a name="getlastpos"></a>CMFCDesktopAlertWnd::GetLastPos

Zwraca ostatnią pozycję okna alertu pulpitu na ekranie.

```
CPoint GetLastPos() const;
```

### <a name="return-value"></a>Wartość zwracana

Punkt we współrzędnych ekranu.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca ostatnią prawidłową pozycję okna alertu na ekranie.

## <a name="cmfcdesktopalertwndgettransparency"></a><a name="gettransparency"></a>CMFCDesktopAlertWnd::GetTransparency

Zwraca poziom przezroczystości.

```
BYTE GetTransparency() const;
```

### <a name="return-value"></a>Wartość zwracana

Poziom przejrzystości od 0 do 255, włącznie. Im większa wartość, tym bardziej nieprzezroczyste okno.

### <a name="remarks"></a>Uwagi

Ta metoda służy do pobierania bieżącego poziomu przezroczystości okna alertu.

## <a name="cmfcdesktopalertwndhassmallcaption"></a><a name="hassmallcaption"></a>CMFCDesktopAlertWnd::HasSmallCaption

Określa, czy w oknie alertu pulpitu jest mały podpis, czy podpis o regularnym rozmiarze.

```
BOOL HasSmallCaption() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno podręczne jest wyświetlane z małym podpisem; FAŁSZ, jeśli okno podręczne jest wyświetlane z podpisem o regularnym rozmiarze.

### <a name="remarks"></a>Uwagi

Ta metoda służy do określenia, czy okno podręczne ma mały podpis lub podpis o regularnym rozmiarze. Domyślnie mały podpis ma wysokość 7 pikseli. Wysokość podpisu o regularnym rozmiarze można uzyskać, `GetSystemMetrics(SM_CYCAPTION)`wywołując funkcję interfejsu API systemu Windows .

## <a name="cmfcdesktopalertwndonbeforeshow"></a><a name="onbeforeshow"></a>CMFCDesktopAlertWnd::OnBeforeShow

```
virtual BOOL OnBeforeShow(CPoint&);
```

### <a name="parameters"></a>Parametry

[w] *CPoint&*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcdesktopalertwndonclicklinkbutton"></a><a name="onclicklinkbutton"></a>CMFCDesktopAlertWnd::OnClickLinkButton

Wywoływana przez strukturę, gdy użytkownik kliknie przycisk łącza znajdujący się w menu alertów na pulpicie.

```
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```

### <a name="parameters"></a>Parametry

*identyfikator uiCmdID*<br/>
[w] Ten parametr nie jest używany.

### <a name="return-value"></a>Wartość zwracana

Zawsze FALSE.

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę w klasie pochodnej, jeśli chcesz otrzymywać powiadomienia, gdy użytkownik kliknie łącze w oknie alertu.

## <a name="cmfcdesktopalertwndoncommand"></a><a name="oncommand"></a>CMFCDesktopAlertWnd::OnCommand

```
virtual BOOL OnCommand(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

[w] *wParam*<br/>

[w] *lParam*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcdesktopalertwndondraw"></a><a name="ondraw"></a>CMFCDesktopAlertWnd::OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[w] *pDC*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcdesktopalertwndprocesscommand"></a><a name="processcommand"></a>CMFCDesktopAlertWnd::ProcessCommand

```
BOOL ProcessCommand(HWND hwnd);
```

### <a name="parameters"></a>Parametry

[w] *hwnd (hwnd)*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcdesktopalertwndsetanimationspeed"></a><a name="setanimationspeed"></a>CMFCDesktopAlertWnd::SetAnimationSpeed

Ustawia nową szybkość animacji.

```cpp
void SetAnimationSpeed(UINT nSpeed);
```

### <a name="parameters"></a>Parametry

*nSpeed (prędkość)*<br/>
[w] Określa nową szybkość animacji w milisekundach.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby ustawić szybkość animacji dla okna alertu. Domyślna szybkość animacji wynosi 30 milisekund.

## <a name="cmfcdesktopalertwndsetanimationtype"></a><a name="setanimationtype"></a>CMFCDesktopAlertWnd::SetAnimationType

Ustawia typ animacji.

```cpp
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```

### <a name="parameters"></a>Parametry

*Typu*<br/>
[w] Określa typ animacji.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby ustawić typ animacji. Można określić jedną z następujących wartości:

- NO_ANIMATION

- Rozwijać

- Slajdów

- Fade

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndsetautoclosetime"></a><a name="setautoclosetime"></a>CMFCDesktopAlertWnd::SetAutoCloseTime

Ustawia limit czasu automatycznego zamykania.

```cpp
void SetAutoCloseTime(int nTime);
```

### <a name="parameters"></a>Parametry

*nCzas*<br/>
[w] Czas w milisekundach, który upływa, zanim okno alertu zostanie automatycznie zamknięte.

### <a name="remarks"></a>Uwagi

Okno alertu jest automatycznie zamykane po określonym czasie, jeśli użytkownik nie wchodzi w interakcję z oknem.

## <a name="cmfcdesktopalertwndsetsmallcaption"></a><a name="setsmallcaption"></a>CMFCDesktopAlertWnd::SetSmallCaption

Przełącza między podpisami o małym i regularnym rozmiarze.

```cpp
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```

### <a name="parameters"></a>Parametry

*bSmallCaption (Własnomienie)*<br/>
[w] PRAWDA, aby określić, że w oknie alertu jest wyświetlany mały podpis; w przeciwnym razie FALSE, aby określić, że w oknie alertu jest wyświetlany podpis o regularnym rozmiarze.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby wyświetlić podpis małych lub regularnych rozmiarów. Domyślnie mały podpis ma wysokość 7 pikseli. Rozmiar zwykłego podpisu można uzyskać, wywołując funkcję `GetSystemMetrics(SM_CYCAPTION)`interfejsu API systemu Windows .

## <a name="cmfcdesktopalertwndsettransparency"></a><a name="settransparency"></a>CMFCDesktopAlertWnd::SetTransparency

Ustawia poziom przezroczystości okna podręcznego.

```cpp
void SetTransparency(BYTE nTransparency);
```

### <a name="parameters"></a>Parametry

*nPrzejrzystywność*<br/>
[w] Określa poziom przezroczystości. Ta wartość musi być między 0 i 255, włącznie. Im większa wartość, tym bardziej nieprzezroczyste okno.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby ustawić poziom przezroczystości okna podręcznego.

## <a name="cmfcdesktopalertwndgetdialogsize"></a><a name="getdialogsize"></a>CMFCDesktopAlertWnd::GetDialogSize

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
