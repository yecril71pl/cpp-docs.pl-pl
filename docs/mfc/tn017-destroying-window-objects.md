---
title: 'TN017: likwidowanie obiektów okien'
ms.date: 11/04/2016
f1_keywords:
- vc.objects
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
ms.openlocfilehash: 2448a2661851f14fc6fe8747ca19495925442436
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226818"
---
# <a name="tn017-destroying-window-objects"></a>TN017: likwidowanie obiektów okien

Ta Uwaga opisuje użycie metody [CWnd::P ostncdestroy](../mfc/reference/cwnd-class.md#postncdestroy) . Użyj tej metody, jeśli chcesz przeprowadzić niestandardowe alokacje `CWnd` obiektów pochodnych. Ta Uwaga wyjaśnia również, dlaczego należy używać [CWnd::D estroywindow](../mfc/reference/cwnd-class.md#destroywindow) do niszczenia obiektu C++ systemu Windows zamiast **`delete`** operatora.

Jeśli przestrzegasz wytycznych w tym temacie, będziesz mieć kilka problemów z czyszczeniem. Te problemy mogą wynikać z problemów, takich jak zapominanie o usunięciu/zwolnieniu pamięci w języku C++, zapominanie do zwolnienia zasobów systemowych, takich jak `HWND` s, lub zwolnienia obiektów zbyt wiele razy.

## <a name="the-problem"></a>Problem

Każdy obiekt systemu Windows (obiekt klasy pochodnej `CWnd` ) reprezentuje zarówno obiekt C++, jak i `HWND` . Obiekty C++ są przydzielane w stercie aplikacji i `HWND` są przydzielane w zasobach systemowych przez Menedżera okien. Ponieważ istnieje kilka sposobów zniszczenia obiektu okna, musimy podać zestaw reguł, które uniemożliwiają przeciek zasobów systemowych lub pamięci. Te reguły muszą również uniemożliwiać zniszczenie obiektów i dojść systemu Windows więcej niż jeden raz.

## <a name="destroying-windows"></a>Niszczenie systemu Windows

Poniżej przedstawiono dwa dozwolone sposoby niszczenia obiektu systemu Windows:

- Wywoływanie `CWnd::DestroyWindow` lub interfejs API systemu Windows `DestroyWindow` .

- Jawne usuwanie z **`delete`** operatorem.

Pierwszy przypadek jest najbardziej typowy. Ten przypadek ma zastosowanie, nawet jeśli kod nie wywołuje `DestroyWindow` bezpośrednio. Gdy użytkownik bezpośrednio zamyka okno ramki, ta akcja generuje komunikat WM_CLOSE, a domyślna odpowiedź na ten komunikat jest wywoływana, `DestroyWindow.` gdy okno nadrzędne zostanie zniszczone, system Windows wywoła `DestroyWindow` wszystkie jego elementy podrzędne.

W drugim przypadku użycie **`delete`** operatora w obiektach systemu Windows powinno być rzadkie. Poniżej znajdują się sytuacje, w których korzystanie **`delete`** z programu jest poprawnym wyborem.

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>Autooczyszczanie przy użyciu CWnd::P ostNcDestroy

Gdy system niszczy okno systemu Windows, ostatni komunikat systemu Windows wysłany do okna jest WM_NCDESTROY. Domyślną procedurą `CWnd` obsługi dla tego komunikatu jest [CWnd:: OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy). `OnNcDestroy`spowoduje odłączenie `HWND` od obiektu C++ i wywołanie funkcji wirtualnej `PostNcDestroy` . Niektóre klasy przesłaniają tę funkcję w celu usunięcia obiektu C++.

Domyślna implementacja `CWnd::PostNcDestroy` nie robi nic, która jest odpowiednia dla obiektów okien, które są przydzielono do ramki stosu lub osadzone w innych obiektach. Nie jest to odpowiednie dla obiektów okien, które są przeznaczone do przydzielania na stercie bez żadnych innych obiektów. Innymi słowy, nie jest to odpowiednie dla obiektów okien, które nie są osadzone w innych obiektach C++.

Te klasy, które są przeznaczone do przydzielenia w stercie, przesłonić `PostNcDestroy` metodę, aby wykonać operację **usuwania**. Ta instrukcja spowoduje zwolnienie dowolnej pamięci skojarzonej z obiektem C++. Mimo że domyślny `CWnd` destruktor wywołuje `DestroyWindow` , jeśli *m_hWnd* ma wartość różną od null, to nie prowadzi do nieskończonej rekursji, ponieważ dojście zostanie odłączone i ma wartość null podczas fazy oczyszczania.

> [!NOTE]
> System jest zazwyczaj wywoływany `CWnd::PostNcDestroy` po przetworzeniu komunikatu WM_NCDESTROY systemu Windows, a `HWND` obiekt okna języka C++ nie jest już połączony. System będzie również wywoływał `CWnd::PostNcDestroy` implementację większości [CWnd:: Create](../mfc/reference/cwnd-class.md#create) wywołuje w przypadku wystąpienia błędu. Reguły automatycznego oczyszczania zostały opisane w dalszej części tego tematu.

## <a name="auto-cleanup-classes"></a>Klasy autooczyszczania

Następujące klasy nie są przeznaczone do autooczyszczania. Są one zazwyczaj osadzone w innych obiektach C++ lub na stosie:

- Wszystkie standardowe formanty systemu Windows ( `CStatic` ,,, itd `CEdit` `CListBox` .).

- Wszystkie podrzędne okna pochodne bezpośrednio z `CWnd` (na przykład kontrolki niestandardowe).

- Okna rozdzielacza ( `CSplitterWnd` ).

- Domyślne paski sterowania (klasy pochodne z `CControlBar` , zobacz [Uwaga techniczna 31](../mfc/tn031-control-bars.md) dla włączania autousuwania dla obiektów paska sterowania).

- Okna dialogowe ( `CDialog` ) przeznaczone dla modalnych okien dialogowych w ramce stosu.

- Wszystkie standardowe okna dialogowe z wyjątkiem `CFindReplaceDialog` .

- Domyślne okna dialogowe utworzone przez ClassWizard.

Poniższe klasy są przeznaczone do autooczyszczania. Są one zazwyczaj przydzielane przez siebie na stercie:

- Główne okna ramowe (pochodne bezpośrednio lub pośrednio z `CFrameWnd` ).

- Wyświetl okna (pochodne bezpośrednio lub pośrednio z `CView` ).

Jeśli chcesz przerwać te reguły, należy zastąpić `PostNcDestroy` metodę w klasie pochodnej. Aby dodać autooczyszczanie do klasy, wywołaj klasę bazową, a następnie **Usuń to**. Aby usunąć autooczyszczanie z klasy, wywołaj `CWnd::PostNcDestroy` bezpośrednio zamiast `PostNcDestroy` metody bezpośredniej klasy podstawowej.

Najbardziej typowym zastosowaniem zmiany zachowania autooczyszczania jest utworzenie niemodalnego okna dialogowego, które może być przydzieloną na stercie.

## <a name="when-to-call-delete"></a>Kiedy należy wywołać metodę Delete

Zalecamy wywołanie `DestroyWindow` niszczenia obiektu systemu Windows, metody języka C++ lub globalnego `DestroyWindow` interfejsu API.

Nie wywołuj globalnego `DestroyWindow` interfejsu API w celu zniszczenia okna podrzędnego MDI. Zamiast tego należy użyć metody wirtualnej `CWnd::DestroyWindow` .

W przypadku obiektów okna języka C++, które nie wykonują autoczyszczenia, użycie **`delete`** operatora może spowodować przeciek pamięci podczas próby wywołania `DestroyWindow` w `CWnd::~CWnd` destruktorze, jeśli VTBL nie wskazuje na poprawną klasę pochodną. Dzieje się tak, ponieważ system nie może odnaleźć odpowiedniej metody niszczenia do wywołania. Użycie `DestroyWindow` zamiast tego **`delete`** eliminuje te problemy. Ponieważ może to być błąd delikatny, skompilowanie w trybie debugowania spowoduje wygenerowanie następującego ostrzeżenia, jeśli jest to ryzykowne.

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

W przypadku obiektów C++ systemu Windows, które wykonują autooczyszczanie, należy wywołać `DestroyWindow` . Jeśli używasz **`delete`** operatora bezpośrednio, Alokator pamięci diagnostyki MFC powiadomi Cię o tym, że zwalniasz pamięć dwa razy. Dwa wystąpienia są pierwszym jawnym wywołaniem i pośrednim wywołaniem **usunięcia tego** elementu w implementacji autooczyszczania `PostNcDestroy` .

Po wywołaniu `DestroyWindow` obiektu bez autooczyszczania obiekt C++ nadal będzie wokół niego, ale *m_hWnd* będzie miał wartość null. Po wywołaniu `DestroyWindow` obiektu autoczyszczącego obiekt języka c++ zostanie usunięty, zwolniony przez operator usuwania języka c++ w implementacji autooczyszczania `PostNcDestroy` .

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numeru](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
