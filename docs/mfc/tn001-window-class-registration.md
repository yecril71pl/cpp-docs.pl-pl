---
title: 'TN001: Rejestracja klas okien | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.registration
dev_langs:
- C++
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e0be2e87f77e047e1b29d99e562a67bb9f4f1ee9
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951981"
---
# <a name="tn001-window-class-registration"></a>TN001: rejestracja klas okien
Ta uwaga opisano procedury MFC, które rejestrują specjalną [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)es wymagane przez program Microsoft Windows. Określone `WNDCLASS` omówiono atrybuty używane przez MFC i Windows.  
  
## <a name="the-problem"></a>Problem  
 Atrybuty [CWnd](../mfc/reference/cwnd-class.md) obiektu, takie jak `HWND` obsługi w systemie Windows, są przechowywane w dwóch miejscach: obiekt window i `WNDCLASS`. Nazwa `WNDCLASS` jest przekazywana do funkcji tworzenia okna ogólne, takich jak [CWnd::Create](../mfc/reference/cwnd-class.md#create) i [CFrameWnd::Create](../mfc/reference/cframewnd-class.md#create) w *lpszClassName* parametru.  
  
 To `WNDCLASS` musi być zarejestrowany za pomocą jednego z czterech oznacza, że:  
  
-   Niejawnie, przy użyciu MFC, pod warunkiem `WNDCLASS`.  
  
-   Niejawnie przez tworzenie podklasy kontrolki systemu Windows (lub pewne inne kontrolki).  
  
-   Jawnie, wywołując MFC [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) lub [afxregisterclass —](../mfc/reference/application-information-and-management.md#afxregisterclass).  
  
-   Jawnie, wywołując procedurę Windows [RegisterClass](http://msdn.microsoft.com/library/windows/desktop/ms633586).  
  
## <a name="wndclass-fields"></a>Pola WNDCLASS  
 `WNDCLASS` Struktury składa się z różnych pól, które opisują klasy okna. Poniższa tabela zawiera pola i określa, jak są używane w aplikacji MFC:  
  
|Pole|Opis|  
|-----------|-----------------|  
|*lpfnWndProc*|proces okna musi być `AfxWndProc`|  
|*cbClsExtra*|nieużywane (powinna wynosić zero)|  
|*cbWndExtra*|nieużywane (powinna wynosić zero)|  
|*hInstance*|automatycznie wypełnione [afxgetinstancehandle —](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|  
|*hIcon*|Poniżej dostępne ikonę okna ramowe|  
|*hCursor*|kursor dla gdy kursor znajduje się nad okno, zobacz poniżej|  
|*hbrBackground*|kolor tła, zobacz poniżej|  
|*lpszMenuName*|nieużywane (powinna być równa NULL)|  
|*lpszClassName*|Nazwa klasy, zobacz poniżej|  
  
## <a name="provided-wndclasses"></a>Podany WNDCLASSes  
 Starsze niż MFC (przed MFC 4.0), podać kilka wstępnie zdefiniowanych klas okien. Domyślnie te klasy okna nie jest już dostępne. Aplikacje powinny używać `AfxRegisterWndClass` z odpowiednimi parametrami.  
  
 Jeśli aplikacja zawiera zasób o identyfikatorze określonego zasobu (na przykład AFX_IDI_STD_FRAME), MFC będzie używać tego zasobu. W przeciwnym razie zostanie użyty domyślny zasób. Ikony ikony standardowej aplikacji jest używany, a kursora, kursor standardowe strzałka jest używany.  
  
 MDI — aplikacje z typami pojedynczego dokumentu obsługuje dwa ikony: jedna ikona dla aplikacji głównej, inne ikony dla ikony dokumentu/MDIChild systemu windows. Dla wielu typów dokumentów z ikonami różnych, należy zarejestrować dodatkowych `WNDCLASS`es lub użyj [CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) funkcji.  
  
 `CFrameWnd::LoadFrame` zarejestruje `WNDCLASS` za pomocą Identyfikatora ikonę można określić jako pierwszy parametr i standardowe następujące atrybuty:  
  
-   Klasa stylu: CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW;  
  
-   Ikona AFX_IDI_STD_FRAME  
  
-   Strzałka kursora  
  
-   Kolor tła COLOR_WINDOW  
  
 Wartości koloru tła i kursora dla [cmdiframewnd —](../mfc/reference/cmdiframewnd-class.md) nie są używane od obszaru klienckiego `CMDIFrameWnd` jest całkowicie objęte **MDICLIENT** okna. Microsoft nie zachęcać podklasy **MDICLIENT** okna tak użycie standardowe kolory i typów kursora, gdy jest to możliwe.  
  
## <a name="subclassing-and-superclassing-controls"></a>Podklasy i kontrolek tworzenie nadklas  
 Jeśli użytkownik podklasy lub superklasie systemu Windows kontrolują (na przykład [CButton](../mfc/reference/cbutton-class.md)), a następnie automatycznie pobiera klasy `WNDCLASS` atrybutów w implementację tego formantu.  
  
## <a name="the-afxregisterwndclass-function"></a>AfxRegisterWndClass — funkcja  
 Rejestrowanie klasy okna MFC zapewnia funkcję pomocnika. Mając do dyspozycji zestaw atrybutów (styl klasy okna, kursor pędzel tła i ikona), nazwę syntetycznych jest generowany, a wynikowa klasy okna jest zarejestrowany. Na przykład  
  
```  
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```  
  
 Ta funkcja zwraca ciąg tymczasowego wygenerowanego okna zarejestrowane nazwy klasy. Aby uzyskać więcej informacji dotyczących tej funkcji, zobacz [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass).  
  
 Zwrócony ciąg jest tymczasowy wskaźnika do buforu statyczny ciąg. Jest prawidłowy, aż do następnego wywołania `AfxRegisterWndClass`. Jeśli chcesz zachować ten ciąg wokół, zapisz go w [cstring —](../atl-mfc-shared/using-cstring.md) zmiennej, jak w poniższym przykładzie:  
  
```  
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...  
CWnd* pWnd = new CWnd;  
pWnd->Create(strWndClass, ...);

...  
```  
  
 `AfxRegisterWndClass` zgłosi [CResourceException](../mfc/reference/cresourceexception-class.md) Jeśli klasy okna nie można zarejestrować (z powodu złych parametrów lub za mało pamięci systemu Windows).  
  
## <a name="the-registerclass-and-afxregisterclass-functions"></a>RegisterClass i afxregisterclass — funkcje  
 Jeśli chcesz wykonać niczego bardziej zaawansowane opcje niż co `AfxRegisterWndClass` udostępnia, można wywołać interfejsu API systemu Windows `RegisterClass` lub funkcji MFC `AfxRegisterClass`. `CWnd`, [Cframewnd —](../mfc/reference/cframewnd-class.md) i [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) `Create` funkcje pobierać *lpszClassName* ciąg nazwę klasy okna jako pierwszym parametrem. Można użyć dowolnej nazwy klasy zarejestrowanych okna, niezależnie od metody użytej do zarejestrowania go.  
  
 Ważne jest, aby użyć `AfxRegisterClass` (lub `AfxRegisterWndClass`) w bibliotece DLL na Win32. Win32 nie automatycznie wyrejestrować klasy zarejestrowany przez bibliotekę DLL, więc musi jawnie wyrejestrować klas, gdy biblioteka DLL jest zakończony. Za pomocą `AfxRegisterClass` zamiast `RegisterClass` to odbywa się automatycznie za Ciebie. `AfxRegisterClass` przechowuje listę klas unikatowy rejestrowane przez biblioteki DLL i automatycznie będzie je wyrejestrować, gdy zakończenie biblioteki DLL. Jeśli używasz `RegisterClass` w bibliotece DLL, upewnij się wszystkie klasy są wyrejestrować, gdy biblioteka DLL jest zakończony (w Twojej [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583) funkcji). Może spowodować niepowodzenie w tym celu `RegisterClass` nieoczekiwane niepowodzenie, gdy inna aplikacja klient próbuje użyć biblioteki DLL.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

