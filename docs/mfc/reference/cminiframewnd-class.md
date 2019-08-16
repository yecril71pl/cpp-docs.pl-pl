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
ms.openlocfilehash: 45b4698cc70487a6c3fe1470fe27f7b5c4f95402
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504602"
---
# <a name="cminiframewnd-class"></a>Klasa CMiniFrameWnd

Przedstawia okno ramki o połowie wysokości zwykle widoczne wokół przestawnych pasków narzędzi.

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
|[CMiniFrameWnd:: Create](#create)|`CMiniFrameWnd` Tworzy obiekt po konstrukcji.|
|[CMiniFrameWnd::CreateEx](#createex)|`CMiniFrameWnd` Tworzy obiekt (z dodatkowymi opcjami) po konstrukcji.|

## <a name="remarks"></a>Uwagi

Te okna ze minią ramką zachowują się jak normalne okna ramowe, z tą różnicą, że nie mają przycisków minimalizowania/maksymalizowania lub menu i wystarczy tylko jednokrotne kliknięcie menu systemowego, aby je zamknąć.

Aby użyć `CMiniFrameWnd` obiektu, najpierw Zdefiniuj obiekt. Następnie wywołaj funkcję [Utwórz](#create) element członkowski, aby wyświetlić okno mini-frame.

Aby uzyskać więcej informacji na temat używania `CMiniFrameWnd` obiektów, zobacz artykuł [dokowanie i przestawne paski narzędzi](../../mfc/docking-and-floating-toolbars.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[Obiektu CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="cminiframewnd"></a>CMiniFrameWnd::CMiniFrameWnd

Konstruuje `CMiniFrameWnd` obiekt, ale nie tworzy okna.

```
CMiniFrameWnd();
```

### <a name="remarks"></a>Uwagi

Aby utworzyć okno, wywołaj [CMiniFrameWnd:: Create](#create).

##  <a name="create"></a>CMiniFrameWnd:: Create

Tworzy okno Windows mini frame i dołącza je do `CMiniFrameWnd` obiektu.

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

*lpClassName*<br/>
Wskazuje ciąg znaków zakończony znakiem null, który nazywa klasę systemu Windows. Nazwa klasy może być dowolną nazwą zarejestrowana w globalnej funkcji [AfxRegisterWndClass —](application-information-and-management.md#afxregisterwndclass) . Jeśli wartość jest równa NULL, Klasa okna zostanie zarejestrowana przez strukturę. MFC przypisuje klasie domyślnej następujące style i atrybuty:

- Ustawia wartość Style bit CS_DBLCLKS, która wysyła wiadomości dwukrotnego kliknięcia do procedury okna, gdy użytkownik kliknie dwukrotnie mysz.

- Ustawia bity w stylu CS_HREDRAW i CS_VREDRAW, który kieruje zawartość obszaru klienta do odrysowania, gdy zmienia się rozmiar okna.

- Ustawia kursor klasy w standardowym IDC_ARROW systemu Windows.

- Ustawia Pędzel tła klasy na wartość NULL, więc okno nie wymazuje jego tła.

- Ustawia ikonę klasy na ikonę standardowego, Waving flagi logo systemu Windows.

- Ustawia domyślny rozmiar i położenie okna, jak wskazano w systemie Windows.

*lpWindowName*<br/>
Wskazuje ciąg znaków zakończony znakiem null, który zawiera nazwę okna.

*dwStyle*<br/>
Określa atrybuty stylu okna. Mogą to być standardowe style okna i co najmniej jeden z następujących stylów specjalnych:

- MFS_MOVEFRAME umożliwia przenoszenie okna mini-frame przez kliknięcie dowolnej krawędzi okna, a nie tylko podpisu.

- MFS_4THICKFRAME wyłącza zmianę rozmiarów okna mini-frame.

- MFS_SYNCACTIVE synchronizuje aktywację okna mini-frame do aktywacji okna nadrzędnego.

- MFS_THICKFRAME umożliwia rozmiar okna mini-frame jako niewielkich, ponieważ zawartość obszaru klienckiego jest dozwolona.

- MFS_BLOCKSYSMENU wyłącza dostęp do menu systemowego i menu sterowania i konwertuje je na część podpisu (pasek tytułu).

Aby uzyskać opis możliwych wartości stylu okna, zobacz [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) . Typową kombinacją dla okien mini-frame jest WS_POPUP&#124;WS_CAPTION&#124;WS_SYSMENU.

*cinania*<br/>
`RECT` Struktura określająca żądane wymiary okna.

*pParentWnd*<br/>
Wskazuje okno nadrzędne. Użyj wartości NULL dla okien najwyższego poziomu.

*nID*<br/>
Jeśli okno mini-frame jest tworzone jako okno podrzędne, jest to identyfikator kontrolki podrzędnej. w przeciwnym razie 0.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`Create`Inicjuje nazwę klasy okna i nazwę okna i rejestruje wartości domyślne dla jego stylu i elementu nadrzędnego.

##  <a name="createex"></a>CMiniFrameWnd::CreateEx

`CMiniFrameWnd` Tworzy obiekt.

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

*dwExStyle*<br/>
Określa rozszerzony styl tworzonego elementu `CMiniFrameWnd` . Zastosuj dowolny z [rozszerzonych stylów okna](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) do okna.

*lpClassName*<br/>
Wskazuje ciąg znaków zakończony znakiem null, który nazywa klasę systemu Windows (struktura [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) ). Nazwa klasy może być dowolną nazwą zarejestrowanej przy użyciu globalnej funkcji [AfxRegisterWndClass —](application-information-and-management.md#afxregisterwndclass) lub dowolnych wstępnie zdefiniowanych nazw klas kontrolek. Nie może mieć wartości NULL.

*lpWindowName*<br/>
Wskazuje ciąg znaków zakończony znakiem null, który zawiera nazwę okna.

*dwStyle*<br/>
Określa atrybuty stylu okna. Zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) i [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) , aby uzyskać opis możliwych wartości.

*cinania*<br/>
Rozmiar i położenie okna we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskazuje obiekt nadrzędny okna.

*nID*<br/>
Identyfikator okna podrzędnego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

`CreateEx` Parametry określają WNDCLASS, styl okna i (opcjonalnie) początkową pozycję i rozmiar okna. `CreateEx`określa również element nadrzędny (jeśli istnieje) okna i identyfikator.

Gdy `CreateEx` jest wykonywane, system Windows wysyła do okna komunikaty [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo), [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)i [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) .

Aby zwiększyć domyślną obsługę komunikatów, należy utworzyć klasę z `CMiniFrameWnd`, dodać do nowej klasy mapę komunikatów i udostępnić funkcje elementów członkowskich dla powyższych komunikatów. Przesłoń `OnCreate`, na przykład, aby wykonać wymaganą inicjalizację dla nowej klasy.

Przesłoń `On`dalsze procedury obsługi komunikatów *komunikatów* , aby dodać dalsze funkcje do klasy pochodnej.

Jeśli podano styl WS_VISIBLE, system Windows wysyła wszystkie komunikaty wymagane do aktywowania i wyświetlenia okna. Jeśli styl okna określa pasek tytułu, na pasku tytułu zostanie wyświetlony tytuł okna wskazywany przez parametr *lpszWindowName* .

Parametr *dwStyle* może być dowolną kombinacją [stylów okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).

Okna przybornika palety stylów starego stylu nie są już obsługiwane. Stary styl, który nie ma przycisku zamknięcia "X", był obsługiwany podczas uruchamiania aplikacji MFC w poprzednich wersjach systemu Windows, ale nie jest już obsługiwany w programie Visual C++.NET. Obsługiwany jest tylko nowy styl WS_EX_TOOLWINDOW; Opis tego stylu można znaleźć w sekcji [Style okna rozszerzonego](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

## <a name="see-also"></a>Zobacz także

[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)
