---
title: Klasa CMDIChildWnd
ms.date: 11/04/2016
f1_keywords:
- CMDIChildWnd
- AFXWIN/CMDIChildWnd
- AFXWIN/CMDIChildWnd::CMDIChildWnd
- AFXWIN/CMDIChildWnd::Create
- AFXWIN/CMDIChildWnd::GetMDIFrame
- AFXWIN/CMDIChildWnd::MDIActivate
- AFXWIN/CMDIChildWnd::MDIDestroy
- AFXWIN/CMDIChildWnd::MDIMaximize
- AFXWIN/CMDIChildWnd::MDIRestore
- AFXWIN/CMDIChildWnd::SetHandles
helpviewer_keywords:
- CMDIChildWnd [MFC], CMDIChildWnd
- CMDIChildWnd [MFC], Create
- CMDIChildWnd [MFC], GetMDIFrame
- CMDIChildWnd [MFC], MDIActivate
- CMDIChildWnd [MFC], MDIDestroy
- CMDIChildWnd [MFC], MDIMaximize
- CMDIChildWnd [MFC], MDIRestore
- CMDIChildWnd [MFC], SetHandles
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
ms.openlocfilehash: 0acd42db19151001d9e292561ef20e469f9e14ea
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222969"
---
# <a name="cmdichildwnd-class"></a>Klasa CMDIChildWnd

Oferuje funkcje okna podrzędnego interfejsu wielu dokumentów (MDI) systemu Windows wraz z elementami członkowskimi do zarządzania oknem.

