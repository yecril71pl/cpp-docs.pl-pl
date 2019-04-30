---
title: Cmdichildwnd — klasa
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
ms.openlocfilehash: 13f027e68184a4869e88883ff8b8d3b123b94e3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403935"
---
# <a name="cmdichildwnd-class"></a>Cmdichildwnd — klasa

Oferuje funkcje Windows okna interfejsu wielu dokumentów (MDI) podrzędne, wraz z elementami członkowskimi do zarządzania oknem.

## <a name="syntax"></a>Składnia

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|Konstruuje `CMDIChildWnd` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMDIChildWnd::Create](#create)|Tworzy okno podrzędne Windows MDI, które są skojarzone z `CMDIChildWnd` obiektu.|
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|Zwraca element nadrzędny MDI ramki okna MDI klienta.|
|[CMDIChildWnd::MDIActivate](#mdiactivate)|Aktywuje to okno podrzędne MDI.|
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|Niszczy to okno podrzędne MDI.|
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|Zapewnia to okno podrzędne MDI.|
|[CMDIChildWnd::MDIRestore](#mdirestore)|Przywraca to okno podrzędne MDI na podstawie rozmiaru w trybie zmaksymalizowanym lub w trybie zminimalizowanym.|
|[CMDIChildWnd::SetHandles](#sethandles)|Ustawia uchwytów dla zasobów menu i akcelerator.|

## <a name="remarks"></a>Uwagi

Okno podrzędne MDI wygląda podobnie jak okno typowej ramki, z tą różnicą, że wewnątrz okna ramki MDI zamiast na pulpicie pojawi się okno podrzędne MDI. Okno podrzędne MDI nie ma własnego paska menu, ale zamiast tego udostępnia menu okna ramki MDI. Struktura automatycznie zmieni menu ramki MDI do reprezentowania aktualnie aktywne okno podrzędne MDI.

Aby utworzyć użyteczne okno podrzędne MDI w aplikacji, należy wyprowadzić klasę z `CMDIChildWnd`. Dodaj zmienne do klasy pochodnej w celu przechowywania danych specyficznych dla aplikacji. Implementowanie obsługi wiadomości elementów członkowskich, a także wiadomość, mapowania w klasie pochodnej, aby określić, co się stanie, gdy komunikaty są kierowane do okna.

Istnieją trzy sposoby, aby utworzyć okno podrzędne MDI:

- Bezpośrednio utworzenia go za pomocą `Create`.

- Bezpośrednio utworzenia go za pomocą `LoadFrame`.

- Pośrednio jego konstruowania przy użyciu szablonu dokumentu.

Przed wywołaniem `Create` lub `LoadFrame`, należy utworzyć obiekt okno ramek na stosie przy użyciu języka C++ **nowe** operatora. Przed wywołaniem `Create` można zarejestrować klasy okna za pomocą [afxregisterwndclass —](application-information-and-management.md#afxregisterwndclass) funkcja globalna, aby ustawić ikonę i klasa style ramki.

Użyj `Create` funkcja elementu członkowskiego do przekazania parametrów tworzenia ramki natychmiastowego jako argumenty.

`LoadFrame` wymaga mniej argumentów niż `Create`i zamiast tego pobiera najbardziej jej wartości domyślnej z zasobów, w tym podpis ramki, ikony, tabeli akceleratora i menu. Dostępne przez `LoadFrame`, te zasoby musi mieć ten sam identyfikator zasobów (na przykład IDR_MAINFRAME).

Gdy `CMDIChildWnd` obiekt zawiera widoki i dokumentów, są tworzone bezpośrednio przez platformę, a nie bezpośrednio przez programistę. `CDocTemplate` Obiektu organizuje tworzenia ramki, tworzenie widoków zawierających i połączenie widoków do odpowiedniego dokumentu. Parametry `CDocTemplate` Określ Konstruktor `CRuntimeClass` trzy klasy zaangażowana (dokument, ramki i widoku). A `CRuntimeClass` obiekt jest używany przez platformę do dynamicznego tworzenia nowych ramek, gdy określony przez użytkownika (na przykład przy użyciu polecenia nowy plik lub nowego okna MDI polecenia).

Pochodne klasy okien ramowych `CMDIChildWnd` musi być zadeklarowany z DECLARE_DYNCREATE w kolejności dla powyższych mechanizmu RUNTIME_CLASS działała prawidłowo.

`CMDIChildWnd` Klasa dziedziczy większość jego domyślna implementacja z `CFrameWnd`. Aby uzyskać szczegółową listę z tych funkcji, zapoznaj się [CFrameWnd](../../mfc/reference/cframewnd-class.md) klasy opis. `CMDIChildWnd` Klasa ma następujące dodatkowe funkcje:

- W połączeniu z `CMultiDocTemplate` klasy, wiele `CMDIChildWnd` obiektów z tego samego szablonu dokumentu udostępnianie tego samego menu, zapisywanie zasobów systemu Windows.

- Aktualnie aktywne menu okno podrzędne MDI całkowicie zastępuje menu okna ramki MDI i podpis aktualnie aktywne okno podrzędne MDI jest dodawany do tytuł okna ramki MDI. Dalsze przykłady funkcje okna podrzędnego MDI, które są implementowane w połączeniu z okna ramki MDI, zobacz `CMDIFrameWnd` klasy opis.

Nie należy używać języka C++ **Usuń** operator można zniszczyć okna ramki. Zamiast nich należy używać słów kluczowych `CWnd::DestroyWindow`. `CFrameWnd` Implementacji `PostNcDestroy` spowoduje usunięcie obiektu języka C++, kiedy niszczony jest okna. Gdy użytkownik zamknie okno ramowe domyślnie `OnClose` wywoła procedurę obsługi `DestroyWindow`.

Aby uzyskać więcej informacji na temat `CMDIChildWnd`, zobacz [Windows ramki](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="cmdichildwnd"></a>  CMDIChildWnd::CMDIChildWnd

Wywołania do konstruowania `CMDIChildWnd` obiektu.

```
CMDIChildWnd();
```

### <a name="remarks"></a>Uwagi

Wywołaj `Create` można utworzyć okna widoczne.

### <a name="example"></a>Przykład

  Zobacz przykład [CMDIChildWnd::Create](#create).

##  <a name="create"></a>  CMDIChildWnd::Create

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć okno podrzędne Windows MDI i dołączyć go do `CMDIChildWnd` obiektu.

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
Wskazuje ciąg znaków zakończony znakiem null, że nazwy klas Windows ( [WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa) struktury). Nazwa klasy może być dowolna nazwa, zarejestrowane w usłudze [afxregisterwndclass —](application-information-and-management.md#afxregisterwndclass) funkcja globalna. Powinna być równa NULL dla standardowego `CMDIChildWnd`.

*lpszWindowName*<br/>
Wskazuje ciąg znaków zakończony znakiem null, który reprezentuje nazwę okna. Używane jako tekst, na pasku tytułu.

*dwStyle*<br/>
Określa okna [styl](../../mfc/reference/styles-used-by-mfc.md#window-styles) atrybutów. Styl WS_CHILD jest wymagana.

*Rect*<br/>
Zawiera rozmiar i położenie okna. `rectDefault` Zezwala na wartość Windows określić rozmiar i położenie nowej `CMDIChildWnd`.

*pParentWnd*<br/>
Określa okna nadrzędnego. Jeśli ma wartość NULL, jest używany w głównym oknie aplikacji.

*pContext*<br/>
Określa [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury. Ten parametr może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aktualnie aktywnego oknem ramki podrzędnego MDI można określić napis nadrzędnej ramki okna. Ta funkcja jest wyłączona, wyłączając bitu stylu FWS_ADDTOTITLE ramki okna podrzędnego.

Struktura wywołuje tej funkcji elementu członkowskiego w odpowiedzi na polecenie użytkownika, można utworzyć okna podrzędnego, a środowisko wykorzystuje *pContext* parametru, aby prawidłowo nawiązania okna podrzędnego aplikacją. Gdy wywołujesz `Create`, *pContext* może mieć wartości NULL.

### <a name="example"></a>Przykład

Przykład 1:

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>Przykład

Przykład 2:

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

##  <a name="getmdiframe"></a>  CMDIChildWnd::GetMDIFrame

Wywołaj tę funkcję, aby zwrócić nadrzędnej ramki MDI.

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nadrzędnego okna MDI ramki.

### <a name="remarks"></a>Uwagi

Ramki, zwracany jest dwóch elementów nadrzędnych usunięte z `CMDIChildWnd` a jest nadrzędne względem okna typu MDICLIENT, która zarządza `CMDIChildWnd` obiektu. Wywołaj [getparent —](../../mfc/reference/cwnd-class.md#getparent) funkcja elementu członkowskiego zwraca `CMDIChildWnd` natychmiastowego MDICLIENT elementu nadrzędnego obiektu jako tymczasowy `CWnd` wskaźnika.

### <a name="example"></a>Przykład

  Zobacz przykład [CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).

##  <a name="mdiactivate"></a>  CMDIChildWnd::MDIActivate

Wywołaj tę funkcję elementu członkowskiego, aby aktywować okno podrzędne MDI niezależnie od oknem ramki aplikacji MDI.

```
void MDIActivate();
```

### <a name="remarks"></a>Uwagi

Podczas uaktywniania ramki okna podrzędnego, który został ostatnio aktywowany zostanie również aktywowane.

### <a name="example"></a>Przykład

  Zobacz przykład [CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).

##  <a name="mdidestroy"></a>  CMDIChildWnd::MDIDestroy

Wywołaj tę funkcję elementu członkowskiego, aby zniszczyć okno podrzędne MDI.

```
void MDIDestroy();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego usuwa tytuł okna podrzędnego z oknem ramki i dezaktywuje okna podrzędnego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

##  <a name="mdimaximize"></a>  CMDIChildWnd::MDIMaximize

Wywołaj tę funkcję elementu członkowskiego, aby zmaksymalizować okno podrzędne MDI.

```
void MDIMaximize();
```

### <a name="remarks"></a>Uwagi

Jeśli okno podrzędne jest zmaksymalizowane, zmienia rozmiar Windows, aby wypełnił obszar klienta okna ramki obszaru klienckiego. Windows umieszcza okno podrzędne formant menu na pasku menu ramki tak, aby użytkownik może przywrócić lub zamknąć okno podrzędne i dodaje tytuł okna podrzędnego do tytułu ramki okna.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

##  <a name="mdirestore"></a>  CMDIChildWnd::MDIRestore

Wywołaj tę funkcję elementu członkowskiego, aby przywrócić okno podrzędne MDI od rozmiaru w trybie zmaksymalizowanym lub w trybie zminimalizowanym.

```
void MDIRestore();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

##  <a name="sethandles"></a>  CMDIChildWnd::SetHandles

Ustawia uchwytów dla zasobów menu i akcelerator.

```
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
Uchwyt zasobu menu.

*hAccel*<br/>
Uchwyt zasób akceleratora.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby ustawić menu i akcelerator zasoby używane przez obiekt okna podrzędnego MDI.

## <a name="see-also"></a>Zobacz także

[Próbki MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Próbki MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Próbki MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)
