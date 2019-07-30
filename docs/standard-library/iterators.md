---
title: Iteratory
ms.date: 11/04/2016
helpviewer_keywords:
- iterator conventions
- C++ Standard Library, iterator conventions
ms.assetid: 2f746be7-b37d-4bfc-bf05-be4336ca982f
ms.openlocfilehash: ec23cbea63bc6884a361600362fcf0061e927ca6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449962"
---
# <a name="iterators"></a>Iteratory

Iterator jest obiektem, który może wykonywać iterację elementów w C++ kontenerze biblioteki standardowej i zapewniać dostęp do poszczególnych elementów. Wszystkie C++ Kontenery biblioteki standardowej zapewniają Iteratory, tak aby algorytmy mogły uzyskiwać dostęp do ich elementów w standardowy sposób, bez konieczności używania typu kontenera, w którym są przechowywane elementy.

Iteratorów można użyć jawnie przy użyciu funkcji składowych i globalnych, `begin()` takich `end()` jak i **--** i operatorów **++** , takich jak i, aby przejść do przodu lub do tyłu. Można również użyć iteratorów niejawnie z zakresem pętli for lub (dla niektórych typów iteratorów) operatora  **\[** indeksu dolnego].

W bibliotece C++ standardowej początek sekwencji lub zakresu jest pierwszym elementem. Koniec sekwencji lub zakresu jest zawsze zdefiniowany jako jeden poza ostatnim elementem. Funkcje `begin` globalne i `end` zwracają Iteratory do określonego kontenera. Typowa jawna pętla iteratora dla wszystkich elementów w kontenerze wygląda następująco:

```cpp
vector<int> vec{ 0,1,2,3,4 };
for (auto it = begin(vec); it != end(vec); it++)
{
    // Access element using dereference operator
    cout << *it << " ";
}
```

Te same czynności można wykonać w przypadku pętli Range for:

```cpp
for (auto num : vec)
{
    // no deference operator
    cout << num << " ";
}
```

Istnieje pięć kategorii iteratorów. Kategorie są następujące:

- **Dane wyjściowe**. **++** __\*__ *Iterator* `X` danych wyjściowych może wykonać iterację w przód przez sekwencję przy użyciu operatora i można napisać element tylko raz, przy użyciu operatora.

- **Dane wejściowe**. **&ast;** *Iterator* `X` danych wejściowych może przechodzić do przodu przez sekwencję przy użyciu operatora + + i może odczytywać element dowolną liczbę razy przy użyciu operatora. Iteratory wejściowe można porównać przy użyciu **++** operatorów i **! =** . Po zwiększeniu każdej kopii iteratora danych wejściowych żadna z innych kopii nie może być bezpiecznie porównana, wykorzystana lub zwiększana później.

- **Do przodu**. **&ast;** *Iterator* `X` do przodu może przechodzić do przodu przez sekwencję przy użyciu operatora + + i może odczytywać dowolny element lub zapisywać elementy inne niż const dowolną liczbę razy przy użyciu operatora. Można uzyskać dostęp do składowych elementów przy **->** użyciu operatora i porównać Iteratory do przodu przy **==** użyciu operatorów i **! =** . Można utworzyć wiele kopii iteratora, z których każda może zostać wykorzystana i jednocześnie narastać. Iterator do przodu, który jest inicjowany bez odwołania do żadnego kontenera jest nazywany *iteratorem do przodu o wartości null*. Iteratory do przodu o wartości null zawsze porównują.

- **Dwukierunkowy**. *Iterator* `X` dwukierunkowy może zamierzyć iterator do przodu. Można jednak również zmniejszyć iterator dwukierunkowy, jak w `--X`, `X--`lub `(V = *X--)`. Można uzyskać dostęp do elementów członkowskich elementów i porównać Iteratory dwukierunkowe w taki sam sposób jak Iteratory do przodu.

- **Dostęp losowy**. *Iterator* `X` dostępu swobodnego może być miejscem iteratora dwukierunkowego. Dzięki iteratorowi dostępu losowego możesz  **\[użyć operatora indeksu** dolnego, aby uzyskać dostęp do elementów. Można użyć **+** operatorów,, **-** **+=** i **-=** , aby przenieść do przodu lub do tyłu określoną liczbę elementów i obliczyć odległość między iteratorami. Można porównać **==** Iteratory dwukierunkowe przy użyciu, **! =** , **\<** , **\< =** **>** ,, i **>=** .

Wszystkie Iteratory mogą zostać przypisane lub skopiowane. Zakłada się, że są to obiekty lekkie i często są przesyłane i zwracane przez wartość, a nie przez odwołanie. Należy zauważyć, że żadna z opisanych wcześniej operacji nie może zgłosić wyjątku podczas wykonywania w prawidłowym iteratoru.

Hierarchię kategorii iteratorów można podsumowywać, pokazując trzy sekwencje. Aby uzyskać dostęp tylko do zapisu do sekwencji, można użyć dowolnego z:

> iterator wyjściowy \
> -> iterator do przodu \
> -> iterator dwukierunkowy \
> -> Iterator dostępu swobodnego

Strzałka w prawo oznacza "może być zastąpiona przez." Dowolny algorytm, który wywołuje dla iteratora danych wyjściowych powinien dobrze z iteratorem do przodu, na przykład, ale *nie* w inny sposób.

Aby uzyskać dostęp tylko do odczytu do sekwencji, można użyć dowolnego z:

> Iterator danych wejściowych \
> -> iterator do przodu \
> -> iterator dwukierunkowy \
> -> Iterator dostępu swobodnego

Iterator danych wejściowych jest najsłabszy ze wszystkich kategorii, w tym przypadku.

Na koniec w przypadku dostępu do odczytu i zapisu do sekwencji można użyć dowolnego z:

> Iterator progresywny \
> -> iterator dwukierunkowy \
> -> Iterator dostępu swobodnego

Wskaźnik obiektu może być zawsze używany jako Iterator dostępu swobodnego, więc może działać jako każda kategoria iteratora, jeśli obsługuje on właściwy dostęp do odczytu/zapisu do wyznaczonej przez siebie sekwencji.

Iterator `Iterator` inny niż wskaźnik obiektu musi także definiować typy elementów członkowskich wymagane przez `iterator_traits<Iterator>`specjalizację. Należy zauważyć, że te wymagania mogą być spełnione przez `Iterator` wyprowadzanie z publicznego [iteratora](../standard-library/iterator-struct.md)klas podstawowych.

Ważne jest zrozumienie niesie obietnice zwiększenia i ograniczeń każdej kategorii iteratora, aby zobaczyć, jak Iteratory są używane przez kontenery i algorytmy w C++ standardowej bibliotece.

> [!NOTE]
> Można uniknąć używania iteratorów jawnie za pomocą funkcji Range dla pętli. Aby uzyskać więcej informacji, zobacz [zakres instrukcji for](../cpp/range-based-for-statement-cpp.md).

Firma C++ Microsoft oferuje teraz sprawdzone Iteratory i Iteratory debugowania, aby upewnić się, że nie zastąpisz granic kontenera. Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md) i [Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md).

## <a name="see-also"></a>Zobacz także

[C++Dokumentacja biblioteki standardowej](../standard-library/cpp-standard-library-reference.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
