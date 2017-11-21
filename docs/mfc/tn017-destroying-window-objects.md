---
title: "TN017: Likwidowanie obiektów okien | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.objects
dev_langs: C++
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f3448fdfbd67db1591d6abd38cefea94dccb4ed2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="tn017-destroying-window-objects"></a>TN017: niszczenie obiektów okien
Opisuje tej uwagi [CWnd::PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) metody. Użyj tej metody, jeśli chcesz wykonać przydziału dostosowanego `CWnd`-pochodnych obiektów. Ta uwaga wyjaśnia, dlaczego warto korzystać [CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) zniszczenie obiektu Windows w języku C++ zamiast `delete` operatora.  
  
 Jeśli wykonujesz wskazówki zawarte w tym temacie, masz kilka problemów oczyszczania. Te problemy mogą wynikać z problemów, takich jak włączaniu delete/zwolnić pamięć C++, zapomniane można zwolnić zasobów systemowych, takich jak `HWND`s lub zwalnianie obiektów zbyt wiele razy.  
  
## <a name="the-problem"></a>Problem  
 Każdy obiekt systemu windows (obiekt klasy pochodzące z `CWnd`) reprezentuje obiekt C++ i `HWND`. Obiekty C++ są przydzielane w pamięci i `HWND`s przydzielania przez Menedżera okien zasobów systemowych. Ponieważ istnieje kilka sposobów, aby zniszczyć obiekt window, możemy podać zestaw reguł, które uniemożliwiają systemu przecieki pamięci lub zasobów. Te reguły należy również uniemożliwić obiekty i uchwyty okien niszczony więcej niż jeden raz.  
  
## <a name="destroying-windows"></a>Niszczenie okien  
 Poniżej przedstawiono dwa sposoby dozwolonych zniszczenie obiektu systemu Windows:  
  
-   Wywoływanie `CWnd::DestroyWindow` lub z Windows API `DestroyWindow`.  
  
-   Jawne usuwanie z `delete` operatora.  
  
 Pierwszym przypadku jest znacznie najczęściej. Przypadek ma zastosowanie, nawet wtedy, gdy nie mogą wywoływać kodu `DestroyWindow` bezpośrednio. Gdy użytkownik zamyka bezpośrednio okno ramowe, ta akcja generuje `WM_CLOSE` komunikat i domyślne odpowiedzi na tę wiadomość jest wywołanie `DestroyWindow.` gdy okno nadrzędne zostanie zniszczony, system Windows wywołuje `DestroyWindow` dla wszystkich jego obiektów podrzędnych.  
  
 Drugim przypadku, użycie `delete` operator obiektów systemu Windows, powinny być rzadko. Następujące są, w niektórych przypadkach, gdy przy użyciu `delete` jest poprawny wybór.  
  
## <a name="auto-cleanup-with-cwndpostncdestroy"></a>Automatyczne czyszczenie z CWnd::PostNcDestroy  
 Gdy system niszczy okno systemu Windows, jest ostatnią wiadomością Windows wysyłany do okna `WM_NCDESTROY`. Wartość domyślna `CWnd` obsługi dla tego komunikatu jest [CWnd::OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy). `OnNcDestroy`Odłącz będzie `HWND` z C++ obiektu i wywołanie funkcji wirtualnych `PostNcDestroy`. Niektóre klasy przesłonić tę funkcję, aby usunąć obiekt C++.  
  
 Domyślna implementacja `CWnd::PostNcDestroy` nie robi nic, który jest odpowiedni dla obiektów okna, które są przydzielone w ramce stosu lub osadzone w innych obiektów. To nie jest odpowiedni dla obiektów okna, które mają zostać przydzielone na stercie bez żadnych innych obiektów. Innymi słowy nie jest odpowiedni dla obiektów okna, które nie są osadzone w innych obiektów C++.  
  
 Zastąpienie tych klas, które mają być samodzielnie przydzielony na stosie `PostNcDestroy` metodę w celu `delete this`. Ta instrukcja zwolni wszystkie skojarzone z obiektem C++ pamięci. Mimo że domyślne `CWnd` wywołania destruktora `DestroyWindow` Jeśli `m_hWnd` jest różna od NULL, nie prowadzi do nieskończonej rekursji ponieważ dojście jest odłączony i wartości NULL podczas fazy czyszczenia.  
  
