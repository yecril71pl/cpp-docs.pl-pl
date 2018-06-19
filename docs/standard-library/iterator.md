---
title: '&lt;Iterator&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <iterator>
- iterator/std::<iterator>
dev_langs:
- C++
helpviewer_keywords:
- iterator header
ms.assetid: c61a3962-f3ed-411a-b5a3-e8b3c2b500bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5066e793c58dca9ccc12ccc159a010654df3efbc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860674"
---
# <a name="ltiteratorgt"></a>&lt;iterator&gt;

Definiuje iteratory pierwotne, iteratory wstępnie zdefiniowane i iteratory strumienia, a także kilka szablonów pomocniczych. Wstępnie zdefiniowane iteratory obejmują adaptery wstawiania i odwracania. Istnieją trzy klasy adapterów iteratorów wstawiania: na przód, na tył i ogólne. Zapewniają one semantykę wstawiania zamiast semantyki zastępowania, którą dostarczają iteratory elementów członkowskich.

## <a name="syntax"></a>Składnia

```cpp
#include <iterator>

```

## <a name="remarks"></a>Uwagi

Iteratory są uogólnieniem wskaźników, abstrahując od ich wymagań w sposób, który pozwala programowi C++ na pracę z różnymi strukturami danych w jednolity sposób. Iteratory pełnią rolę pośredników pomiędzy kontenerami i algorytmami ogólnymi. Zamiast pracy na poszczególnych typach danych, algorytmy są zdefiniowane do pracy w zakresie określonym przez typ iteratora. Każda struktura danych, która spełnia wymagania iteratora, może być eksploatowana przez algorytm. Istnieje pięć typów lub kategorii iteratora, z których każda ma własne wymagania i funkcje wynikowe:

- Wyjście: przenoszenie do przodu, może przechowywać wartości, ale nie je pobierać, dostarczone przez ostream i inserter.

- Wejście: przenoszenie do przodu, może pobierać wartości, ale nie je przechowywać, dostarczone przez istream.

- Do przodu: przenoszenie do przodu może przechowywać i pobierać wartości.

- Dwukierunkowe: przenoszenie do przodu i do tyłu, może przechowywać i pobierać wartości dostarczone przez listy, zestawy, zestawy wielokrotne, mapy i mapy wielokrotne.

- Dostęp swobodny: elementy dostępne w dowolnej kolejności, może przechowywać i pobierać wartości, dostarczone przez vector, deque, string i array.

Iteratory, które mają większe wymagania i bardziej wydajny dostęp do elementów, mogą być używane zamiast iteratorów z mniejszymi wymaganiami. Na przykład, jeżeli iterator do przodu zostanie wywołany, wówczas można zamiast niego użyć iteratora swobodnego dostępu.

