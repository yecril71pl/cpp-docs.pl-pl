---
title: Klasa CMiniFrameWnd
ms.date: 11/04/2016
f1_keywords:
- CMiniFrameWnd
- AFXWIN/CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::Create
- AFXWIN/CMiniFrameWnd::CreateEx
helpviewer_keywords:
- CMiniFrameWnd [MFC], CMiniFrameWnd
- CMiniFrameWnd [MFC], Create
- CMiniFrameWnd [MFC], CreateEx
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
ms.openlocfilehash: e9b91161f4207f4d2215d8777beade93617ddfac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319817"
---
# <a name="cminiframewnd-class"></a>Klasa CMiniFrameWnd

Reprezentuje okno ramy o połowie wysokości, zwykle widoczne wokół ruchomych pasków narzędzi.

## <a name="syntax"></a>Składnia

```
class CMiniFrameWnd : public CFrameWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|Konstruuje `CMiniFrameWnd` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMiniFrameWnd::Tworzenie](#create)|Tworzy `CMiniFrameWnd` obiekt po zakończeniu budowy.|
|[CMiniFrameWnd::CreateEx](#createex)|Tworzy `CMiniFrameWnd` obiekt (z dodatkowymi opcjami) po zakończeniu budowy.|

## <a name="remarks"></a>Uwagi

Te okna mini-frame zachowują się jak normalne okna ramki, z tą różnicą, że nie mają zminimalizować / zmaksymalizować przyciski lub menu i trzeba tylko jednoklik na menu systemowym, aby je odrzucić.

Aby użyć `CMiniFrameWnd` obiektu, należy najpierw zdefiniować obiekt. Następnie zadzwoń do funkcji [Utwórz](#create) element członkowski, aby wyświetlić okno mini-ramki.

Aby uzyskać więcej informacji `CMiniFrameWnd` na temat używania obiektów, zobacz artykuł [Dokowanie i przestawne paski narzędzi](../../mfc/docking-and-floating-toolbars.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cminiframewndcminiframewnd"></a><a name="cminiframewnd"></a>CMiniFrameWnd::CMiniFrameWnd

Konstruuje `CMiniFrameWnd` obiekt, ale nie tworzy okna.

```
CMiniFrameWnd();
```

### <a name="remarks"></a>Uwagi

Aby utworzyć okno, zadzwoń do [CMiniFrameWnd::Create](#create).

## <a name="cminiframewndcreate"></a><a name="create"></a>CMiniFrameWnd::Tworzenie

Tworzy okno miniklatka systemu Windows `CMiniFrameWnd` i dołącza je do obiektu.

```
virtual BOOL Create(
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>Parametry

*lpClassName (nazwa klasy lp)*<br/>
Wskazuje ciąg znaków zakończony z wartością null, który nazywa klasę systemu Windows. Nazwa klasy może być dowolną nazwą zarejestrowaną za pomocą globalnej funkcji [AfxRegisterWndClass.](application-information-and-management.md#afxregisterwndclass) Jeśli NULL, klasa okna zostanie zarejestrowana dla Ciebie przez platformę. MFC daje klasy domyślnej następujące style i atrybuty:

- Ustawia styl CS_DBLCLKS bitowy, który wysyła wiadomości dwukrotnego kliknięcia do procedury okna, gdy użytkownik kliknie dwukrotnie myszą.

- Ustawia bity stylu CS_HREDRAW i CS_VREDRAW, które kierują zawartość obszaru klienta do ponownego narysowania, gdy okno zmieni rozmiar.

- Ustawia kursor klasy na standardowy IDC_ARROW systemu Windows.

- Ustawia pędzel tła klasy na NULL, więc okno nie spowoduje wymazania jego tła.

- Ustawia ikonę klasy na standardową ikonę logo systemu Windows z flagą machającą flagą.

- Ustawia domyślny rozmiar i położenie okna, zgodnie z wskazywanymi przez system Windows.

*lpWindowName*<br/>
Wskazuje ciąg znaków zakończony z wartością null, który zawiera nazwę okna.

*Dwstyle*<br/>
Określa atrybuty stylu okna. Mogą to być standardowe style okien i co najmniej jeden z następujących stylów specjalnych:

- MFS_MOVEFRAME Umożliwia przeniesienie okna mini-ramki przez kliknięcie dowolnej krawędzi okna, a nie tylko podpisu.

- MFS_4THICKFRAME Wyłącza zmiany rozmiaru okna mini-ramki.

- MFS_SYNCACTIVE Synchronizuje aktywację okna mini-ramki z aktywacją okna nadrzędnego.

- MFS_THICKFRAME Umożliwia rozmiar okna mini-ramki tak mały, jak pozwala na to zawartość obszaru klienta.

- MFS_BLOCKSYSMENU Wyłącza dostęp do menu systemowego i menu sterowania i konwertuje je na część podpisu (pasek tytułu).

Zobacz [CWnd::Tworzenie](../../mfc/reference/cwnd-class.md#create) opisu możliwych wartości stylu okna. Typowa kombinacja używana do okien mini-ramki jest WS_POPUP&#124;WS_CAPTION&#124;WS_SYSMENU.

*Rect*<br/>
Struktura `RECT` określająca żądane wymiary okna.

*pParentWnd*<br/>
Wskazuje okno nadrzędne. Użyj wartości NULL dla okien najwyższego poziomu.

*Nid*<br/>
Jeśli okno mini-ramki jest tworzony jako okno podrzędne, jest to identyfikator formantu podrzędnego; w przeciwnym razie 0.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`Create`inicjuje nazwę klasy okna i nazwę okna i rejestruje wartości domyślne dla jego stylu i nadrzędnego.

## <a name="cminiframewndcreateex"></a><a name="createex"></a>CMiniFrameWnd::CreateEx

Tworzy obiekt `CMiniFrameWnd`.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>Parametry

*Dwexstyle*<br/>
Określa rozszerzony styl tworzonego. `CMiniFrameWnd` Zastosuj dowolny z [rozszerzonych stylów okien](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) do okna.

*lpClassName (nazwa klasy lp)*<br/>
Wskazuje ciąg znaków zakończony z wartością null, który nazywa klasę systemu Windows (strukturę [WNDCLASS).](/windows/win32/api/winuser/ns-winuser-wndclassw) Nazwa klasy może być dowolną nazwą zarejestrowaną za pomocą globalnej funkcji [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) lub dowolnej ze wstępnie zdefiniowanych nazw klasy kontrolnej. Nie może być null.

*lpWindowName*<br/>
Wskazuje ciąg znaków zakończony z wartością null, który zawiera nazwę okna.

*Dwstyle*<br/>
Określa atrybuty stylu okna. Zobacz [Style okien](../../mfc/reference/styles-used-by-mfc.md#window-styles) i [CWnd::Tworzenie](../../mfc/reference/cwnd-class.md#create) opisu możliwych wartości.

*Rect*<br/>
Rozmiar i położenie okna, we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskazuje obiekt okna nadrzędnego.

*Nid*<br/>
Identyfikator okna podrzędnego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Parametry `CreateEx` określają WNDCLASS, styl okna i (opcjonalnie) początkowe położenie i rozmiar okna. `CreateEx`określa również element nadrzędny okna (jeśli istnieje) i identyfikator.

Podczas `CreateEx` wykonywania system Windows wysyła do okna [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) [, WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)i [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) wiadomości.

Aby rozszerzyć domyślną obsługę wiadomości, `CMiniFrameWnd`należy wyprowadzić klasę z , dodać mapę wiadomości do nowej klasy i zapewnić funkcje członkowskie dla powyższych wiadomości. Zastąd w celu wykonania wymaganej inicjalizacji `OnCreate`dla nowej klasy.

Zastąpić dalsze `On` *programy* obsługi wiadomości, aby dodać dalsze funkcje do klasy pochodnej.

Jeśli podany jest styl WS_VISIBLE, system Windows wysyła do okna wszystkie komunikaty wymagane do aktywacji i wyświetlenia okna. Jeśli styl okna określa pasek tytułu, tytuł okna wskazywał parametr *lpszWindowName* na pasku tytułu.

Parametrem *dwStyle* może być dowolna kombinacja [stylów okien](../../mfc/reference/styles-used-by-mfc.md#window-styles).

Stare okna przybornika palety stylu nie są już obsługiwane. Stary styl, który nie miał przycisku "X" Zamknij, był obsługiwany podczas uruchamiania aplikacji MFC w poprzednich wersjach systemu Windows, ale nie jest już obsługiwany w programie Visual C++.NET. Tylko nowy styl WS_EX_TOOLWINDOW jest teraz obsługiwany; aby uzyskać opis tego stylu, zobacz [Style okien rozszerzonych](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

## <a name="see-also"></a>Zobacz też

[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)