> [!NOTE]
>  Zazwyczaj wymaga systemu `CWnd::PostNcDestroy` po przetwarza systemu Windows `WM_NCDESTROY` wiadomości i `HWND` i obiektem okna języka C++ nie jest już połączony. System będzie wymagało `CWnd::PostNcDestroy` w implementacji większość [CWnd::Create](../mfc/reference/cwnd-class.md#create) wywołania w przypadku niepowodzenia. Reguły oczyszczania automatycznie są opisane w dalszej części tego tematu.  
  
## <a name="auto-cleanup-classes"></a>Automatyczne czyszczenie klas  
 Następujące klasy nie są przeznaczone do automatycznego czyszczenia. Zazwyczaj są osadzone w innych obiektów C++ lub na stosie:  
  
-   Wszystkie formanty standardowe systemu Windows (`CStatic`, `CEdit`, `CListBox`i tak dalej).  
  
-   Ewentualnie okien podrzędnych pochodzi bezpośrednio z `CWnd` (na przykład formantów niestandardowych).  
  
-   Okna podziału (`CSplitterWnd`).  
  
-   Domyślne paski sterowania (klasy wyprowadzone z `CControlBar`, zobacz [31 Uwaga techniczna](../mfc/tn031-control-bars.md) włączenia automatycznego usuwania obiektów pasek sterowania).  
  
-   Okna dialogowe (`CDialog`) przeznaczone dla dialogów modalnych w ramce stosu.  
  
-   Wszystkie standardowe okna z wyjątkiem `CFindReplaceDialog`.  
  
-   Okna dialogowe domyślny utworzony przez ClassWizard.  
  
 Następujące klasy są przeznaczone do automatycznego czyszczenia. Samodzielnie są zwykle przydzielone na stercie:  
  
-   Okna ramowe głównego (pochodzi bezpośrednio lub pośrednio od `CFrameWnd`).  
  
-   Wyświetlanie okien (pochodzi bezpośrednio lub pośrednio od `CView`).  
  
 Jeśli chcesz przerwać te reguły, konieczne jest przesłonięcie `PostNcDestroy` metody w klasie pochodnej. Aby dodać automatycznego czyszczenia do klasy, wywołaj klasy podstawowej, a następnie wykonaj `delete this`. Aby usunąć automatycznego czyszczenia z klasy, należy wywołać `CWnd::PostNcDestroy` bezpośrednio zamiast z `PostNcDestroy` metody bezpośredniej klasy podstawowej.  
  
 Tworzenie niemodalnego okna dialogowego, który może zostać przydzielone na stercie jest najczęściej używane zmiany zachowania oczyszczania automatycznie.  
  
## <a name="when-to-call-delete"></a>Gdy do usuwania wywołania  
 Firma Microsoft zaleca, aby wywołać `DestroyWindow` zniszczenie obiektu Windows metody C++ lub globalnej `DestroyWindow` interfejsu API.  
  
 Nie wywołuj globalnej `DestroyWindow` interfejsu API można zniszczyć okna podrzędnego MDI. Należy używać metody wirtualnej `CWnd::DestroyWindow` zamiast tego.  
  
 Dla okna języka C++ obiekty nie wykonuj automatycznego czyszczenia, za pomocą `delete` operator może spowodować przeciek pamięci w przypadku próby wywołania `DestroyWindow` w `CWnd::~CWnd` destruktor, jeśli VTBL nie wskazuje klasy pochodnej poprawnie. Dzieje się tak, ponieważ system nie można odnaleźć odpowiedniej destroy — metoda do wywołania. Przy użyciu `DestroyWindow` zamiast `delete` pozwala uniknąć tych problemów. Ponieważ może to być błąd niewielkie, kompilowania kodu w trybie debugowania wygeneruje następujące ostrzeżenie, jeśli są narażeni na ataki.  
  
```  
Warning: calling DestroyWindow in CWnd::~CWnd  
    OnDestroy or PostNcDestroy in derived class will not be called  
```  
  
 W przypadku obiektów Windows w języku C++, które należy wykonywać automatycznego czyszczenia, należy wywołać `DestroyWindow`. Jeśli używasz `delete` — operator bezpośrednio, alokatora diagnostycznych MFC powiadomienie, że możesz się zwolnić pamięć, dwa razy. Dwa wystąpienia są Twoje pierwsze wywołanie jawne i pośrednie wywołanie `delete this` oczyszczania automatycznego stosowania `PostNcDestroy`.  
  
 Po wywołaniu `DestroyWindow` dla obiektu z systemem innym niż oczyszczania automatycznie, obiekt C++ nadal będzie wokół, ale `m_hWnd` będzie mieć wartość NULL. Po wywołaniu `DestroyWindow` obiektu automatycznego czyszczenia C++ obiekt zostanie usunięty, zwolniony przez operatora delete C++ w ramach oczyszczania automatycznego stosowania `PostNcDestroy`.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

