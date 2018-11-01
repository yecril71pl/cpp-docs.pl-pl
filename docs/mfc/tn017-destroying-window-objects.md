---
title: 'TN017: niszczenie obiektów okien'
ms.date: 11/04/2016
f1_keywords:
- vc.objects
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
ms.openlocfilehash: 06553677e67a4314116077e7942381bd847c64d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502235"
---
# <a name="tn017-destroying-window-objects"></a>TN017: niszczenie obiektów okien

Ta uwaga opisuje korzystanie z [CWnd::PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) metody. Użyj tej metody, jeśli chcesz wykonać przydziału dostosowanego `CWnd`-obiektami wywodzącymi. Ta uwaga wyjaśnia, dlaczego należy używać [CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) do zniszczenia obiektu języka C++ Windows zamiast **Usuń** operatora.

Jeśli postępuj zgodnie z wytycznymi w tym temacie, masz kilka problemów oczyszczania. Te problemy mogą wynikać z problemów, takich jak Zapominanie o usunięcie/zwolnić pamięć języka C++, Zapominanie o zwalnianiu zasobów systemowych, takich jak `HWND`s lub zwalnianie obiektów zbyt wiele razy.

## <a name="the-problem"></a>Ten Problem

Każdy obiekt systemu windows (obiekt klasy pochodne `CWnd`) reprezentuje obiekt C++ i `HWND`. Obiekty C++ są przydzielane w pamięci i `HWND`s przydzielania zasobów systemowych przez Menedżera okien. Ponieważ istnieje kilka sposobów, aby zniszczyć obiekt window, firma Microsoft zapewnia zestaw reguł, które uniemożliwiają systemu przecieki zasobu lub pamięci. Te reguły należy również uniemożliwić obiektów i uchwytów Windows niszczone więcej niż jeden raz.

## <a name="destroying-windows"></a>Niszczenie Windows

Poniżej przedstawiono dwie metody dozwolonych zniszczenie obiektu Windows:

- Wywoływanie `CWnd::DestroyWindow` lub Windows API `DestroyWindow`.

- Jawne usuwanie z **Usuń** operatora.

Pierwszy przypadek jest najpopularniejszą najczęściej. Ten przypadek ma zastosowanie, nawet wtedy, gdy kod wywołuje `DestroyWindow` bezpośrednio. Po użytkownik bezpośrednio zamknie okno ramowe, ta akcja generuje komunikat WM_CLOSE, natomiast domyślną odpowiedź na tę wiadomość do wywołania `DestroyWindow.` kiedy niszczony jest okno nadrzędne, Windows wywołuje `DestroyWindow` dla wszystkich elementów podrzędnych.

Drugi przypadek, stosowania **Usuń** operatora w obiektach Windows powinny być rzadko. Następujące rodzaje niektórych przypadków, w przypadku, gdy za pomocą **Usuń** odpowiednim wyborem.

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>Automatyczne oczyszczanie przy użyciu CWnd::PostNcDestroy

Gdy system niszczy okno programu Windows, ostatni komunikat Windows wysyłany do okna jest WM_NCDESTROY. Wartość domyślna `CWnd` obsługi dla tego komunikatu jest [CWnd::OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy). `OnNcDestroy` spowoduje odłączenie `HWND` z C++ obiektu i wywołać funkcję wirtualną `PostNcDestroy`. Niektóre klasy przesłonić tę funkcję można usunąć obiektu języka C++.

Domyślna implementacja klasy `CWnd::PostNcDestroy` nie wykonuje żadnych działań, które jest odpowiednie dla obiektów okna, które są przydzielane na ramce stosu lub informacje osadzone w innych obiektów. To nie jest odpowiedni dla obiektów okna, które mają zostać przydzielone na stercie bez żadnych innych obiektów. Innymi słowy nie jest właściwe dla obiektów okna, które nie są osadzone w innych obiektów języka C++.

Zastąpienie tych klas, które są przeznaczone do można samodzielnie przydzielony na stosie `PostNcDestroy` metodę w celu **usunąć ten**. Ta instrukcja zwolni pamięć, wszelkie skojarzone z obiektu języka C++. Mimo że domyślnie `CWnd` wywołania destruktora `DestroyWindow` Jeśli *m_hWnd* jest różna od NULL, to nie powoduje nieskończoną rekursję ponieważ uchwytu będzie odłączony i o wartości NULL podczas fazy czyszczenia.

