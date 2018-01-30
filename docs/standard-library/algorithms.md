---
title: Algorytmy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], C++ algorithm conventions
- algorithms [C++], C++
- C++ Standard Library, algorithms
- algorithm template function C++ library conventions
- conventions [C++], C++ algorithm
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5bc9d57f93b5d3ee537330ab16c2c9a02b6beead
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="algorithms"></a>Algorytmy
Algorytmy są integralną częścią standardowej biblioteki C++. Algorytmy nie działają z kontenerami samodzielnie, ale raczej z Iteratory. W związku z tym samym algorytm może służyć przez większość, jeśli nie dla wszystkich kontenerów standardowa biblioteka C++. W tej sekcji omówiono konwencje i terminologię algorytmów standardowa biblioteka C++.  
  
## <a name="remarks"></a>Uwagi  
 Opisy funkcji szablonu algorytm wykonać kilka fraz skrótu:  
  
-   Wyrażenie "w zakresie [*A*, *B*)" oznacza, że Sekwencja zero lub więcej wartości dyskretnych, począwszy od *A* do, ale nie obejmuje *B*. Zakres jest prawidłowy tylko wtedy, gdy *B* jest dostępny z *A;* można przechowywać *A* w obiekcie *N* (*N*  =  *A*), zwiększyć obiekt zero lub więcej razy (++*N*), i mieć obiekt porównanie *B* po skończoną liczbę przyrostów (N == B*).*  
  
-   Wyrażenie "każdego *N* z zakresu [*A*, *B*)" oznacza, że *N* rozpoczyna się od wartości *A* i jest zwiększany zero lub więcej razy, aż do jej równa wartości *B*. Przypadku *N* == *B* nie znajduje się w zakresie.  
  
-   Wyrażenie "najmniejszą wartość z *N* z zakresu [*A*, *B*) tak, aby *X*" oznacza, że warunek *X*jest określana dla każdego *N* z zakresu [*A*, *B*) do warunku *X* jest spełniony.  
  
-   Wyrażenie "najwyższą wartość *N* z zakresu [*A*, *B*) tak, aby *X* oznacza, że *X* jest określić dla każdej *N* z zakresu [*A*, *B*). Funkcja są przechowywane w `K` kopię *N* po każdej aktualizacji warunek *X* jest spełniony. W przypadku takich magazynu funkcja zastępuje końcowa wartość *N*, która jest równa *B*, z wartością `K`. Dwukierunkowy lub iteratora dostępie swobodnym, jednak ją można również oznaczają, że *N* rozpoczyna się od najwyższą wartość z zakresu i jest zmniejszana w zakresie do warunku *X* jest spełniony.  
  
-   Wyrażenia takie jak *X* - *Y*, gdzie *X* i *Y* może być Iteratory niż Iteratory dostępie swobodnym, mają w tym sensie, matematycznych. Funkcja nie zwraca operator **-**  Jeśli musisz określić takich wartości. Dotyczy to również wyrażeń takich jak *X* + *N* i *X* - *N*, gdzie *N*  jest typu Liczba całkowita.  
  
 Algorytmy kilka stosowania predykatu, który wykonuje porównania parowania, takich jak z `operator==`, umożliwiające uzyskanie `bool` wynik. Funkcja predykatu `operator==`, lub zastąpieniem, nie mogą zmieniać jeden z argumentów. One musi dostarczyć takie same `bool` powoduje za każdym razem będzie oceniana, i musi uzyskanie takiego samego wyniku, jeśli argument zastępuje kopię którykolwiek argument operacji.  
  
 Algorytmy kilka stosowania predykatu musi nałożyć strict słabe porządkowanie dla pary elementów z sekwencji. Dla predykatu `pr`(*X*, *Y*):  
  
-   Strict oznacza, że `pr`(*X*, *X*) ma wartość false.  
  
-   Niska oznacza, że *X* i *Y* mają równoważne if porządkowania!`pr` (*X*, *Y*) & &!`pr` (*Y*, *X*) (*X* == *Y* nie muszą być zdefiniowane).  
  
-   Porządkowanie oznacza, że `pr`(*X*, *Y*) & & `pr`(*Y*, Z) oznacza `pr`(*X*, Z).  
  
 Niektóre z tych algorytmów niejawnie użyć predykatu *X* \< *Y*. Są inne predykaty zwykle spełniających strict niska, kolejność wymaganie *X* > *Y*, **mniej**(*X*,  *Y*), a `greater`(*X*, *Y*). Uwaga, jednak, że predykaty takich jak *X* \< =  *Y* i *X* >= *Y* nie spełniają to wymaganie.  
  
 Sekwencję elementów wskazywany przez Iteratory z zakresu [`First`, `Last`) jest sekwencją uporządkowanych według operator **<**  if, dla każdego *N* w zakresie [0, `Last`  -  `First`) i dla każdego *M* w zakresie (N, `Last`  -  `First`) predykat! () \*(`First` + *M*) < \*(*pierwszy* + *N*)) ma wartość true. (Należy pamiętać, że elementy będą sortowane w kolejności rosnącej). Funkcja predykatu **operatora <**, lub zastąpieniem, nie mogą zmieniać jeden z argumentów. One musi dostarczyć takie same `bool` powoduje za każdym razem będzie oceniana, i musi uzyskanie takiego samego wyniku, jeśli argument zastępuje kopię którykolwiek argument operacji. Ponadto należy nałożyć strict słabe porządkowanie dla argumentów operacji, który porównuje.  
  
 Sekwencję elementów wskazywany przez Iteratory w zakresie [`First`, `Last`) jest sterty uporządkowanych według **operatora <** if, dla każdego *N* z zakresu [1, `Last`  -  `First`) predykat! (\*`First` < \*(`First` + *N*)) ma wartość true. (Pierwszy element to największa). Jego struktury wewnętrznej jest znany tylko na funkcje szablonu [make_heap —](../standard-library/algorithm-functions.md#make_heap), [pop_heap —](../standard-library/algorithm-functions.md#pop_heap), i [push_heap —](../standard-library/algorithm-functions.md#push_heap). W przypadku uporządkowanej kolejności, funkcja predykatu **operatora <**, zastępuje go, nie mogą zmieniać jeden z argumentów i musi nakłada strict słabe kolejności w wypadku argumentów operacji porównywania. One musi dostarczyć takie same `bool` powoduje za każdym razem będzie oceniana, i musi uzyskanie takiego samego wyniku, jeśli argument zastępuje kopię którykolwiek argument operacji.  
  
 Algorytmy standardowa biblioteka C++ znajdują się w [ \<algorytm >](../standard-library/algorithm.md) i [ \<liczbowych >](../standard-library/numeric.md) pliki nagłówków.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki C++ Standard](../standard-library/cpp-standard-library-reference.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

