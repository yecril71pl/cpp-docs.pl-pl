---
title: Iteratory | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- iterator conventions
- C++ Standard Library, iterator conventions
ms.assetid: 2f746be7-b37d-4bfc-bf05-be4336ca982f
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4c1012add5e2a62110a8f10792a0ea2bb878dce2
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="iterators"></a>Iteratory

Iteratora jest obiekt, który można iteracja elementów w kontenerze standardowa biblioteka C++ i zapewnienia dostępu do poszczególnych elementów. Standardowa biblioteka C++ kontenery oferować Iteratory umożliwiając algorytmów dostęp do swoich elementów w standardowy sposób bez konieczności zajmować się typ kontenera elementy są przechowywane w.

Można użyć Iteratory jawnie przy użyciu elementu członkowskiego i funkcje globalne, takie jak begin() i end() i operatory takich jak ++ i--przenoszenia do przodu i do tyłu. Można również używać Iteratory niejawnie z zakresu-pętli for lub (w przypadku niektórych typów iteratora) operator indeksu dolnego [].

W standardowej bibliotece C++ na początku sekwencji lub zakres jest pierwszym elementem. Koniec sekwencji lub zakres zawsze jest definiowany jako jeden po ostatnim elemencie. Funkcje globalne rozpoczęcia i zakończenia Iteratory powrotu do określonego kontenera. Pętla typowe iteratora jawne przez wszystkie elementy w kontenerze wygląda następująco:

```cpp
vector<int> vec{ 0,1,2,3,4 };
for (auto it = begin(vec);

it != end(vec);

it++)
{  // Access element using dereference operator
    cout <<*it <<" ";
}
```

Ten sam efekt można zrobić po prostu zakres-Pętla for:

```cpp
for (auto num : vec)
 {  // no deference operator
    cout <<num <<" ";
 }
```

Istnieje pięć kategorii iteratorów. W porządku rosnących zasilania kategorie są:

- **Dane wyjściowe**. Iteratora dane wyjściowe `X` można przejść do przodu przez sekwencję przy użyciu ++ operatora i można zapisać elementu tylko raz przy użyciu * — operator.

- **Dane wejściowe**. Wejściowy iteratora `X` można przejść do przodu przez sekwencję przy użyciu ++ operatora i można odczytać elementu dowolną liczbę razy przy użyciu * — operator. Możesz porównać Iteratory wejściowego przy użyciu ++ i! = operatory. Po zwiększa się wszystkie kopie iteratora wejściowych, brak pozostałe kopie można bezpiecznie porównać, wyłuskiwany lub zwiększany później.

- **Przekazuj**. Do przodu iteratora `X` można przejść do przodu przez przy użyciu sekwencji ++ — operator i można czytać dowolny element lub zapisywania elementów z systemem innym niż stała dowolną liczbę razy przy użyciu * — operator. Dostęp do elementów członkowskich elementu przy użyciu -> — operator i porównać do przodu Iteratory przy użyciu == i! = operatory. Można tworzyć kopie iteratora do przodu, z których każdy wyłuskiwany i zwiększany niezależnie. Iteratora do przodu, który został zainicjowany bez odwołania do dowolnego kontenera jest nazywany null iteratora do przodu. Wartości null do przodu Iteratory zawsze Porównuj takie same.

- Dwukierunkowego. Iterator dwukierunkowego `X` można przeprowadzać iteratora do przodu. Możesz można jednak również zmniejszyć iteratora dwukierunkowego, podobnie jak w--`X`, `X`—, lub (`V` = *`X`--). Możesz dostęp do elementów członkowskich elementu i porównania Iteratory dwukierunkowego w taki sam sposób jak Iteratory do przodu.

- **Dostęp losowy**. Iterator dostępie swobodnym `X` można przeprowadzać iteratora dwukierunkowego. Z iteratora dostępie swobodnym służy [] — operator indeksu dolnego do dostępu do elementów. Można użyć +, -, += i-= operatory przenoszenia do przodu i do tyłu określoną liczbę elementów, jak i do obliczania odległość między Iteratory. Możesz porównać Iteratory dwukierunkowego przy użyciu ==,! =, \<, >, \<=, a > =.

Iteratory wszystkich można przypisać lub skopiowane. Obiekty lekkie są rozpatrywane i są często przekazane i zwrócony przez wartość, nie przez odwołanie. Należy pamiętać, że żadna z operacji opisany wcześniej throw Wystąpił wyjątek podczas wykonywania na prawidłową iteratora.

Hierarchia kategorii iteratora można podsumować pokazując trzy sekwencji. Aby uzyskać dostęp tylko do zapisu do sekwencji można użyć dowolnego z:

> dane wyjściowe iteratora<br/>
> -> do przodu iteratora<br/>
> -> dwukierunkowego iteratora<br/>
> -> dostępie swobodnym iteratora<br/>

Strzałka w prawo oznacza "może zostać zastąpiona." Dowolny algorytm, który wywołuje iteratora dane wyjściowe powinny działa dobrze z iteratora do przodu, na przykład, ale *nie* odwrotnie.

Aby uzyskać dostęp tylko do odczytu do sekwencji można użyć dowolnego z:

> wejściowy iteratora<br/>
> -> do przodu iteratora<br/>
> -> dwukierunkowego iteratora<br/>
> -> dostępie swobodnym iteratora<br/>

W tym przypadku jest najsłabszą wszystkich kategorii wejściowych iteratora.

Na koniec do odczytu i zapisu do sekwencji, możesz można użyć dowolnego z:

> do przodu iteratora<br/>
> -> dwukierunkowego iteratora<br/>
> -> dostępie swobodnym iteratora<br/>

Wskaźnik do obiektu zawsze może stanowić iteratora dostępie swobodnym, więc jeśli obsługuje dostęp do odczytu/zapisu do sekwencji, który wyznacza ona może służyć jako każdej kategorii iteratora.

Iterator `Iterator` innej niż obiekt wskaźnika musi także definiować typy elementów członkowskich wymaganych przez specjalizacji `iterator_traits<Iterator>`. Należy pamiętać, że tych wymagań można spełnić przez wyprowadzanie `Iterator` z publicznej klasy podstawowej [iterator](../standard-library/iterator-struct.md).

Należy zapoznać się z ze zobowiązania i ograniczenia dotyczące każdej kategorii iteratora, aby zobaczyć, jak Iteratory używanych przez kontenery i algorytmy standardowa biblioteka C++.

> [!NOTE]
> Możesz uniknąć używania Iteratory jawnie za pomocą zakresu — dla pętli. Aby uzyskać więcej informacji, zobacz [na podstawie zakresu dla instrukcji](../cpp/range-based-for-statement-cpp.md).

Visual C++ oferuje teraz zaznaczone Iteratory i debugowania Iteratory zapewnienia niezastępowanie granice z kontenera. Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md) i [Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