## <a name="syntax"></a>Składnia

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMDIChildWnd:: CMDIChildWnd](#cmdichildwnd)|Konstruuje `CMDIChildWnd` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMDIChildWnd:: Create](#create)|Tworzy okno podrzędne MDI systemu Windows skojarzone z `CMDIChildWnd` obiektem.|
|[CMDIChildWnd:: GetMDIFrame](#getmdiframe)|Zwraca nadrzędną ramkę MDI okna klienta MDI.|
|[CMDIChildWnd:: MDIActivate](#mdiactivate)|Aktywuje to okno podrzędne MDI.|
|[CMDIChildWnd:: MDIDestroy](#mdidestroy)|Niszczy to okno podrzędne MDI.|
|[CMDIChildWnd:: MDIMaximize](#mdimaximize)|Maksymalizuje to okno podrzędne MDI.|
|[CMDIChildWnd:: MDIRestore](#mdirestore)|Przywraca to okno podrzędne MDI z rozmiaru zmaksymalizowanego lub zminimalizowanego.|
|[CMDIChildWnd:: sethandles](#sethandles)|Ustawia uchwyty dla zasobów menu i akceleratora.|

## <a name="remarks"></a>Uwagi

Okno podrzędne MDI wygląda podobnie do typowego okna ramowego, z tą różnicą, że okno potomne MDI pojawia się wewnątrz okna ramki MDI, a nie na pulpicie. Okno podrzędne MDI nie ma własnego paska menu, ale zamiast tego udostępnia menu w oknie ramka MDI. Struktura automatycznie zmienia menu ramki MDI, aby reprezentować aktualnie aktywne okno podrzędne MDI.

Aby utworzyć przydatne okno podrzędne MDI dla aplikacji, Utwórz klasę z `CMDIChildWnd` . Dodaj Zmienne Członkowskie do klasy pochodnej, aby przechowywać dane specyficzne dla aplikacji. Implementuj funkcje składowe programu obsługi komunikatów i mapę komunikatów w klasie pochodnej, aby określić, co się dzieje w przypadku kierowania komunikatów do okna.

Istnieją trzy sposoby konstruowania podrzędnego okna MDI:

- Bezpośrednie konstruowanie przy użyciu `Create` .

- Bezpośrednie konstruowanie przy użyciu `LoadFrame` .

- Pośrednie konstruowanie go za pomocą szablonu dokumentu.

Przed wywołaniem `Create` lub należy `LoadFrame` skonstruować obiekt okna ramki na stercie przy użyciu **`new`** operatora C++. Przed wywołaniem `Create` można również zarejestrować klasę okna przy użyciu funkcji globalnej [AfxRegisterWndClass —](application-information-and-management.md#afxregisterwndclass) , aby ustawić style ikon i klas dla ramki.

Użyj `Create` funkcji członkowskiej, aby przekazać parametry tworzenia ramki jako natychmiastowe argumenty.

`LoadFrame`wymaga mniej argumentów niż `Create` , a zamiast tego pobiera większość wartości domyślnych z zasobów, w tym podpis ramki, ikonę, tabelę akceleratorów i menu. Aby można było uzyskać dostęp do programu `LoadFrame` , wszystkie te zasoby muszą mieć ten sam identyfikator zasobu (na przykład IDR_MAINFRAME).

Gdy `CMDIChildWnd` obiekt zawiera widoki i dokumenty, są one tworzone pośrednio przez platformę, a nie bezpośrednio przez programistę. Obiekt organizuje `CDocTemplate` Tworzenie ramki, Tworzenie widoków zawierających i łączenie widoków z odpowiednim dokumentem. Parametry `CDocTemplate` konstruktora określają `CRuntimeClass` spośród trzech należących do siebie klas (dokumentu, ramki i widoku). `CRuntimeClass`Obiekt jest używany przez platformę do dynamicznego tworzenia nowych ramek, gdy jest określony przez użytkownika (na przykład przy użyciu polecenia nowy plik lub w oknie MDI nowe polecenie).

Klasa okien ramowych pochodna from `CMDIChildWnd` musi być zadeklarowana przy użyciu DECLARE_DYNCREATE, aby powyższy mechanizm RUNTIME_CLASS działał poprawnie.

`CMDIChildWnd`Klasa dziedziczy większość implementacji domyślnej z `CFrameWnd` . Aby uzyskać szczegółową listę tych funkcji, zapoznaj się z opisem klasy [obiektu CFrameWnd](../../mfc/reference/cframewnd-class.md) . `CMDIChildWnd`Klasa ma następujące dodatkowe funkcje:

- W połączeniu z `CMultiDocTemplate` klasą, wiele `CMDIChildWnd` obiektów z tego samego szablonu dokumentu współużytkuje to samo menu, co oszczędza zasoby systemu Windows.

- Obecnie aktywne menu okna podrzędnego MDI zastępuje menu okna ramki MDI, a podpis okna podrzędnego aktualnie aktywnego MDI jest dodawany do podpisu okna ramki MDI. Aby uzyskać więcej przykładów funkcji okna podrzędnego MDI, które są zaimplementowane w połączeniu z oknem ramki MDI, zobacz `CMDIFrameWnd` opis klasy.

Nie używaj **`delete`** operatora C++ do niszczenia okna ramki. Zamiast tego użyj polecenia cmdlet `CWnd::DestroyWindow`. `CFrameWnd`Implementacja programu `PostNcDestroy` spowoduje usunięcie obiektu C++, gdy okno zostanie zniszczone. Gdy użytkownik zamknie okno ramki, domyślnie `OnClose` zostanie wywołana procedura obsługi `DestroyWindow` .

Aby uzyskać więcej informacji na temat `CMDIChildWnd` , zobacz [okna ramek](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="cmdichildwndcmdichildwnd"></a><a name="cmdichildwnd"></a>CMDIChildWnd:: CMDIChildWnd

Wywołanie metody konstruowania `CMDIChildWnd` obiektu.

```
CMDIChildWnd();
```

### <a name="remarks"></a>Uwagi

Wywołaj `Create` , aby utworzyć widoczne okno.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CMDIChildWnd:: Create](#create).

## <a name="cmdichildwndcreate"></a><a name="create"></a>CMDIChildWnd:: Create

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć okno podrzędne MDI systemu Windows i dołączyć je do `CMDIChildWnd` obiektu.

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_OVERLAPPEDWINDOW,
    const RECT& rect = rectDefault,
    CMDIFrameWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

*lpszClassName*<br/>
Wskazuje ciąg znaków zakończony znakiem null, który nazywa klasę systemu Windows (struktura [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) ). Nazwą klasy może być dowolna nazwa zarejestrowana w funkcji globalnej [AfxRegisterWndClass —](application-information-and-management.md#afxregisterwndclass) . Dla warstwy Standardowa powinna mieć wartość NULL `CMDIChildWnd` .

*lpszWindowName*<br/>
Wskazuje ciąg znaków zakończony znakiem null, który reprezentuje nazwę okna. Używany jako tekst paska tytułu.

*dwStyle*<br/>
Określa atrybuty [stylu](../../mfc/reference/styles-used-by-mfc.md#window-styles) okna. Styl WS_CHILD jest wymagany.

*cinania*<br/>
Zawiera rozmiar i położenie okna. `rectDefault`Wartość umożliwia systemowi Windows określenie rozmiaru i położenia nowego `CMDIChildWnd` .

*pParentWnd*<br/>
Określa element nadrzędny okna. Jeśli wartość jest równa NULL, używane jest główne okno aplikacji.

*pContext*<br/>
Określa strukturę [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) . Ten parametr może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aktywne okno ramki podrzędnej MDI może określić podpis okna ramki nadrzędnej. Ta funkcja jest wyłączona, wyłączając FWS_ADDTOTITLE bitowej stylu okna ramki podrzędnej.

Struktura wywołuje tę funkcję elementu członkowskiego w odpowiedzi na polecenie użytkownika w celu utworzenia okna podrzędnego, a struktura używa parametru *pContext* w celu prawidłowego połączenia okna podrzędnego z aplikacją. Po wywołaniu `Create` *pContext* może mieć wartość null.

### <a name="example"></a>Przykład

Przykład 1:

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>Przykład

Przykład 2:

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

## <a name="cmdichildwndgetmdiframe"></a><a name="getmdiframe"></a>CMDIChildWnd:: GetMDIFrame

Wywołaj tę funkcję, aby zwrócić ramkę nadrzędną MDI.

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna ramki nadrzędnej MDI.

### <a name="remarks"></a>Uwagi

Zwrócona ramka to dwie elementy nadrzędne usunięte z `CMDIChildWnd` i jest elementem nadrzędnym okna typu MDICLIENT, który zarządza `CMDIChildWnd` obiektem. Wywołaj funkcję elementu członkowskiego [GetParent](../../mfc/reference/cwnd-class.md#getparent) , aby zwracała `CMDIChildWnd` natychmiastowy element nadrzędny MDICLIENT obiektu jako `CWnd` wskaźnik tymczasowy.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CMDIFrameWnd:: MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).

## <a name="cmdichildwndmdiactivate"></a><a name="mdiactivate"></a>CMDIChildWnd:: MDIActivate

Wywołaj tę funkcję elementu członkowskiego, aby aktywować okno potomne MDI niezależnie od okna ramki MDI.

```cpp
void MDIActivate();
```

### <a name="remarks"></a>Uwagi

Gdy ramka zostanie uaktywniona, uaktywnia się okno podrzędne, które zostało ostatnio aktywowane.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CMDIFrameWnd:: GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).

## <a name="cmdichildwndmdidestroy"></a><a name="mdidestroy"></a>CMDIChildWnd:: MDIDestroy

Wywołaj tę funkcję elementu członkowskiego, aby zniszczyć okno potomne MDI.

```cpp
void MDIDestroy();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska usuwa tytuł okna podrzędnego z okna ramki i dezaktywuje okno podrzędne.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

## <a name="cmdichildwndmdimaximize"></a><a name="mdimaximize"></a>CMDIChildWnd:: MDIMaximize

Wywołaj tę funkcję elementu członkowskiego, aby zmaksymalizować okno podrzędne MDI.

```cpp
void MDIMaximize();
```

### <a name="remarks"></a>Uwagi

Gdy okno podrzędne jest zmaksymalizowane, system Windows zmienia jego rozmiar, aby obszar klienta wypełniał obszar klienta okna ramki. System Windows umieści menu sterowania okna podrzędnego na pasku menu ramki, dzięki czemu użytkownik może przywrócić lub zamknąć okno podrzędne i dodaje tytuł okna podrzędnego do tytułu okna ramki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

## <a name="cmdichildwndmdirestore"></a><a name="mdirestore"></a>CMDIChildWnd:: MDIRestore

Wywołaj tę funkcję elementu członkowskiego, aby przywrócić okno podrzędne MDI z rozmiaru zmaksymalizowanego lub zminimalizowanego.

```cpp
void MDIRestore();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

## <a name="cmdichildwndsethandles"></a><a name="sethandles"></a>CMDIChildWnd:: sethandles

Ustawia uchwyty dla zasobów menu i akceleratora.

```cpp
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
Uchwyt zasobu menu.

*hAccel*<br/>
Uchwyt zasobu akceleratora.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby ustawić zasoby menu i akceleratora używane przez obiekt podrzędnego okna MDI.

## <a name="see-also"></a>Zobacz także

[Przykładowy interfejs MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład MDIDOCVW MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład SNAPVW MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa obiektu CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)
