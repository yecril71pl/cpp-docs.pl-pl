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
ms.openlocfilehash: a0a1165d731e44568d530e3ed919d73e2a3e8e5e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648035"
---
# <a name="algorithms"></a>Algorytmy

Algorytmy są integralną częścią standardowej biblioteki języka C++. Algorytmy nie działają z kontenerami, samodzielnie, ale raczej z iteratorami. W związku z tym ten sam algorytm może służyć przez większość, jeśli nie dla wszystkich kontenerów standardowej biblioteki języka C++. W tej sekcji omówiono konwencje i terminologii algorytmów standardowej biblioteki języka C++.

## <a name="remarks"></a>Uwagi

Opisy funkcji szablonu algorytm stosować kilka skróconą wyrażenia:

- Wyrażenie "w zakresie \[ *A*, *B*)" oznacza, że Sekwencja zero lub więcej wartości dyskretnych, począwszy od *A* maksymalnie z wyjątkiem *B* . Zakres jest prawidłowy tylko wtedy, gdy *B* jest dostępny z *A;* można przechowywać *A* w obiekcie *N* (*N*  =  *A*), Zwiększ obiekt zero lub więcej razy (++*N*), i zastosować obiekt równe *B* po skończoną liczbę przyrostów (*N*   ==  *B*).

- Wyrażenie "każdego *N* w zakresie \[ *A*, *B*)" oznacza, że *N* zaczyna się od wartości *A*i następuje zero lub więcej razy do momentu jej jest równa wartości *B*. Przypadek *N* == *B* nie znajduje się w zakresie.

- Wyrażenie "najmniejszą wartość z *N* w zakresie \[ *A*, *B*) tak, aby *X*" oznacza, że warunek *X* jest określany dla poszczególnych *N* w zakresie \[ *A*, *B*) aż do warunku *X*jest spełniony.

- Wyrażenie "najwyższą wartość *N* w zakresie \[ *A*, *B*) tak, aby *X* oznacza, że *X* jest określany dla poszczególnych *N* w zakresie \[ *A*, *B*). Funkcja przechowuje w *K* kopię *N* każdym warunku *X* jest spełniony. Jeśli wystąpi taki magazyn, funkcja zastępuje końcowa wartość *N*, która jest równa *B*, z wartością *K*. Dwukierunkowe lub iteratora dostępu swobodnego, jednak ją można również oznaczają, że *N* rozpoczyna się od najwyższą wartość z zakresu i jest zmniejszana w zakresie aż do warunku *X* jest spełniony.

- Wyrażenia takie jak *X* - *Y*, gdzie *X* i *Y* może być Iteratory niż iteratorami dostępu swobodnego, jest przeznaczona w sensie matematycznym. Funkcja nie zwraca operatora **-** Jeśli musisz określić, takich wartości. To samo dotyczy również dla wyrażenia takie jak *X* + *N* i *X* - *N*, gdzie *N*  typu liczby całkowitej.

Algorytmy kilka użyć predykatu, który wykonuje porównania parowania, takie jak za pomocą `operator==`, umożliwiające uzyskanie **bool** wynik. Funkcja predykatu `operator==`, lub zastępuje go, nie mogą zmieniać jeden z argumentów. One musi dostarczyć takie same **bool** wyniku za każdym razem, gdy zostaje oceniony i musi mieć zdolność ten sam wynik, jeśli argument zastępuje kopię jeden z operandów.

Algorytmy kilka użyć predykatu, który musi powodować ścisłe słabe porządkowanie w pary elementów z sekwencji. Dla predykatu *pred*(*X*, *Y*):

- Strict oznacza, że *pred*(*X*, *X*) ma wartość false.

- Weak oznacza, że *X* i *Y* mieć równoważne if szeregowania \! *pred*(*X*, *Y*) & & \! *pred*(*Y*, *X*) (*X* == *Y*nie musi być zdefiniowana).

- Kolejność oznacza, że *pred*(*X*, *Y*) & & *pred*(*Y*, *Z*) oznacza *pred*(*X*, *Z*).

Niektóre z tych algorytmów niejawnie orzeczenie *X* \< *Y*. Inne predykaty, zwykle spełniających ścisłym słabym porządkowanie wymagania są *X* > *Y*, `less`(*X*, *Y*), a `greater`(*X*, *Y*). Należy pamiętać, jednak, predykaty takich jak *X* \< =  *Y* i *X* >= *Y* nie spełniają to wymaganie.

Sekwencja elementów wyznaczony przez Iteratory w zakresie \[ *pierwszy*, *ostatniego*) to sekwencja określona przez operator **<** if, dla każdego  *N* w zakresie \[0, *ostatniego* - *pierwszy*) i dla każdego *M* w zakresie (*N*, *Ostatniego* - *pierwszy*) predykat \!(\*(*pierwszy*  +  *M*) < \*(*pierwszy* + *N*)) ma wartość true. (Zwróć uwagę, że elementy są sortowane w kolejności rosnącej). Funkcja predykatu `operator<`, lub zastępuje go, nie mogą zmieniać jeden z argumentów. One musi dostarczyć takie same **bool** wyniku za każdym razem, gdy zostaje oceniony i musi mieć zdolność ten sam wynik, jeśli argument zastępuje kopię jeden z operandów. Ponadto należy nakładają, ścisłe słabe porządkowanie w przypadku argumentów operacji, które są porównywane.

Sekwencja elementów wyznaczony przez Iteratory w zakresie \[ `First`, `Last`) sterty są uporządkowane według `operator<` if, dla każdego *N* w zakresie \[1, *ostatnie*  -  *Pierwszy*) predykat \!(\*_pierwszy_ < \*(*pierwszy*  +  *N*)) ma wartość true. (Pierwszy element jest największy). Jego wewnętrznej struktury w przeciwnym razie znanego tylko funkcje szablonu [make_heap —](../standard-library/algorithm-functions.md#make_heap), [pop_heap —](../standard-library/algorithm-functions.md#pop_heap), i [push_heap —](../standard-library/algorithm-functions.md#push_heap). Podobnie jak w przypadku uporządkowana sekwencja funkcji predykatu `operator<`, lub zastępuje go, nie mogą zmieniać jeden z argumentów i może nałożyć, ścisłe słabe porządkowanie w przypadku argumentów operacji porównywania. One musi dostarczyć takie same **bool** wyniku za każdym razem, gdy zostaje oceniony i musi mieć zdolność ten sam wynik, jeśli argument zastępuje kopię jeden z operandów.

Algorytmy standardowej biblioteki języka C++ znajdują się w [ \<algorytm >](../standard-library/algorithm.md) i [ \<liczbowych >](../standard-library/numeric.md) plików nagłówkowych.

## <a name="see-also"></a>Zobacz także

[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
