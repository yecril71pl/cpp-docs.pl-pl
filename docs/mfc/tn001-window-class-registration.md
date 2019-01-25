---
title: 'TN001: Rejestrowanie klasy okna'
ms.date: 11/04/2016
f1_keywords:
- vc.registration
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
ms.openlocfilehash: 4ae94d1c9c57f6c315ae482e44576ae25194c00f
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894266"
---
# <a name="tn001-window-class-registration"></a>TN001: Rejestrowanie klasy okna

Ta uwaga opisuje procedury MFC, które rejestrują specjalne [WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa)es wymagane przez program Microsoft Windows. Określone `WNDCLASS` omówiono atrybuty używane przez MFC i Windows.

## <a name="the-problem"></a>Ten Problem

Atrybuty [CWnd](../mfc/reference/cwnd-class.md) obiektu, takie jak `HWND` obsługi w Windows, są przechowywane w dwóch miejscach: obiekt okna i `WNDCLASS`. Nazwa `WNDCLASS` jest przekazywany do funkcji tworzenia ogólnego okna, takie jak [CWnd::Create](../mfc/reference/cwnd-class.md#create) i [CFrameWnd::Create](../mfc/reference/cframewnd-class.md#create) w *lpszClassName* parametru.

To `WNDCLASS` musi być zarejestrowana za pomocą jednego z czterech sposobów:

- Niejawnie, przy użyciu MFC, pod warunkiem `WNDCLASS`.

- Niejawnie przez tworzenie podklasy kontrolki Windows (lub niektóre inne kontrolki).

- Jawnie, wywołując MFC [afxregisterwndclass —](../mfc/reference/application-information-and-management.md#afxregisterwndclass) lub [afxregisterclass —](../mfc/reference/application-information-and-management.md#afxregisterclass).

- Jawnie, wywołując procedurę Windows [RegisterClass](/windows/desktop/api/winuser/nf-winuser-registerclassa).

## <a name="wndclass-fields"></a>Pola WNDCLASS

`WNDCLASS` Struktury składa się z różnych pól, które opisują klasy okna. W poniższej tabeli przedstawiono pola i określa, jak są używane w aplikacji MFC:

|Pole|Opis|
|-----------|-----------------|
|*lpfnWndProc*|proces okna musi być `AfxWndProc`|
|*cbClsExtra*|nieużywane (powinna wynosić zero)|
|*cbWndExtra*|nieużywane (powinna wynosić zero)|
|*hInstance*|automatycznie wypełnione [afxgetinstancehandle —](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|
|*hIcon*|Poniżej przedstawiono ikonę okien ramowych|
|*hCursor*|Poniżej przedstawiono kursora dla gdy kursor znajduje się nad okno,|
|*hbrBackground*|kolor tła, znajduje się poniżej|
|*lpszMenuName*|nieużywane (powinna być równa NULL)|
|*lpszClassName*|Nazwa klasy, znajduje się poniżej|

## <a name="provided-wndclasses"></a>Podany WNDCLASSes

Wcześniejszych wersjach programu MFC (przed MFC 4.0), pod warunkiem kilka wstępnie zdefiniowanych klas okien. Domyślnie nie są już dostępne są te klasy okna. Aplikacje powinny używać `AfxRegisterWndClass` z odpowiednimi parametrami.

Jeśli aplikacja udostępnia zasób o określonym identyfikatorze zasobu (na przykład AFX_IDI_STD_FRAME), MFC użyje tego zasobu. W przeciwnym razie zostanie użyty domyślny zasób. Ikony ikona standardowej aplikacji jest używana i kursora, jest używany kursora standardowa strzałki.

Dwie ikony obsługuje aplikacje MDI za pomocą pojedynczego dokumentu typów: jedna ikona dla aplikacji głównej, inne ikony dla ikony dokumentu/MDIChild systemu windows. Dla wielu typów dokumentów z różnych ikonami, musisz się zarejestrować, dodatkowe `WNDCLASS`ak lub użyj [CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) funkcji.

`CFrameWnd::LoadFrame` zarejestruje `WNDCLASS` przy użyciu Identyfikatora ikonę, można określić jako pierwszego parametru i standardowe następujące atrybuty:

- style klasy: CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW;

- icon AFX_IDI_STD_FRAME

- Strzałka kursora

- Kolor tła COLOR_WINDOW

Wartości koloru tła i kursora dla [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) nie są używane od obszaru klienckiego `CMDIFrameWnd` całkowicie jest objęta **MDICLIENT** okna. Microsoft nie będzie zachęcać do podklasy **MDICLIENT** okna, dlatego użyty kolory standardowe i typy kursora, gdy jest to możliwe.

## <a name="subclassing-and-superclassing-controls"></a>Podklasy i Superclassing formantów

Jeśli możesz podklasy lub superklasie Windows kontrolować (na przykład [CButton](../mfc/reference/cbutton-class.md)), a następnie automatycznie pobiera klasy `WNDCLASS` atrybutów w implementacji Windows tej kontrolki.

## <a name="the-afxregisterwndclass-function"></a>The AfxRegisterWndClass Function

MFC udostępnia funkcję pomocnika dla rejestrowanie klasy okna. Biorąc pod uwagę zestaw atrybutów (styl klasy okna, kursor, Pędzel tła i ikony), zostanie wygenerowana nazwa syntetycznych, a wynikowe klasy okna jest zarejestrowany. Na przykład

```
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```

Ta funkcja zwraca ciąg tymczasowego wygenerowanego okna zarejestrowane nazwy klasy. Aby uzyskać więcej informacji na temat tej funkcji, zobacz [afxregisterwndclass —](../mfc/reference/application-information-and-management.md#afxregisterwndclass).

Zwracanego ciągu jest tymczasowy wskaźnik do buforu ciągu statyczne. Jest on prawidłowy aż do następnego wywołania metody `AfxRegisterWndClass`. Jeśli chcesz zachować ten ciąg wokół zapisać ją w [CString](../atl-mfc-shared/using-cstring.md) zmiennych, jak w poniższym przykładzie:

```
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...
CWnd* pWnd = new CWnd;
pWnd->Create(strWndClass, ...);

...
```

`AfxRegisterWndClass` zgłosi [CResourceException](../mfc/reference/cresourceexception-class.md) Jeśli klasy okna nie powiodło się zarejestrowanie (z powodu złych parametrów lub za mało pamięci Windows).

## <a name="the-registerclass-and-afxregisterclass-functions"></a>RegisterClass i afxregisterclass — funkcje

Jeśli chcesz to zaawansowane niczego więcej niż co `AfxRegisterWndClass` udostępnia, można wywołać interfejsu API Windows `RegisterClass` lub funkcji MFC `AfxRegisterClass`. `CWnd`, [CFrameWnd](../mfc/reference/cframewnd-class.md) i [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) `Create` funkcje podejmują *lpszClassName* nazwę ciągu dla klasy okna jako pierwszy parametr. Możesz użyć dowolnej nazwy klasy okna zarejestrowanych, niezależnie od metody użytej do zarejestrowania go.

Ważne jest, aby użyć `AfxRegisterClass` (lub `AfxRegisterWndClass`) w bibliotece DLL na Win32. Win32 nie automatycznie wyrejestrować klasy zarejestrowany przez bibliotekę DLL, aby jawnie musi wyrejestrować klas, gdy biblioteka DLL jest zakończony. Za pomocą `AfxRegisterClass` zamiast `RegisterClass` to odbywa się automatycznie dla Ciebie. `AfxRegisterClass` przechowuje listę klas unikatowy rejestrowane przez biblioteki DLL i automatycznie, aby wyrejestrować się je, gdy kończy się biblioteki DLL. Zastosowania `RegisterClass` w bibliotece DLL, upewnij się, wszystkie klasy są wyrejestrowany, jeśli biblioteka DLL jest zakończona (w Twojej [DllMain](/windows/desktop/Dlls/dllmain) funkcji). Niewykonanie tej czynności może powodować `RegisterClass` się nieoczekiwanie ulegają awarii, gdy inna aplikacja klienta próbuje użyć biblioteki DLL.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