Visual Studio dodaje rozszerzenia do iteratorów standardowej biblioteki C++, w celu uwzględnienia różnych sytuacji trybu debugowania dla iteratorów sprawdzonych i niesprawdzonych. Aby uzyskać więcej informacji, zobacz [bezpieczne biblioteki: Standardowa biblioteka C++](../standard-library/safe-libraries-cpp-standard-library.md).

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[advance](../standard-library/iterator-functions.md#advance)|Inkrementuje iterator o określoną liczbę pozycji.|
|[back_inserter](../standard-library/iterator-functions.md#back_inserter)|Tworzy iterator, który może wstawiać elementy z tyłu określonego kontenera.|
|[begin](../standard-library/iterator-functions.md#begin)|Pobiera iterator do pierwszego elementu w określonym kontenerze.|
|[cbegin](../standard-library/iterator-functions.md#cbegin)|Pobiera stały iterator do pierwszego elementu w określonym kontenerze.|
|[cend](../standard-library/iterator-functions.md#cend)|Pobiera stały iterator do elementu, który następuje po ostatnim elemencie w określonym kontenerze.|
|[odległość](../standard-library/iterator-functions.md#distance)|Określa liczbę przyrostów między położeniami, do których odnoszą się dwa iteratory.|
|[Koniec](../standard-library/iterator-functions.md#end)|Pobiera iterator do elementu, który następuje po ostatnim elemencie w określonym kontenerze.|
|[front_inserter](../standard-library/iterator-functions.md#front_inserter)|Tworzy iterator, która może wstawiać elementy z przodu określonego kontenera.|
|[Wstawianie](../standard-library/iterator-functions.md#inserter)|Adapter iteratora, który dodaje nowy element do kontenera w określonym punkcie wstawiania.|
|[make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator)|Tworzy [checked_array_iterator —](../standard-library/checked-array-iterator-class.md) które mogą być używane przez inne algorytmy. **Uwaga:** tej funkcji to rozszerzenie Microsoft standardowej biblioteki C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft.|
|[make_move_iterator](../standard-library/iterator-functions.md#make_move_iterator)|Zwraca iterator przenoszenia, zawierający podany iterator taki, jak jego przechowywany iterator podstawowy.|
|[make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator)|Tworzy [unchecked_array_iterator —](../standard-library/unchecked-array-iterator-class.md) które mogą być używane przez inne algorytmy. **Uwaga:** tej funkcji to rozszerzenie Microsoft standardowej biblioteki C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft.|
|[next](../standard-library/iterator-functions.md#next)|Dokonuje iteracji określoną liczbę razy i zwraca nową pozycję iteratora.|
|[Poprzedni](../standard-library/iterator-functions.md#prev)|Dokonuje iteracji odwrotnej określoną liczbę razy i zwraca nową pozycję iteratora.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](../standard-library/iterator-operators.md#op_neq)|Testuje, czy obiekt iteratora po lewej stronie operatora nie jest równy obiektowi iteratora po prawej stronie.|
|[operator==](../standard-library/iterator-operators.md#op_eq_eq)|Testuje, czy obiekt iteratora po lewej stronie operatora jest równy obiektowi iteratora po prawej stronie.|
|[Operator <](../standard-library/iterator-operators.md#op_lt)|Testuje, czy obiekt iteratora po lewej stronie operatora jest mniejszy niż obiekt iteratora po prawej stronie.|
|[Operator\<=](../standard-library/iterator-operators.md#op_gt_eq)|Testuje, czy obiekt iteratora po lewej stronie operatora jest mniejszy niż lub równy obiektowi iteratora po prawej stronie.|
|[operator>](../standard-library/iterator-operators.md#op_gt)|Testuje, czy obiekt iteratora po lewej stronie operatora jest większy niż obiekt iteratora po prawej stronie.|
|[operator>=](../standard-library/iterator-operators.md#op_gt_eq)|Testuje, czy obiekt iteratora po lewej stronie operatora jest większy niż lub równy obiektowi iteratora po prawej stronie.|
|[operator +](../standard-library/iterator-operators.md#op_add)|Dodaje przesunięcia do iteratora i zwraca nowy `reverse_iterator` adresowania wstawiony element w nowe położenie przesunięcia.|
|[operator-](../standard-library/iterator-operators.md#operator-)|Odejmuje jeden iterator od innego i zwraca różnicę.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[back_insert_iterator](../standard-library/back-insert-iterator-class.md)|Klasa szablonu opisuje obiekt iteratora wyjściowego. Wstawia elementy do kontenera typu **kontenera**, który uzyskuje dostęp do za pośrednictwem chronionej **wskaźnika** przechowuje obiekt o nazwie kontenera.|
|[bidirectional_iterator_tag —](../standard-library/bidirectional-iterator-tag-struct.md)|Klasa, która zawiera typ zwracany dla **iterator_category** funkcja, która reprezentuje iteratora dwukierunkowego.|
|[checked_array_iterator](../standard-library/checked-array-iterator-class.md)|Klasa, która uzyskuje dostęp do tablicy przy użyciu sprawdzonego iteratora dostępu swobodnego. **Uwaga:** ta klasa jest rozszerzeniem Microsoft standardowej biblioteki C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft.|
|[forward_iterator_tag —](../standard-library/forward-iterator-tag-struct.md)|Klasa, która zawiera typ zwracany dla **iterator_category** funkcja, która reprezentuje iteratora do przodu.|
|[front_insert_iterator](../standard-library/front-insert-iterator-class.md)|Klasa szablonu opisuje obiekt iteratora wyjściowego. Wstawia elementy do kontenera typu **kontenera**, który uzyskuje dostęp do za pośrednictwem chronionej **wskaźnika** przechowuje obiekt o nazwie kontenera.|
|[input_iterator_tag](../standard-library/input-iterator-tag-struct.md)|Klasa, która zawiera typ zwracany dla **iterator_category** funkcja, która reprezentuje wejściowych iteratora.|
|[insert_iterator](../standard-library/insert-iterator-class.md)|Klasa szablonu opisuje obiekt iteratora wyjściowego. Wstawia elementy do kontenera typu **kontenera**, który uzyskuje dostęp do za pośrednictwem chronionej **wskaźnika** przechowuje obiekt o nazwie kontenera. Przechowuje także chronionej **iterator** obiekt klasy **Container::iterator**o nazwie **iter**.|
|[istream_iterator](../standard-library/istream-iterator-class.md)|Klasa szablonu opisuje obiekt iteratora wejściowego. Wyodrębnia on obiektów klasy **Ty** ze strumienia wejściowego, który uzyskuje dostęp do za pośrednictwem przechowuje, typ wskaźnika do obiektu `basic_istream` \< **elementu**, **Tr**>.|
|[istreambuf_iterator](../standard-library/istreambuf-iterator-class.md)|Klasa szablonu opisuje obiekt iteratora wejściowego. Wstawia elementy klasy **elementu** w buforze strumienia wyjściowego, które it uzyskuje dostęp do za pośrednictwem obiektu go magazyny typu **wskaźnika** do `basic_streambuf` \< **elementu**, **Tr**>.|
|[iterator](../standard-library/iterator-struct.md)|Klasa szablonu jest używana jako typ podstawowy dla wszystkich iteratorów.|
|[iterator_traits](../standard-library/iterator-traits-struct.md)|Klasa pomocnika szablonu udostępnia typy krytyczne, które są skojarzone z innymi typami iteratora, tak że można się do nich odwoływać w taki sam sposób.|
|[move_iterator](../standard-library/move-iterator-class.md)|A `move_iterator` obiekt przechowuje iteratora dostępie swobodnym typu `RandomIterator`. Zachowuje się jak iterator dostępu swobodnego, z wyjątkiem przypadków wyłuskania. Wynik `operator*` niejawnie jest rzutowane na `value_type&&:` dokonanie `rvalue reference`.|
|[ostream_iterator](../standard-library/ostream-iterator-class.md)|Klasa szablonu opisuje obiekt iteratora wyjściowego. Wstawia obiektów klasy **typu** do strumienia wyjściowego, które it uzyskuje dostęp do za pośrednictwem obiektu go magazyny typu **wskaźnika** do `basic_ostream` \< **elementu** , **Tr**>.|
|[ostreambuf_iterator, klasa](../standard-library/ostreambuf-iterator-class.md)|Klasa szablonu opisuje obiekt iteratora wyjściowego. Wstawia elementy klasy **elementu** do buforu strumienia wyjściowego, który uzyskuje dostęp do za pośrednictwem przechowuje, typ wskaźnika do obiektu `basic_streambuf` \< **elementu**, **Tr**>.|
|[output_iterator_tag](../standard-library/output-iterator-tag-struct.md)|Klasa, która zawiera typ zwracany dla **iterator_category** funkcja, która reprezentuje iteratora danych wyjściowych.|
|[random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)|Klasa, która zawiera typ zwracany dla **iterator_category** funkcja, która reprezentuje iteratora dostępie swobodnym.|
|[reverse_iterator](../standard-library/reverse-iterator-class.md)|Klasa szablonu opisuje obiekt, który zachowuje się jak iterator dostępu swobodnego, tylko w odwrotnej kolejności.|
|[unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)|Klasa, która uzyskuje dostęp do tablicy przy użyciu niesprawdzonego iteratora dostępu swobodnego. **Uwaga:** ta klasa jest rozszerzeniem Microsoft standardowej biblioteki C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
