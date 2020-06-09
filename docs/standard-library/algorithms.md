---
title: Algorytmy
ms.date: 10/18/2018
helpviewer_keywords:
- libraries [C++], C++ algorithm conventions
- algorithms [C++], C++
- C++ Standard Library, algorithms
- algorithm template function C++ library conventions
- conventions [C++], C++ algorithm
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
ms.openlocfilehash: 4b49b3c296d3afcbb26af028dc0b4a885444a897
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617629"
---
# <a name="algorithms"></a>Algorytmy

Algorytmy są podstawową częścią standardowej biblioteki języka C++. Algorytmy nie działają z kontenerami, ale raczej z iteratorów. W związku z tym ten sam algorytm może być używany w większości, jeśli nie wszystkie kontenery standardowej biblioteki języka C++. W tej sekcji omówiono konwencje i terminologię algorytmów standardowej biblioteki języka C++.

## <a name="remarks"></a>Uwagi

Opisy funkcji szablonu algorytmu korzystają z kilku skróconych fraz:

- Fraza "w zakresie \[ *A*, *B*)" oznacza sekwencję zero lub więcej dyskretnych wartości zaczynających się *A* do, ale nie z uwzględnieniem *B*. Zakres jest prawidłowy tylko wtedy, gdy *B* jest osiągalny z *;* *można przechowywać w* obiekcie *n* (*n*  =  *A*), zwiększać obiekt zero lub więcej razy (+ +*N*) i czy porównywany obiekt jest równy *B* po skończonej liczbie przyrostów (*N*  ==  *B*).

- Fraza "Każdy *N* w zakresie \[ *A*, *B*)" oznacza, że *N* zaczyna się od wartości *a* i jest zwiększana zero lub więcej razy, dopóki nie będzie równa wartości *B*. Przypadek *N*  ==  *B* nie należy do zakresu.

- Fraza "najniższa wartość *N* w zakresie \[ *a*, *b*) taka, że *x*" oznacza, że warunek *x* jest określany dla każdego *N* w zakresie \[ *a*, *b*) do momentu spełnienia warunku *x* .

- Fraza "najwyższa wartość *N* w zakresie \[ *a*, *B*) taka, że *x* oznacza, że *x* jest określana dla każdego *N* w zakresie \[ *a*, *b*). Funkcja zapisuje w *K* a kopię *N* za każdym razem, gdy spełniony jest warunek *X* . W przypadku wystąpienia dowolnego takiego magazynu funkcja zastępuje końcową wartość *N*, która jest równa *B*, z wartością *K*. Jednak dla iteratora dwukierunkowego lub swobodnego dostępu, można również oznaczać, że *N* zaczyna się od najwyższej wartości zakresu i jest zmniejszany do zakresu do momentu spełnienia warunku *X* .

- Wyrażenia takie jak *x*  -  *Y*, gdzie *x* i *Y* mogą być iteratorami innymi niż Iteratory dostępu swobodnego, są zamierzone w sensie matematycznym. Funkcja nie musi obliczać operatora **-** , jeśli musi ustalić taką wartość. Ta sama wartość dotyczy również wyrażeń, takich jak *x*  +  *n* i *x*  -  *n*, gdzie *N* jest typem liczb całkowitych.

Kilka algorytmów używa predykatu, który wykonuje porównanie parowania, takie jak with `operator==` , w celu uzyskania wyniku **logicznego** . Funkcja predykatu `operator==` lub wszelkie jej zamiany nie mogą zmieniać żadnego z argumentów operacji. Musi ona dawać ten sam wynik **bool** przy każdej ocenie i musi dać ten sam wynik, jeśli kopia jednego z operandów jest zastępowana dla operandu.

Kilka algorytmów używa predykatu, który musi mieć ścisłe słabe porządkowanie dla par elementów z sekwencji. W przypadku predykatu *pred*(*X*, *Y*):

- Strict oznacza, że *pred*(*x*, *x*) ma wartość false.

- Słabe oznacza, że *X* i *Y* mają równoważne porządkowanie, jeśli \! *pred*(*x*, *Y*)  && \! *pred*(*y*, *x*) (*x*  ==  *Y* nie musi być zdefiniowana).

- Porządkowanie oznacza, że *pred*(*x*, *Y*)  && *pred*(*Y*, *z*) implikuje *pred*(*x*, *z*).

Niektóre z tych algorytmów niejawnie używają predykatu *x* \< *Y*. Other predicates that typically satisfy the strict weak ordering requirement are *X* > *Y*, `less` (*X*, *Y*) i `greater` (*x*, *y*). Należy jednak zauważyć, że predykaty takie jak *X* \<= *Y* and *X* > =  *Y* nie spełniają tego wymagania.

Sekwencja elementów wyznaczono przez Iteratory w zakresie \[ *pierwszy*, *ostatni*) jest sekwencją uporządkowaną według operatora **<** , jeśli dla każdego *N* z zakresu \[ od 0, *ostatniego*  -  *pierwszego*) i dla każdego *M* w zakresie (*N*, *ostatni*  -  *pierwszy*) predykat \! ( \* (*pierwszy*  +  *M*) < \* (*pierwsze*  +  *n*)) ma wartość true. (Należy zauważyć, że elementy są sortowane w kolejności rosnącej). Funkcja predykatu `operator<` lub wszelkie jej zamiany nie mogą zmieniać żadnego z argumentów operacji. Musi ona dawać ten sam wynik **bool** przy każdej ocenie i musi dać ten sam wynik, jeśli kopia jednego z operandów jest zastępowana dla operandu. Ponadto musi nałożyć ścisłe słabe porządkowanie dla operandów, które porównuje.

Sekwencja elementów oznaczona przez Iteratory w zakresie \[ `First` , `Last` ) jest stertą uporządkowaną według `operator<` IF, dla każdego *N* z zakresu \[ 1, *ostatniego*  -  *pierwszego*) predykat \! ( \* _pierwszy_  <  \* (*pierwszy*  +  *N*)) ma wartość true. (Pierwszy element jest największą.) Struktura wewnętrzna jest w inny sposób znana tylko w przypadku funkcji szablonu [make_heap](algorithm-functions.md#make_heap), [pop_heap](algorithm-functions.md#pop_heap)i [push_heap](algorithm-functions.md#push_heap). Podobnie jak w przypadku kolejności uporządkowanej, funkcji predykatu `operator<` lub wszelkich zastąpień dla niej, nie może zmienić któregokolwiek z operandów i musi nałożyć ścisłe niedokładne porządkowanie dla operandów, które porównuje. Musi ona dawać ten sam wynik **bool** przy każdej ocenie i musi dać ten sam wynik, jeśli kopia jednego z operandów jest zastępowana dla operandu.

Algorytmy standardowej biblioteki języka C++ znajdują się [\<algorithm>](algorithm.md) w [\<numeric>](numeric.md) plikach nagłówkowych i.

## <a name="see-also"></a>Zobacz też

[Dokumentacja standardowej biblioteki języka C++](cpp-standard-library-reference.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](thread-safety-in-the-cpp-standard-library.md)
