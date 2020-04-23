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
ms.openlocfilehash: a547a21b96d035f507e749aeb19f891175498d5d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754574"
---
# <a name="cmdichildwnd-class"></a>Klasa CMDIChildWnd

Udostępnia funkcje okna podrzędnego interfejsu wielu dokumentów systemu Windows (MDI) wraz z członkami do zarządzania oknem.

## <a name="syntax"></a>Składnia

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|Konstruuje `CMDIChildWnd` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMDIChildWnd::Utwórz](#create)|Tworzy okno podrzędne mdi systemu `CMDIChildWnd` Windows skojarzone z obiektem.|
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|Zwraca ramkę nadrzędnego MDI okna klienta MDI.|
|[CMDIChildWnd::MDIActivate](#mdiactivate)|Aktywuje to okno podrzędne MDI.|
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|Niszczy to okno podrzędne MDI.|
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|Maksymalizuje to okno podrzędne MDI.|
|[CMDIChildWnd::MDIRestore](#mdirestore)|Przywraca to okno podrzędne MDI z maksymalnego lub zminimalizowane rozmiar.|
|[CMDIChildWnd::SetHandles](#sethandles)|Ustawia uchwyty dla zasobów menu i akceleratora.|

## <a name="remarks"></a>Uwagi

Okno podrzędne MDI wygląda podobnie do typowego okna ramki, z tą różnicą, że okno podrzędne MDI pojawia się wewnątrz okna ramki MDI, a nie na pulpicie. Okno podrzędne MDI nie ma własnego paska menu, ale zamiast tego udostępnia menu okna ramki MDI. Struktura automatycznie zmienia menu ramki MDI, aby reprezentować aktualnie aktywne okno podrzędne MDI.

Aby utworzyć przydatne okno podrzędne MDI dla aplikacji, należy wyprowadzić klasę z . `CMDIChildWnd` Dodaj zmienne członkowskie do klasy pochodnej do przechowywania danych specyficznych dla aplikacji. Zaimplementuj funkcje członkowskie programu message-handler i mapę wiadomości w klasie pochodnej, aby określić, co się dzieje, gdy wiadomości są kierowane do okna.

Istnieją trzy sposoby konstruowania okna podrzędnego MDI:

- Bezpośrednio konstruuj go za pomocą `Create`.

- Bezpośrednio konstruuj go za pomocą `LoadFrame`.

- Pośrednio konstruować go za pomocą szablonu dokumentu.

Przed `Create` wywołaniem `LoadFrame`lub , należy skonstruować obiekt okna ramki na stosie przy użyciu **c++ nowy** operator. Przed `Create` wywołaniem można również zarejestrować klasę okna za pomocą [afxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) funkcji globalnej, aby ustawić ikonę i style klasy dla ramki.

Funkcja `Create` elementu członkowskiego służy do przekazywania parametrów tworzenia ramki jako argumentów natychmiastowych.

`LoadFrame`wymaga mniejszej `Create`liczby argumentów niż program , a zamiast tego pobiera większość wartości domyślnych z zasobów, w tym podpis ramki, ikonę, tabelę akceleratora i menu. Aby dostęp `LoadFrame`do nich był dostępny, wszystkie te zasoby muszą mieć ten sam identyfikator zasobu (na przykład IDR_MAINFRAME).

Gdy `CMDIChildWnd` obiekt zawiera widoki i dokumenty, są one tworzone pośrednio przez strukturę, a nie bezpośrednio przez programistę. Obiekt `CDocTemplate` organizuje tworzenie ramki, tworzenie zawierających widoków i połączenie widoków z odpowiednim dokumentem. Parametry konstruktora `CDocTemplate` określają `CRuntimeClass` trzy zaangażowane klasy (dokument, ramka i widok). Obiekt `CRuntimeClass` jest używany przez strukturę do dynamicznego tworzenia nowych ramek po określeniu przez użytkownika (na przykład za pomocą polecenia Plik nowy lub polecenia Okno MDI Nowe).

Klasa okna ramki pochodzące z `CMDIChildWnd` muszą być zadeklarowane z DECLARE_DYNCREATE, aby powyższy mechanizm RUNTIME_CLASS działać poprawnie.

Klasa `CMDIChildWnd` dziedziczy większość swojej domyślnej implementacji z `CFrameWnd`. Aby uzyskać szczegółową listę tych funkcji, zapoznaj się z opisem klasy [CFrameWnd.](../../mfc/reference/cframewnd-class.md) Klasa `CMDIChildWnd` posiada następujące dodatkowe funkcje:

- W połączeniu `CMultiDocTemplate` z klasą wiele `CMDIChildWnd` obiektów z tego samego szablonu dokumentu współużytkuje to samo menu, oszczędzając zasoby systemowe systemu Windows.

- Aktualnie aktywne menu okna podrzędnego MDI całkowicie zastępuje menu okna ramki MDI, a podpis aktualnie aktywnego okna podrzędnego MDI jest dodawany do podpisu okna ramki MDI. Aby uzyskać więcej przykładów funkcji okna podrzędnego MDI, które są implementowane w połączeniu z oknem ramki MDI, zobacz opis `CMDIFrameWnd` klasy.

Nie należy używać operatora **usuwania** języka C++, aby zniszczyć okno ramki. Zamiast tego użyj polecenia cmdlet `CWnd::DestroyWindow`. Implementacja `CFrameWnd` `PostNcDestroy` spowoduje usunięcie obiektu C++, gdy okno zostanie zniszczone. Gdy użytkownik zamknie okno ramki, wywoła domyślny `OnClose` program obsługi `DestroyWindow`.

Aby uzyskać `CMDIChildWnd`więcej informacji na temat , zobacz [Ramka Systemu Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cmdichildwndcmdichildwnd"></a><a name="cmdichildwnd"></a>CMDIChildWnd::CMDIChildWnd

Wywołanie do `CMDIChildWnd` konstruowania obiektu.

```
CMDIChildWnd();
```

### <a name="remarks"></a>Uwagi

Wywołanie, `Create` aby utworzyć widoczne okno.

### <a name="example"></a>Przykład

  Zobacz przykład [dla CMDIChildWnd::Create](#create).

## <a name="cmdichildwndcreate"></a><a name="create"></a>CMDIChildWnd::Utwórz

Wywołanie tej funkcji elementu członkowskiego, aby utworzyć okno `CMDIChildWnd` podrzędne MDI systemu Windows i dołączyć go do obiektu.

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

*lpszClassName (nazwa klasy)*<br/>
Wskazuje ciąg znaków zakończony z wartością null, który nazywa klasę systemu Windows (strukturę [WNDCLASS).](/windows/win32/api/winuser/ns-winuser-wndclassw) Nazwa klasy może być dowolną nazwą zarejestrowaną za pomocą funkcji globalnej [AfxRegisterWndClass.](application-information-and-management.md#afxregisterwndclass) Powinien być NULL `CMDIChildWnd`dla standardu .

*lpszWindowName*<br/>
Wskazuje ciąg znaków zakończony z wartością null, który reprezentuje nazwę okna. Używany jako tekst paska tytułu.

*Dwstyle*<br/>
Określa atrybuty [stylu](../../mfc/reference/styles-used-by-mfc.md#window-styles) okna. Wymagany jest styl WS_CHILD.

*Rect*<br/>
Zawiera rozmiar i położenie okna. Wartość `rectDefault` umożliwia systemowi Windows określenie rozmiaru `CMDIChildWnd`i położenia nowego pliku .

*pParentWnd*<br/>
Określa element nadrzędny okna. Jeśli null, używane jest główne okno aplikacji.

*Pcontext*<br/>
Określa strukturę [CCreateContext.](../../mfc/reference/ccreatecontext-structure.md) Ten parametr może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aktualnie aktywne okno ramki podrzędnej MDI może określić podpis nadrzędnego okna ramki. Ta funkcja jest wyłączona przez wyłączenie FWS_ADDTOTITLE stylu okna ramki podrzędnej.

Struktura wywołuje tę funkcję elementu członkowskiego w odpowiedzi na polecenie użytkownika, aby utworzyć okno podrzędne, a struktura używa parametru *pContext,* aby poprawnie połączyć okno podrzędne z aplikacją. Podczas wywoływania `Create`, *pContext* może być NULL.

### <a name="example"></a>Przykład

Przykład 1:

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>Przykład

Przykład 2:

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

## <a name="cmdichildwndgetmdiframe"></a><a name="getmdiframe"></a>CMDIChildWnd::GetMDIFrame

Wywołanie tej funkcji, aby zwrócić ramkę nadrzędną MDI.

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna ramki nadrzędnej MDI.

### <a name="remarks"></a>Uwagi

Zwrócona ramka jest dwa `CMDIChildWnd` nadrzędne usunięte z i jest elementem nadrzędnym `CMDIChildWnd` okna typu MDICLIENT, który zarządza obiektem. Wywołanie Funkcji elementu członkowskiego [GetParent,](../../mfc/reference/cwnd-class.md#getparent) aby zwrócić `CMDIChildWnd` obiekt bezpośredni `CWnd` obiekt nadrzędny MDICLIENT jako wskaźnik tymczasowy.

### <a name="example"></a>Przykład

  Zobacz przykład [dla CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).

## <a name="cmdichildwndmdiactivate"></a><a name="mdiactivate"></a>CMDIChildWnd::MDIActivate

Wywołanie tej funkcji elementu członkowskiego, aby aktywować okno podrzędne MDI niezależnie od okna ramki MDI.

```cpp
void MDIActivate();
```

### <a name="remarks"></a>Uwagi

Gdy ramka stanie się aktywna, zostanie aktywowane okno podrzędne, które zostało ostatnio aktywowane.

### <a name="example"></a>Przykład

  Zobacz przykład [dla CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).

## <a name="cmdichildwndmdidestroy"></a><a name="mdidestroy"></a>CMDIChildWnd::MDIDestroy

Wywołanie tej funkcji elementu członkowskiego, aby zniszczyć okno podrzędne MDI.

```cpp
void MDIDestroy();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego usuwa tytuł okna podrzędnego z okna ramki i dezaktywuje okno podrzędne.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

## <a name="cmdichildwndmdimaximize"></a><a name="mdimaximize"></a>CMDIChildWnd::MDIMaximize

Wywołanie tej funkcji elementu członkowskiego, aby zmaksymalizować okno podrzędne MDI.

```cpp
void MDIMaximize();
```

### <a name="remarks"></a>Uwagi

Gdy okno podrzędne jest zmaksymalizowane, system Windows zmienia jego rozmiar, aby jego obszar klienta wypełniał obszar klienta okna ramki. System Windows umieszcza menu Sterowanie okna podrzędnego na pasku menu ramki, aby użytkownik mógł przywrócić lub zamknąć okno podrzędne i dodaje tytuł okna podrzędnego do tytułu okna ramki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

## <a name="cmdichildwndmdirestore"></a><a name="mdirestore"></a>CMDIChildWnd::MDIRestore

Wywołanie tej funkcji elementu członkowskiego, aby przywrócić okno podrzędne MDI z maksymalnego lub zminimalizowanego rozmiaru.

```cpp
void MDIRestore();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

## <a name="cmdichildwndsethandles"></a><a name="sethandles"></a>CMDIChildWnd::SetHandles

Ustawia uchwyty dla zasobów menu i akceleratora.

```cpp
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>Parametry

*Hmenu*<br/>
Dojście zasobu menu.

*hAccel (własówk.*<br/>
Dojście zasobu akceleratora.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby ustawić zasoby menu i akceleratora używane przez obiekt okna podrzędnego MDI.

## <a name="see-also"></a>Zobacz też

[Przykładowy MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)
