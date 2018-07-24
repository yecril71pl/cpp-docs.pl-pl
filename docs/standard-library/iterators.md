---
title: Iteratory | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- iterator conventions
- C++ Standard Library, iterator conventions
ms.assetid: 2f746be7-b37d-4bfc-bf05-be4336ca982f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bb8efba0146a0a230a85a7980f1e71381fcf4b2
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208405"
---
# <a name="iterators"></a>Iteratory

Iterator jest obiektem, który można przejść przez elementy kontenera standardowej biblioteki języka C++ i zapewniają dostęp do poszczególnych elementów. Kontenery standardowej biblioteki języka C++, podane przez wszystkie Iteratory, tak aby algorytmy mogą uzyskać dostęp do ich elementów w standardowy sposób bez konieczności zainteresowanych przy użyciu typu kontenera elementy są przechowywane w.

Możesz użyć Iteratory, które jawnie przy użyciu elementu członkowskiego i funkcje globalne, takie jak begin() i metodę end() i operatorów takich jak ++ i--do przechodzenia do przodu lub Wstecz. Umożliwia także Iteratory niejawnie zakres-pętli for lub (w przypadku niektórych typów iteratora) operator indeksu dolnego [].

W standardowej bibliotece języka C++ na początek sekwencji lub zakres jest pierwszym elementem. Koniec sekwencji lub zakres, zawsze jest definiowany jako jednym elementem. Funkcje globalne początku i końcu zwracany Iteratory do określonego kontenera. Pętla typowe iteratora jawne za pośrednictwem wszystkich elementów w kontenerze wygląda następująco:

```cpp
vector<int> vec{ 0,1,2,3,4 };
for (auto it = begin(vec);

it != end(vec);

it++)
{  // Access element using dereference operator
    cout <<*it <<" ";
}
```

Ten sam efekt można osiągnąć po prostu z szerokim zakresem — Pętla for:

```cpp
for (auto num : vec)
 {  // no deference operator
    cout <<num <<" ";
 }
```

Istnieje pięć kategorii iteratorów. W kolejności power zwiększenia dostępne są następujące kategorie:

- **Dane wyjściowe**. Iterator danych wyjściowych `X` może przejść do przodu przez sekwencję przy użyciu ++ operatora i można zapisać elementu tylko raz przy użyciu \* operatora.

- **Dane wejściowe**. Iterator danych wejściowych `X` może przejść do przodu przez sekwencję przy użyciu ++ operatora i może odczytać element dowolną liczbę razy za pomocą \* operatora. Możesz porównać Iteratory wejściowych przy użyciu ++ i! = operatorów. Po zwiększa się wszystkie kopie iterator danych wejściowych, brak pozostałe kopie bezpiecznie można porównywać, wyłuskiwany lub zwiększona po tej dacie.

- **Do przodu**. Iterator do przodu `X` może przejść do przodu przez przy użyciu sekwencji ++ — operator i może odczytać dowolny element lub zapisać elementy o wartości innej niż stała dowolną liczbę razy przy użyciu \* operatora. Dostęp do elementów członkowskich elementu przy użyciu -> — operator i porównać tworzyć Iteratory do przodu przy użyciu == i! = operatorów. Można tworzyć kopie iterator do przodu, z których każdy może być wyłuskany i zwiększany niezależnie. Iterator do przodu, który jest inicjowany bez odwołania do dowolnego kontenera jest nazywany iterator do przodu o wartości null. Iteratory do przodu o wartości null zawsze są sobie równe.

- Dwukierunkowy. Iterator dwukierunkowy `X` mogą być wykonywane iterator do przodu. Możesz można jednak również zmniejszyć iteratora dwukierunkowego, podobnie jak w —`X`, `X`—, lub (`V` = \*`X`—). Można dostęp do elementów członkowskich elementu, a następnie porównaj dwukierunkowe Iteratory w taki sam sposób, jak tworzyć Iteratory do przodu.

- **Losowym**. Iterator dostępu swobodnego `X` mogą być wykonywane iterator dwukierunkowy. Za pomocą iteratora dostępu swobodnego, można użyć [] operator indeksu dolnego do dostępu do elementów. Możesz użyć +, -, operatory += i-= przenoszenia do przodu lub Wstecz określonej liczby elementów i obliczyć odległość między Iteratory. Możesz porównać dwukierunkowe Iteratory przy użyciu ==,! =, \<, >, \<= i > =.

Wszystkie Iteratory można przypisać lub kopiowany. Są zakłada się, że obiekty lekkie i są one często przekazane i zwracane przez wartość, nie przez odwołanie. Należy zauważyć, że żadne operacje opisane wcześniej może zgłosić wyjątek podczas wykonywania na prawidłowe iteratora.

Hierarchia kategorii iteratora można podsumować, pokazując sekwencje trzech. Aby uzyskać dostęp tylko do zapisu do sekwencji użyć dowolnego z:

> iterator danych wyjściowych<br/>
> -> iterator do przodu<br/>
> -> iteratora dwukierunkowego<br/>
> -> iteratora dostępu swobodnego<br/>

Strzałka w prawo oznacza "może być zastąpiony." Dowolny algorytm, który wywołuje dla iteratora danych wyjściowych powinien działać dobrze z iterator do przodu, na przykład, ale *nie* odwrotnie.

Aby uzyskać dostęp tylko do odczytu do sekwencji można użyć dowolnego z:

> iterator danych wejściowych<br/>
> -> iterator do przodu<br/>
> -> iteratora dwukierunkowego<br/>
> -> iteratora dostępu swobodnego<br/>

Iterator danych wejściowych jest najsłabsza wszystkie kategorie, w tym przypadku.

Na koniec uzyskać dostęp do odczytu/zapisu do sekwencji, umożliwiają wszystkich:

> iterator do przodu<br/>
> -> iteratora dwukierunkowego<br/>
> -> iteratora dostępu swobodnego<br/>

Wskaźnik do obiektu zawsze może służyć jako iterator dostępu swobodnego, dzięki czemu może służyć jako dowolnej kategorii iteratora, gdy obsługuje dostęp do odczytu/zapisu do sekwencji, który ją określa.

Iterator `Iterator` innego niż obiekt wskaźnika musi także definiować typy elementów członkowskich, wymagane przez specjalizację `iterator_traits<Iterator>`. Należy pamiętać, że te wymagania mogą zostać spełnione przez wyprowadzanie `Iterator` z publicznej klasy bazowej [iteratora](../standard-library/iterator-struct.md).

Należy zapoznać się z ze zobowiązania i ograniczenia wystąpienia każdej kategorii iteratora, aby zobaczyć, jak Iteratory są używane przez kontenery i algorytmy standardowej biblioteki języka C++.

> [!NOTE]
> Możesz uniknąć używania iteratorów jawnie przy użyciu zakresu-pętli for. Aby uzyskać więcej informacji, zobacz [Range-based for, instrukcja](../cpp/range-based-for-statement-cpp.md).

Visual C++ oferuje teraz Iteratory sprawdzane i Iteratory debugowania, aby upewnić się, że nie zastępuj granice kontenera. Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md) i [Debug Iterator Support](../standard-library/debug-iterator-support.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
