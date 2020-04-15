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
ms.openlocfilehash: 9802669468cbbba89f23b8ac127358d1fc15ec9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370419"
---
# <a name="tn017-destroying-window-objects"></a>TN017: likwidowanie obiektów okien

W tej notatce opisano użycie [CWnd::PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) metody. Tej metody należy użyć, jeśli chcesz `CWnd`wykonać niestandardową alokację obiektów pochodnych. W tej notatce wyjaśniono również, dlaczego należy użyć [CWnd::DestroyWindow,](../mfc/reference/cwnd-class.md#destroywindow) aby zniszczyć obiekt systemu Windows w języku C++ zamiast operatora **usuwania.**

Jeśli zastosujesz się do wytycznych w tym temacie, będziesz miał kilka problemów z oczyszczaniem. Problemy te mogą wynikać z problemów, takich jak zapominanie o usunięciu/uwolnieniu pamięci C++, zapominanie o wolnych zasobach systemowych, takich jak `HWND`s, lub zwalnianie obiektów zbyt wiele razy.

## <a name="the-problem"></a>The Problem

Każdy obiekt systemu Windows (obiekt `CWnd`klasy pochodnej) reprezentuje zarówno `HWND`obiekt C++ i . Obiekty języka C++ są przydzielane w `HWND`stercie aplikacji i s są przydzielane w zasobach systemowych przez menedżera okien. Ponieważ istnieje kilka sposobów, aby zniszczyć obiekt okna, musimy podać zestaw reguł, które zapobiegają wyciekom zasobów systemowych lub pamięci. Reguły te muszą również zapobiegać niszczenia obiektów i uchwytów systemu Windows więcej niż jeden raz.

## <a name="destroying-windows"></a>Niszczenie systemu Windows

Poniżej przedstawiono dwa dozwolone sposoby niszczenia obiektu systemu Windows:

- Połączenia `CWnd::DestroyWindow` lub interfejsu `DestroyWindow`API systemu Windows .

- Jawne usuwanie za pomocą operatora **usuwania.**

Pierwszy przypadek jest zdecydowanie najczęstszy. Ten przypadek ma zastosowanie, nawet `DestroyWindow` jeśli kod nie jest wywoływany bezpośrednio. Gdy użytkownik bezpośrednio zamyka okno ramki, ta akcja generuje komunikat WM_CLOSE, a domyślną odpowiedzią na ten komunikat jest `DestroyWindow.` `DestroyWindow` wywołanie Gdy okno nadrzędne zostanie zniszczone, system Windows wywołuje wszystkie jego wiązki obrażeń.

Drugi przypadek, użycie operatora **usuwania** w obiektach systemu Windows, powinno być rzadkie. Poniżej przedstawiono kilka przypadków, w których użycie **delete** jest właściwym wyborem.

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>Automatyczne oczyszczanie za pomocą CWnd::PostNcDestroy

Gdy system niszczy okno systemu Windows, ostatni komunikat systemu Windows wysłany do okna jest WM_NCDESTROY. Domyślnym `CWnd` programem obsługi tej wiadomości jest [CWnd::OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy). `OnNcDestroy`odłączy `HWND` obiekt C++ i wywoła funkcję `PostNcDestroy`wirtualną . Niektóre klasy zastąpić tę funkcję, aby usunąć obiekt C++.

Domyślna implementacja `CWnd::PostNcDestroy` nie robi nic, co jest odpowiednie dla obiektów okna, które są przydzielane w ramce stosu lub osadzone w innych obiektach. Nie jest to odpowiednie dla obiektów okna, które są przeznaczone do przydzielania na stercie bez żadnych innych obiektów. Innymi słowy nie jest odpowiedni dla obiektów okna, które nie są osadzone w innych obiektów Języka C++.

Te klasy, które są przeznaczone do przypisanie samodzielnie `PostNcDestroy` na stercie zastąpić metodę, aby wykonać **usunąć to**. Ta instrukcja zwalnia wszelkie pamięci skojarzone z C++ obiektu. Mimo że `CWnd` domyślny destruktor `DestroyWindow` *wywołuje,* jeśli m_hWnd jest nienastępna, nie prowadzi to do nieskończonej rekursji, ponieważ dojście zostanie odłączone i null podczas fazy oczyszczania.

> [!NOTE]
> System zwykle `CWnd::PostNcDestroy` wywołuje po przetwarza komunikat WM_NCDESTROY systemu `HWND` Windows i i C++ obiekt okna nie są już połączone. System będzie również `CWnd::PostNcDestroy` wywołać w implementacji większości [CWnd::Create](../mfc/reference/cwnd-class.md#create) wywołań, jeśli wystąpi błąd. Reguły oczyszczania automatycznego są opisane w dalszej części tego tematu.

## <a name="auto-cleanup-classes"></a>Klasy automatycznego oczyszczania

Następujące klasy nie są przeznaczone do automatycznego oczyszczania. Są one zazwyczaj osadzone w innych obiektach Języka C++ lub na stosie:

- Wszystkie standardowe formanty systemu Windows (`CStatic`, `CEdit` `CListBox`, i tak dalej).

- Wszystkie okna podrzędne pochodzące bezpośrednio z `CWnd` (na przykład formanty niestandardowe).

- Okna rozdzielacza (`CSplitterWnd`).

- Domyślne paski sterowania (klasy pochodzące z `CControlBar`programu , patrz Uwaga [techniczna 31,](../mfc/tn031-control-bars.md) aby włączyć automatyczne usuwanie obiektów paska sterowania).

- Dialogi`CDialog`( ) przeznaczone do modalnych okien dialogowych w ramce stosu.

- Wszystkie standardowe okna `CFindReplaceDialog`dialogowe z wyjątkiem .

- Domyślne okna dialogowe utworzone przez ClassWizard.

Następujące klasy są przeznaczone do automatycznego oczyszczania. Są one zazwyczaj przydzielane przez siebie na stercie:

- Okna ramki głównej (pochodzące bezpośrednio `CFrameWnd`lub pośrednio z ).

- Okna widoku (pochodzące bezpośrednio lub `CView`pośrednio z ).

Jeśli chcesz złamać te reguły, należy `PostNcDestroy` zastąpić metodę w klasie pochodnej. Aby dodać automatyczne oczyszczanie do klasy, zadzwoń do klasy podstawowej, a następnie **usuń tę .** Aby usunąć automatyczne oczyszczanie z `CWnd::PostNcDestroy` klasy, zadzwoń bezpośrednio `PostNcDestroy` zamiast metody bezpośredniej klasy podstawowej.

Najczęstszym zastosowaniem zmiany zachowania oczyszczania automatycznego jest utworzenie niemodnego okna dialogowego, które można przydzielić na stercie.

## <a name="when-to-call-delete"></a>Kiedy wywołać usuń

Zaleca się wywołanie, `DestroyWindow` aby zniszczyć obiekt systemu Windows, metoda `DestroyWindow` C++ lub globalnego interfejsu API.

Nie należy wywoływać globalnego `DestroyWindow` interfejsu API, aby zniszczyć okno podrzędne MDI. Zamiast tego należy `CWnd::DestroyWindow` użyć metody wirtualnej.

Dla obiektów okna języka C++, które nie wykonują automatycznego oczyszczania, za pomocą `DestroyWindow` **delete** operator może spowodować przeciek pamięci podczas próby wywołania w `CWnd::~CWnd` destruktora, jeśli VTBL nie wskazuje poprawnie pochodną klasy. Dzieje się tak, ponieważ system nie może znaleźć odpowiednią metodę destroy do wywołania. Użycie `DestroyWindow` zamiast **usuwania** pozwala uniknąć tych problemów. Ponieważ może to być błąd subtelny, kompilacja w trybie debugowania wygeneruje następujące ostrzeżenie, jeśli jesteś zagrożony.

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

W przypadku obiektów systemu Windows języka C++, które wykonują `DestroyWindow`automatyczne oczyszczanie, należy wywołać program . Jeśli używasz **delete** operator bezpośrednio, Alokator pamięci diagnostycznej MFC powiadomi, że zwalniasz pamięć dwa razy. Dwa wystąpienia są pierwszym jawnym wywołaniem i wywołaniem pośrednim, aby `PostNcDestroy`usunąć **to** w implementacji automatycznego oczyszczania .

Po `DestroyWindow` wywołaniu obiektu bez automatycznego oczyszczania obiekt C++ nadal będzie w pobliżu, ale *m_hWnd* będzie null. Po `DestroyWindow` wywołaniu obiektu automatycznego oczyszczania obiekt C++ zniknie, zwolniony przez operatora delete języka C++ `PostNcDestroy`w implementacji automatycznego oczyszczania .

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