> [!NOTE]
>  System zwykle wywołuje `CWnd::PostNcDestroy` po przetwarza komunikat Windows WM_NCDESTROY i `HWND` i obiekt okna języka C++ nie jest już połączony. System będzie także wywoływać `CWnd::PostNcDestroy` w implementacji większość [CWnd::Create](../mfc/reference/cwnd-class.md#create) wywołania po wystąpieniu błędu. Reguły automatycznego oczyszczania są opisane w dalszej części tego tematu.

## <a name="auto-cleanup-classes"></a>Automatyczne oczyszczanie klas

Następujące klasy nie są przeznaczone do automatycznego czyszczenia. Zazwyczaj są osadzone w innych obiektów C++ lub na stosie:

- Wszystkie kontrolki Windows standardowe (`CStatic`, `CEdit`, `CListBox`i tak dalej).

- Ewentualnie okien podrzędnych pochodzi bezpośrednio z `CWnd` (na przykład, kontrolki niestandardowe).

- Okna podziału (`CSplitterWnd`).

- Domyślne paski sterowania (klasy pochodne `CControlBar`, zobacz [techniczne 31 Uwaga](../mfc/tn031-control-bars.md) umożliwiające automatyczne usuwanie obiektów pasek sterowania).

- Okna dialogowe (`CDialog`) przeznaczone dla dialogów modalnych na ramce stosu.

- Wszystkie standardowe okien dialogowych z wyjątkiem `CFindReplaceDialog`.

- Okna dialogowe domyślne, utworzone przez ClassWizard.

Następujące klasy są przeznaczone do automatycznego czyszczenia. Samodzielnie są zazwyczaj przydzielone na stercie:

- Głównego okna ramowe (pochodzi bezpośrednio lub pośrednio z `CFrameWnd`).

- Wyświetlanie okien (pochodzi bezpośrednio lub pośrednio z `CView`).

Jeśli chcesz przerwać te reguły, konieczne jest przesłonięcie `PostNcDestroy` metody w klasie pochodnej. Aby dodać automatycznego czyszczenia do klasy, wywołaj klasę bazową, a następnie wykonaj **usunąć ten**. Aby usunąć automatycznego oczyszczania klasy, należy wywołać `CWnd::PostNcDestroy` bezpośrednio zamiast z `PostNcDestroy` metody bezpośredniej klasy podstawowej.

Najczęściej używane zmiany zachowania oczyszczania automatycznie jest Tworzenie niemodalnego okna dialogowego, która może być przydzielona na stosie.

## <a name="when-to-call-delete"></a>Gdy do wywołania delete

Firma Microsoft zaleca wywołanie `DestroyWindow` do zniszczenia obiektu Windows, Metoda C++ lub globalnego `DestroyWindow` interfejsu API.

Nie wywołuj globalnego `DestroyWindow` interfejsu API można zniszczyć okna elementu podrzędnego MDI. Należy używać metody wirtualnej `CWnd::DestroyWindow` zamiast tego.

Dla okna języka C++ obiektów, który nie należy wykonywać automatyczne oczyszczanie, za pomocą **Usuń** operator może spowodować przeciek pamięci, podczas próby wywołania `DestroyWindow` w `CWnd::~CWnd` destruktor, jeśli VTBL nie wskazuje klasy pochodnej poprawnie. Dzieje się tak, ponieważ system nie można odnaleźć odpowiedniej destroy — metoda do wywołania. Za pomocą `DestroyWindow` zamiast **Usuń** pozwala uniknąć tych problemów. Ponieważ może to być subtelnych błędów, kompilowanie w trybie debugowania wygeneruje poniższe ostrzeżenie, jeśli zaistnieje ryzyko.

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

W przypadku obiektów C++ Windows, które wykonują automatycznego oczyszczania, należy wywołać `DestroyWindow`. Jeśli używasz **Usuń** operator bezpośrednio alokatora pamięci diagnostycznych MFC powiadomi użytkownika, czy możesz się zwalnianie pamięci dwa razy. Dwa wystąpienia są pierwszego wywołania jawnego i pośrednie wywołanie **usunąć ten** w implementacji automatyczne oczyszczanie `PostNcDestroy`.

Po wywołaniu `DestroyWindow` w obiekcie bez czyszczenia automatycznie obiektu języka C++ nadal będzie się wokół, ale *m_hWnd* będzie mieć wartość NULL. Po wywołaniu `DestroyWindow` na obiekcie automatyczne oczyszczanie obiektu języka C++ nie będą już dostępne, uwolniony przez operatora delete C++ w implementacji automatyczne oczyszczanie `PostNcDestroy`.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

