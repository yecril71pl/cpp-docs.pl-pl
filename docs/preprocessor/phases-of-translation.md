---
title: Fazy tłumaczenia
ms.date: 08/29/2019
helpviewer_keywords:
- translation phases
- preprocessor, translation
- translation, compiler process
- preprocessor
- file translation [C++], compiler process
- files [C++], translation
ms.assetid: a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db
ms.openlocfilehash: d072c9aec48d815ba85f8a12576baa6447703f8c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218308"
---
# <a name="phases-of-translation"></a>Fazy tłumaczenia

Programy C i C++ składają się z jednego lub więcej plików źródłowych, z których każdy zawiera część tekstu programu. Plik źródłowy wraz z *plikami plików*dołączanych, które są uwzględniane przy użyciu `#include` dyrektywy preprocesora, ale bez uwzględniania sekcji kodu usunięte przez dyrektywy kompilacji warunkowej, takie jak `#if`, nosi nazwę  *Jednostka tłumaczenia*.

Pliki źródłowe mogą być tłumaczone w różnym czasie. W rzeczywistości często jest możliwe przetłumaczenie tylko nieaktualnych plików. Przetłumaczone jednostki translacji mogą być przetwarzane do oddzielnych plików obiektu lub bibliotek kodu obiektu. Te oddzielne, przetłumaczone jednostki translacji są następnie łączone, aby sformułować program wykonywalny lub bibliotekę dynamicznych połączeń (DLL). Aby uzyskać więcej informacji na temat plików, które mogą być używane jako dane wejściowe dla konsolidatora, zobacz [łączenie plików wejściowych](../build/reference/link-input-files.md).

Jednostki translacji mogą komunikować się za pomocą:

- Wywołań funkcji, które mają powiązania zewnętrzne.

- Wywołań funkcji składowych klasy, które mają powiązania zewnętrzne.

- Bezpośrednich modyfikacji obiektów, które mają powiązania zewnętrzne.

- Bezpośrednich modyfikacji plików.

- Komunikacji międzyprocesowej (tylko dla aplikacji opartych na Microsoft Windows).

Na poniższej liście opisano fazy, w których kompilator tłumaczy pliki:

*Mapowanie znaków*\
Znaki w pliku źródłowym są mapowane do wewnętrznej reprezentacji źródła. Sekwencje trzech znaków są konwertowane na wewnętrzną reprezentację pojedynczych znaków w tej fazie.

*Łączenie wierszy*\
Wszystkie wiersze kończące się ukośnikiem odwrotnym ( **\\** ) bezpośrednio po znaku nowego wiersza są sprzężone z następnym wierszem w pliku źródłowym, tworząc linie logiczne z linii fizycznych. O ile nie jest pusty, plik źródłowy musi kończyć się znakiem nowego wiersza, który nie jest poprzedzony ukośnikiem odwrotnym.

*Tokenizacji*\
Plik źródłowy jest dzielony na tokeny wstępnego przetwarzania i znaki odstępu. Każdy komentarz w pliku źródłowym jest zamieniany na jeden znak spacji. Znaki nowego wiersza są zachowywane.

*Przetwarzania wstępnego*\
Dyrektywy przetwarzania wstępnego są wykonywane, a makra rozwijane do pliku źródłowego. Instrukcja `#include` wywołuje translację począwszy od powyższych trzech kroków translacji na dowolnym dołączonym tekście.

*Mapowanie zestawu znaków*\
Wszystkie elementy członkowskie zestawu znaków źródła i sekwencje unikowe są konwertowane na ich odpowiedniki w zestawie znaków wykonywania. Zestawy znaków źródła i wykonania są w kodowaniu ASCII w Microsoft C i C++.

*Łączenie ciągów*\
Wszystkie sąsiadujące ciągi znaków i literały szerokiego ciągu są łączone. Na przykład, `"String " "concatenation"` staje się `"String concatenation"`.

*Licz*\
Wszystkie tokeny są analizowane składniowo i semantycznie; tokeny te są przekształcane na kod obiektu.

*Powiązania*\
Wszystkie odwołania zewnętrzne są rozwiązywane, aby utworzyć program wykonywalny lub bibliotekę dołączaną dynamicznie.

Kompilator generuje ostrzeżenia lub błędy podczas faz tłumaczenia, w których napotka błędy składniowe.

Konsolidator usuwa wszystkie odwołania zewnętrzne i tworzy plik wykonywalny lub bibliotekę DLL przez połączenie jednej lub więcej jednostek translacji z bibliotekami standardowymi.

## <a name="see-also"></a>Zobacz także

[Preprocesor](../preprocessor/preprocessor.md)
