---
title: Fazy tłumaczenia
ms.date: 10/18/2018
helpviewer_keywords:
- translation phases
- preprocessor, translation
- translation, compiler process
- preprocessor
- file translation [C++], compiler process
- files [C++], translation
ms.assetid: a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db
ms.openlocfilehash: 11e36e06adc4fa95cb9aa607704e72f64c812429
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036156"
---
# <a name="phases-of-translation"></a>Fazy tłumaczenia

Programy C i C++ składają się z jednego lub więcej plików źródłowych, z których każdy zawiera część tekstu programu. Plik źródłowy, wraz z dołączonymi plikami (plikami dołączonymi za pomocą dyrektywy preprocesora `#include`), ale bez sekcji kodu usuniętych przez dyrektywy kompilacji warunkowej takie jak `#if`, nosi nazwę „jednostki translacji”.

Pliki źródłowe mogą być tłumaczone w różnym czasie — w rzeczywistości bardzo często tłumaczone są tylko nieaktualne pliki. Przetłumaczone jednostki translacji mogą być przetwarzane do oddzielnych plików obiektu lub bibliotek kodu obiektu. Te oddzielne, przetłumaczone jednostki translacji są następnie łączone, aby sformułować program wykonywalny lub bibliotekę dynamicznych połączeń (DLL).  Aby uzyskać więcej informacji o plikach, które mogą być używane jako dane wejściowe do konsolidatora, zobacz [pliki wejściowe LINK](../build/reference/link-input-files.md).

Jednostki translacji mogą komunikować się za pomocą:

- Wywołań funkcji, które mają powiązania zewnętrzne.

- Wywołań funkcji składowych klasy, które mają powiązania zewnętrzne.

- Bezpośrednich modyfikacji obiektów, które mają powiązania zewnętrzne.

- Bezpośrednich modyfikacji plików.

- Komunikacji międzyprocesowej (tylko dla aplikacji opartych na Microsoft Windows).

Na poniższej liście opisano fazy, w których kompilator tłumaczy pliki:

*Mapowanie znaków*<br/>
Znaki w pliku źródłowym są mapowane do wewnętrznej reprezentacji źródła. Sekwencje trzech znaków są konwertowane na wewnętrzną reprezentację pojedynczych znaków w tej fazie.

*Łączenie wierszy*<br/>
Wszystkie wiersze kończące się znakiem ukośnika odwrotnego (**\\**) i po których bezpośrednio następuje przez nowy wiersz znaków są przyłączane do następnego wiersza w pliku źródłowym, tworząc logiczne wiersze z wierszy fizycznych. O ile nie jest on pusty, plik źródłowy musi kończyć się znakiem nowego wiersza, który nie jest poprzedzony znakiem ukośnika odwrotnego.

*Tokenizacji*<br/>
Plik źródłowy jest dzielony na tokeny wstępnego przetwarzania i znaki odstępu. Każdy komentarz w pliku źródłowym jest zamieniany na jeden znak spacji. Znaki nowego wiersza są zachowywane.

*Przetwarzanie wstępne*<br/>
Dyrektywy przetwarzania wstępnego są wykonywane, a makra rozwijane do pliku źródłowego. Instrukcja `#include` wywołuje translację począwszy od powyższych trzech kroków translacji na dowolnym dołączonym tekście.

*{1&gt;Mapowanie zestawu znaków&lt;1}*<br/>
Wszystkie elementy członkowskie zestawu znaków źródła i sekwencje unikowe są konwertowane na ich odpowiedniki w zestawie znaków wykonywania. Zestawy znaków źródła i wykonania są w kodowaniu ASCII w Microsoft C i C++.

*{1&gt;Łączenie ciągów&lt;1}*<br/>
Wszystkie sąsiadujące ciągi znaków i literały szerokiego ciągu są łączone. Na przykład, `"String " "concatenation"` staje się `"String concatenation"`.

*{1&gt;Translacja&lt;1}*<br/>
Wszystkie tokeny są analizowane składniowo i semantycznie; tokeny te są przekształcane na kod obiektu.

*Połączenie*<br/>
Wszystkie odwołania zewnętrzne są rozwiązywane, aby utworzyć program wykonywalny lub bibliotekę dołączaną dynamicznie.

Kompilator generuje ostrzeżenia lub błędy podczas faz tłumaczenia, w których napotka błędy składniowe.

Konsolidator usuwa wszystkie odwołania zewnętrzne i tworzy plik wykonywalny lub bibliotekę DLL przez połączenie jednej lub więcej jednostek translacji z bibliotekami standardowymi.

## <a name="see-also"></a>Zobacz także

[Preprocesor](../preprocessor/preprocessor.md)