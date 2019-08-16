---
title: 'TN001: Rejestracja klasy okna'
ms.date: 11/04/2016
f1_keywords:
- vc.registration
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
ms.openlocfilehash: 95e35ddd6f55c955bc2adb7b4db2460ae84a6dc7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513548"
---
# <a name="tn001-window-class-registration"></a>TN001: Rejestracja klasy okna

Ta Uwaga opisuje procedury MFC, które rejestrują specjalne [WNDCLASSy](/windows/win32/api/winuser/ns-winuser-wndclassw), które są niezbędne w systemie Microsoft Windows. Omówione `WNDCLASS` są określone atrybuty używane przez MFC i Windows.

## <a name="the-problem"></a>Problem

Atrybuty obiektu [CWnd](../mfc/reference/cwnd-class.md) , takie jak `HWND` uchwyt w systemie Windows, są przechowywane w dwóch miejscach: obiekt `WNDCLASS`Window i. Nazwa `WNDCLASS` jest przenoszona do ogólnych funkcji tworzenia okna, takich jak [CWnd:: Create](../mfc/reference/cwnd-class.md#create) i [obiektu CFrameWnd:: Create](../mfc/reference/cframewnd-class.md#create) w parametrze *lpszClassName* .

Ta `WNDCLASS` Metoda musi być zarejestrowana w jednym z czterech:

- Niejawnie przy użyciu dostarczonej `WNDCLASS`biblioteki MFC.

- Niejawnie przez podklasy kontrolki systemu Windows (lub innej kontrolki).

- Jawnie przez wywołanie MFC [AfxRegisterWndClass —](../mfc/reference/application-information-and-management.md#afxregisterwndclass) lub [AfxRegisterClass](../mfc/reference/application-information-and-management.md#afxregisterclass).

- Jawnie przez wywołanie procedury systemu Windows [RegisterClass](/windows/win32/api/winuser/nf-winuser-registerclassw).

## <a name="wndclass-fields"></a>Pola WNDCLASS

`WNDCLASS` Struktura składa się z różnych pól, które opisują klasę okna. W poniższej tabeli przedstawiono pola i sposób ich użycia w aplikacji MFC:

|Pole|Opis|
|-----------|-----------------|
|*lpfnWndProc*|proces okna musi być`AfxWndProc`|
|*cbClsExtra*|nieużywane (wartość powinna być równa zero)|
|*cbWndExtra*|nieużywane (wartość powinna być równa zero)|
|*hInstance*|automatycznie wypełnione [AfxGetInstanceHandle](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|
|*hIcon*|ikona dla okien ramowych, patrz poniżej|
|*hCursor*|kursor, gdy wskaźnik myszy znajduje się nad oknem, patrz poniżej|
|*hbrBackground*|kolor tła, zobacz poniżej|
|*lpszMenuName*|nieużywane (powinno mieć wartość NULL)|
|*lpszClassName*|Nazwa klasy, zobacz poniżej.|

## <a name="provided-wndclasses"></a>Podano WNDCLASSes

Starsze wersje MFC (przed MFC 4,0), dostarczyły kilka wstępnie zdefiniowanych klas okien. Te klasy okien nie są już domyślnie udostępniane. Aplikacje powinny być `AfxRegisterWndClass` używane z odpowiednimi parametrami.

Jeśli aplikacja udostępnia zasób o określonym IDENTYFIKATORze zasobu (na przykład AFX_IDI_STD_FRAME), MFC będzie używać tego zasobu. W przeciwnym razie użyje zasobu domyślnego. W przypadku ikony zostanie użyta ikona standardowej aplikacji, a dla kursora zostanie użyty standardowy kursor strzałek.

Dwie ikony obsługują aplikacje MDI o pojedynczym typie dokumentu: jedną ikonę dla aplikacji głównej, drugą ikonę dla okna Dokument z ikonami/MDIChild. Dla wielu typów dokumentów z różnymi ikonami należy zarejestrować dodatkowe `WNDCLASS`es lub użyć funkcji [obiektu CFrameWnd:: LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) .

`CFrameWnd::LoadFrame`spowoduje zarejestrowanie `WNDCLASS` się przy użyciu identyfikatora ikony, który jest określany jako pierwszy parametr i następujące atrybuty standardowe:

- styl klasy: CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW;

- icon AFX_IDI_STD_FRAME

- kursor strzałki

- Kolor tła COLOR_WINDOW

Wartości koloru tła i kursora dla [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) nie są używane, ponieważ obszar `CMDIFrameWnd` klienta jest całkowicie objęty oknem **MDICLIENT** . Firma Microsoft nie zachęca do podklasy okna **MDICLIENT** , więc używaj standardowych kolorów i typów kursorów, gdy jest to możliwe.

## <a name="subclassing-and-superclassing-controls"></a>Podklasy i kontrolki superklasy

Jeśli podklasa lub Superklasa jest formantem systemu Windows (na przykład [CButton](../mfc/reference/cbutton-class.md)), Klasa automatycznie pobiera `WNDCLASS` atrybuty podane w implementacji systemu Windows.

## <a name="the-afxregisterwndclass-function"></a>Funkcja AfxRegisterWndClass —

MFC udostępnia funkcję pomocnika do rejestracji klasy okna. Po otrzymaniu zestawu atrybutów (stylu klasy okna, kursora, pędzla tła i ikony) jest generowana nazwa syntetyczna, a powstała Klasa okna jest zarejestrowana. Na przykład

```
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```

Ta funkcja zwraca tymczasowy ciąg wygenerowanej nazwy klasy okna zarejestrowanej. Aby uzyskać więcej informacji na temat tej funkcji, zobacz [AfxRegisterWndClass —](../mfc/reference/application-information-and-management.md#afxregisterwndclass).

Zwrócony ciąg jest tymczasowym wskaźnikiem do statycznego buforu ciągu. Jest on ważny do momentu następnego wywołania `AfxRegisterWndClass`do. Jeśli chcesz zachować ten ciąg, Zapisz go w zmiennej [CString](../atl-mfc-shared/using-cstring.md) , jak w poniższym przykładzie:

```
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...
CWnd* pWnd = new CWnd;
pWnd->Create(strWndClass, ...);

...
```

`AfxRegisterWndClass`wygeneruje [CResourceException](../mfc/reference/cresourceexception-class.md) , jeśli nie można zarejestrować klasy okna (z powodu nieprawidłowych parametrów lub z pamięci systemu Windows).

## <a name="the-registerclass-and-afxregisterclass-functions"></a>Funkcje RegisterClass i AfxRegisterClass

Jeśli chcesz zrobić coś bardziej, niż to `AfxRegisterWndClass` możliwe, możesz wywołać interfejs API `RegisterClass` systemu Windows lub funkcję `AfxRegisterClass`MFC. [](../mfc/reference/cmdichildwnd-class.md) `Create` [](../mfc/reference/cframewnd-class.md) Funkcje, obiektu CFrameWnd i CMDIChildWnd przyjmują nazwę ciągu lpszClassName dla klasy Window jako pierwszy parametr. `CWnd` Możesz użyć dowolnej nazwy klasy okna, niezależnie od metody użytej do zarejestrowania.

Ważne jest użycie `AfxRegisterClass` (lub `AfxRegisterWndClass`) w bibliotece DLL w systemie Win32. Win32 nie wyrejestruje automatycznie klas zarejestrowanych przez bibliotekę DLL, więc musisz jawnie wyrejestrować klasy, gdy biblioteka DLL zostanie przerwana. `AfxRegisterClass` Użycie`RegisterClass` zamiast tego jest obsługiwane automatycznie. `AfxRegisterClass`zachowuje listę unikatowych klas zarejestrowanych przez bibliotekę DLL i automatycznie wyrejestrowuje je po zakończeniu działania biblioteki DLL. W przypadku korzystania `RegisterClass` z programu w bibliotece DLL, należy się upewnić, że wszystkie klasy są wyrejestrowane, gdy biblioteka DLL zostanie zakończona (w funkcji [DllMain](/windows/win32/Dlls/dllmain) ). Niewykonanie tej czynności może spowodować `RegisterClass` nieoczekiwane niepowodzenie, gdy inna aplikacja kliencka próbuje użyć biblioteki DLL.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
