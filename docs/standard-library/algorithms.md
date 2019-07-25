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
ms.openlocfilehash: d363dc3f06222121ac5efc79b30516ebd55ff539
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456483"
---
# <a name="algorithms"></a>Algorytmy

Algorytmy są podstawową częścią C++ standardowej biblioteki. Algorytmy nie działają z kontenerami, ale raczej z iteratorów. W związku z tym tego samego algorytmu można użyć w większości, jeśli nie wszystkie C++ Kontenery biblioteki standardowej. W tej sekcji omówiono konwencje i terminologię C++ standardowych algorytmów biblioteki.

## <a name="remarks"></a>Uwagi

Opisy funkcji szablonu algorytmu korzystają z kilku skróconych fraz:

- Wyrażenie "w zakresie \[*A*, *B*)" oznacza, że Sekwencja zero lub więcej wartości dyskretnych, począwszy od *A* maksymalnie z wyjątkiem*B*. Zakres jest prawidłowy tylko wtedy, gdy *B* jest dostępny z *A;* można przechowywać *A* w obiekcie *N* (*N*  =  *A*), Zwiększ obiekt zero lub więcej razy (++*N*), i zastosować obiekt równe *B* po skończoną liczbę przyrostów (*N*  ==  *B*).

- Wyrażenie "każdego *N* w zakresie \[*A*, *B*)" oznacza, że *N* zaczyna się od wartości *A*i następuje zero lub więcej razy do momentu jej jest równa wartości *B*. Przypadek *N* == *B* nie należy do zakresu.

- Fraza "najniższa wartość *N* w zakresie \[ *a*, *b*) taka, że *x*" oznacza, że warunek *x* jest określany dla każdego *N* w \[zakresie *a*, *b*) do momentu Warunek *X* został spełniony.

- Fraza "najwyższa wartość *N* w zakresie \[ *a*, *B*) taka, że *x* oznacza, że *x* jest określana dla każdego *N* w \[zakresie *a*, *b*). Funkcja zapisuje w *K* a kopię *N* za każdym razem, gdy spełniony jest warunek *X* . W przypadku wystąpienia dowolnego takiego magazynu funkcja zastępuje końcową wartość *N*, która jest równa *B*, z wartością *K*. Jednak dla iteratora dwukierunkowego lub swobodnego dostępu, można również oznaczać, że *N* zaczyna się od najwyższej wartości zakresu i jest zmniejszany do zakresu do momentu spełnienia warunku *X* .

- Wyrażenia takie jak *x* - *Y*, gdzie *x* i *Y* mogą być iteratorami innymi niż Iteratory dostępu swobodnego, są zamierzone w sensie matematycznym. Funkcja nie zwraca operatora **-** Jeśli musisz określić, takich wartości. To samo dotyczy również dla wyrażenia takie jak *X* + *N* i *X* - *N*, gdzie *N* typu liczby całkowitej.

Kilka algorytmów używa predykatu, który wykonuje porównanie parowania, takie jak with `operator==`, w celu uzyskania wyniku **logicznego** . Funkcja `operator==`predykatu lub wszelkie jej zamiany nie mogą zmieniać żadnego z argumentów operacji. Musi ona dawać ten sam wynik **bool** przy każdej ocenie i musi dać ten sam wynik, jeśli kopia jednego z operandów jest zastępowana dla operandu.

Kilka algorytmów używa predykatu, który musi mieć ścisłe słabe porządkowanie dla par elementów z sekwencji. W przypadku predykatu *pred*(*X*, *Y*):

- Strict oznacza, że *pred*(*x*, *x*) ma wartość false.

- Słabe oznacza, że *X* i *Y* mają równoważne porządkowanie, \!Jeśli *pred*(*x*, *Y*) & \!& *pred*(*y*, *x*) (*x* == *Y* nie należy zdefiniować).

- Porządkowanie oznacza, że *pred*(*x*, *Y*) & & *pred*(*Y*, *z*) implikuje *pred*(*X*, *z*).

Niektóre z tych algorytmów niejawnie używają predykatu *X* \< *Y*. Inne predykaty, które zwykle spełniają rygorystyczne wymagania dotyczące niesłabszego określania `less`kolejności, to *X* > *Y*, ( `greater`*x*, *Y*) i (*x*, *y*). Należy jednak zauważyć, że predykaty takie jak *x* \< =  *y* i *x* >= *y* nie spełniają tego wymagania.

Sekwencja elementów wyznaczony przez Iteratory w zakresie \[*pierwszy*, *ostatniego*) to sekwencja określona przez operator **<** if, dla każdego *N* w zakresie \[0, *ostatniego* - *pierwszy*) i dla każdego *M* w zakresie (*N*, *Ostatniego* - *pierwszy*) predykat \!(\*(*pierwszy* + *M*) < \*(*pierwszy* + *N*)) ma wartość true. (Należy zauważyć, że elementy są sortowane w kolejności rosnącej). Funkcja `operator<`predykatu lub wszelkie jej zamiany nie mogą zmieniać żadnego z argumentów operacji. Musi ona dawać ten sam wynik **bool** przy każdej ocenie i musi dać ten sam wynik, jeśli kopia jednego z operandów jest zastępowana dla operandu. Ponadto musi nałożyć ścisłe słabe porządkowanie dla operandów, które porównuje.

Sekwencja elementów \[oznaczona przez Iteratory w zakresie -  \[ `operator<` `First`, `Last`) jest stertą uporządkowaną według IF, dla każdego *N* z zakresu 1, *ostatniego* *pierwszego*) predykat \!(\*_First_ *(pierwsze*N))ma wartość true. +  < \* (Pierwszy element jest największą.) Struktura wewnętrzna jest w inny sposób znana tylko w przypadku funkcji szablonu [make_heap](../standard-library/algorithm-functions.md#make_heap), [pop_heap](../standard-library/algorithm-functions.md#pop_heap)i [push_heap](../standard-library/algorithm-functions.md#push_heap). Podobnie jak w przypadku kolejności uporządkowanej, funkcji `operator<`predykatu lub wszelkich zastąpień dla niej, nie może zmienić któregokolwiek z operandów i musi nałożyć ścisłe niedokładne porządkowanie dla operandów, które porównuje. Musi ona dawać ten sam wynik **bool** przy każdej ocenie i musi dać ten sam wynik, jeśli kopia jednego z operandów jest zastępowana dla operandu.

Algorytmy C++ standardowej biblioteki znajdują się w [ \<algorytmach >](../standard-library/algorithm.md) i [ \<liczbowych >](../standard-library/numeric.md) plikach nagłówkowych.

## <a name="see-also"></a>Zobacz także

[C++Dokumentacja biblioteki standardowej](../standard-library/cpp-standard-library-reference.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
