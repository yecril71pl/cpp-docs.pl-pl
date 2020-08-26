---
title: '&lt;Iterator&gt;'
ms.date: 11/04/2016
f1_keywords:
- <iterator>
- iterator/std::<iterator>
helpviewer_keywords:
- iterator header
ms.assetid: c61a3962-f3ed-411a-b5a3-e8b3c2b500bd
ms.openlocfilehash: 08e2051db70ee1891c7b60860c7ea0b423855be5
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841925"
---
# <a name="ltiteratorgt"></a>&lt;Iterator&gt;

Definiuje iteratory pierwotne, iteratory wstępnie zdefiniowane i iteratory strumienia, a także kilka szablonów pomocniczych. Wstępnie zdefiniowane iteratory obejmują adaptery wstawiania i odwracania. Istnieją trzy klasy adapterów iteratorów wstawiania: na przód, na tył i ogólne. Zapewniają one semantykę wstawiania zamiast semantyki zastępowania, którą dostarczają iteratory elementów członkowskich.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<iterator>

**Przestrzeń nazw:** std

## <a name="remarks"></a>Uwagi

Iteratory są uogólnieniem wskaźników, abstrahując od ich wymagań w sposób, który pozwala programowi C++ na pracę z różnymi strukturami danych w jednolity sposób. Iteratory pełnią rolę pośredników pomiędzy kontenerami i algorytmami ogólnymi. Zamiast pracy na poszczególnych typach danych, algorytmy są zdefiniowane do pracy w zakresie określonym przez typ iteratora. Każda struktura danych, która spełnia wymagania iteratora, może być eksploatowana przez algorytm. Istnieje pięć typów lub kategorii iteratora, z których każda ma własne wymagania i funkcje wynikowe:

- Wyjście: przenoszenie do przodu, może przechowywać wartości, ale nie je pobierać, dostarczone przez ostream i inserter.

- Wejście: przenoszenie do przodu, może pobierać wartości, ale nie je przechowywać, dostarczone przez istream.

- Do przodu: przenoszenie do przodu może przechowywać i pobierać wartości.

- Dwukierunkowe: przenoszenie do przodu i do tyłu, może przechowywać i pobierać wartości dostarczone przez listy, zestawy, zestawy wielokrotne, mapy i mapy wielokrotne.

- Dostęp swobodny: elementy dostępne w dowolnej kolejności, może przechowywać i pobierać wartości, dostarczone przez vector, deque, string i array.

Iteratory, które mają większe wymagania i bardziej wydajny dostęp do elementów, mogą być używane zamiast iteratorów z mniejszymi wymaganiami. Na przykład, jeżeli iterator do przodu zostanie wywołany, wówczas można zamiast niego użyć iteratora swobodnego dostępu.

Visual Studio dodaje rozszerzenia do iteratorów standardowej biblioteki C++, w celu uwzględnienia różnych sytuacji trybu debugowania dla iteratorów sprawdzonych i niesprawdzonych. Aby uzyskać więcej informacji, zobacz [bezpieczne biblioteki: standardowa biblioteka języka C++](../standard-library/safe-libraries-cpp-standard-library.md).

## <a name="members"></a>Elementy członkowskie

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|-|
|[chodzenie](../standard-library/iterator-functions.md#advance)|Inkrementuje iterator o określoną liczbę pozycji.|
|[back_inserter](../standard-library/iterator-functions.md#back_inserter)|Tworzy iterator, który może wstawiać elementy z tyłu określonego kontenera.|
|[zaczną](../standard-library/iterator-functions.md#begin)|Pobiera iterator do pierwszego elementu w określonym kontenerze.|
|[cbegin](../standard-library/iterator-functions.md#cbegin)|Pobiera stały iterator do pierwszego elementu w określonym kontenerze.|
|[cend](../standard-library/iterator-functions.md#cend)|Pobiera stały iterator do elementu, który następuje po ostatnim elemencie w określonym kontenerze.|
|[crbegin —](../standard-library/iterator-functions.md#crbegin)||
|[crend](../standard-library/iterator-functions.md#crend)||
|[data](../standard-library/iterator-functions.md#data)||
|[miast](../standard-library/iterator-functions.md#distance)|Określa liczbę przyrostów między położeniami, do których odnoszą się dwa iteratory.|
|[punktów](../standard-library/iterator-functions.md#end)|Pobiera iterator do elementu, który następuje po ostatnim elemencie w określonym kontenerze.|
|[puste](../standard-library/iterator-functions.md#empty)||
|[front_inserter](../standard-library/iterator-functions.md#front_inserter)|Tworzy iterator, która może wstawiać elementy z przodu określonego kontenera.|
|[Inserter](../standard-library/iterator-functions.md#inserter)|Adapter iteratora, który dodaje nowy element do kontenera w określonym punkcie wstawiania.|
|[make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator)|Tworzy [checked_array_iterator](../standard-library/checked-array-iterator-class.md) , które mogą być używane przez inne algorytmy. **Uwaga:**  Ta funkcja jest rozszerzeniem firmy Microsoft biblioteki standardowej języka C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft.|
|[make_move_iterator](../standard-library/iterator-functions.md#make_move_iterator)|Zwraca iterator przenoszenia, zawierający podany iterator taki, jak jego przechowywany iterator podstawowy.|
|[make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator)|Tworzy [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md) , które mogą być używane przez inne algorytmy. **Uwaga:**  Ta funkcja jest rozszerzeniem firmy Microsoft biblioteki standardowej języka C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft.|
|[ponown](../standard-library/iterator-functions.md#next)|Dokonuje iteracji określoną liczbę razy i zwraca nową pozycję iteratora.|
|[przeglądan](../standard-library/iterator-functions.md#prev)|Dokonuje iteracji odwrotnej określoną liczbę razy i zwraca nową pozycję iteratora.|
|[rbegin](../standard-library/iterator-functions.md#rbegin)||
|[rend](../standard-library/iterator-functions.md#rend)||
|[zmienia](../standard-library/iterator-functions.md#size)||

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[operator! =](../standard-library/iterator-operators.md#op_neq)|Testuje, czy obiekt iteratora po lewej stronie operatora nie jest równy obiektowi iteratora po prawej stronie.|
|[operator = =](../standard-library/iterator-operators.md#op_eq_eq)|Testuje, czy obiekt iteratora po lewej stronie operatora jest równy obiektowi iteratora po prawej stronie.|
|[<operatora ](../standard-library/iterator-operators.md#op_lt)|Testuje, czy obiekt iteratora po lewej stronie operatora jest mniejszy niż obiekt iteratora po prawej stronie.|
|[zakład\<=](../standard-library/iterator-operators.md#op_gt_eq)|Testuje, czy obiekt iteratora po lewej stronie operatora jest mniejszy niż lub równy obiektowi iteratora po prawej stronie.|
|[>operatora ](../standard-library/iterator-operators.md#op_gt)|Testuje, czy obiekt iteratora po lewej stronie operatora jest większy niż obiekt iteratora po prawej stronie.|
|[>operatora =](../standard-library/iterator-operators.md#op_gt_eq)|Testuje, czy obiekt iteratora po lewej stronie operatora jest większy niż lub równy obiektowi iteratora po prawej stronie.|
|[operator +](../standard-library/iterator-operators.md#op_add)|Dodaje przesunięcie do iteratora i zwraca nowy odnoszący `reverse_iterator` się do wstawionego elementu w nowym położeniu przesunięcia.|
|[zakład](../standard-library/iterator-operators.md#operator-)|Odejmuje jeden iterator od innego i zwraca różnicę.|

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|-|-|
|[back_insert_iterator](../standard-library/back-insert-iterator-class.md)|Szablon klasy zawiera opis obiektu iteratora danych wyjściowych. Wstawia elementy do kontenera typu `Container` , do którego uzyskuje dostęp za pomocą chronionego `pointer` obiektu, który przechowuje nazwę kontenera.|
|[bidirectional_iterator_tag](../standard-library/bidirectional-iterator-tag-struct.md)|Klasa udostępniająca typ zwracany dla `iterator_category` funkcji, która reprezentuje iterator dwukierunkowy.|
|[checked_array_iterator](../standard-library/checked-array-iterator-class.md)|Klasa, która uzyskuje dostęp do tablicy przy użyciu sprawdzonego iteratora dostępu swobodnego. **Uwaga:**  Ta klasa jest rozszerzeniem firmy Microsoft biblioteki standardowej języka C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft.|
|[forward_iterator_tag](../standard-library/forward-iterator-tag-struct.md)|Klasa udostępniająca typ zwracany dla `iterator_category` funkcji, która reprezentuje iterator do przodu.|
|[front_insert_iterator](../standard-library/front-insert-iterator-class.md)|Szablon klasy zawiera opis obiektu iteratora danych wyjściowych. Wstawia elementy do kontenera typu `Container` , do którego uzyskuje dostęp za pomocą chronionego `pointer` obiektu, który przechowuje nazwę kontenera.|
|[input_iterator_tag](../standard-library/input-iterator-tag-struct.md)|Klasa, która dostarcza typ zwracany dla `iterator_category` funkcji, która reprezentuje iterator wejściowy.|
|[insert_iterator](../standard-library/insert-iterator-class.md)|Szablon klasy zawiera opis obiektu iteratora danych wyjściowych. Wstawia elementy do kontenera typu `Container` , do którego uzyskuje dostęp za pomocą chronionego `pointer` obiektu, który przechowuje nazwę kontenera. Przechowuje również `iterator` obiekt chroniony klasy `Container::iterator` , o nazwie `iter` .|
|[istream_iterator](../standard-library/istream-iterator-class.md)|Szablon klasy opisuje obiekt iteratora wejściowego. Wyodrębnia obiekty klasy `Ty` ze strumienia wejściowego, do którego uzyskuje dostęp przez obiekt, który przechowuje, typu wskaźnika do `basic_istream` \<**Elem**, **Tr**> .|
|[istreambuf_iterator](../standard-library/istreambuf-iterator-class.md)|Szablon klasy opisuje obiekt iteratora wejściowego. Wstawia elementy klasy `Elem` do buforu strumienia wyjściowego, do którego uzyskuje dostęp przez obiekt, który przechowuje, typu `pointer` do `basic_streambuf` \<**Elem**, **Tr**> .|
|[Iterator](../standard-library/iterator-struct.md)|Szablon klasy jest używany jako typ podstawowy dla wszystkich iteratorów.|
|[iterator_traits](../standard-library/iterator-traits-struct.md)|Klasa pomocnika szablonu udostępnia typy krytyczne, które są skojarzone z innymi typami iteratora, tak że można się do nich odwoływać w taki sam sposób.|
|[move_iterator](../standard-library/move-iterator-class.md)|`move_iterator`Obiekt przechowuje Iterator dostępu swobodnego typu `RandomIterator` . Zachowuje się jak iterator dostępu swobodnego, z wyjątkiem przypadków wyłuskania. Wynik `operator*` jest niejawnie rzutowany na, `value_type&&:` Aby utworzyć `rvalue reference` .|
|[ostream_iterator](../standard-library/ostream-iterator-class.md)|Szablon klasy zawiera opis obiektu iteratora danych wyjściowych. Wstawia obiekty klasy `Type` do strumienia wyjściowego, do którego uzyskuje dostęp przez obiekt, który przechowuje, typu `pointer` do `basic_ostream` \<**Elem**, **Tr**> .|
|[Klasa ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md)|Szablon klasy zawiera opis obiektu iteratora danych wyjściowych. Wstawia elementy klasy `Elem` do buforu strumienia wyjściowego, do którego uzyskuje dostęp przez obiekt, który przechowuje, typu wskaźnika do `basic_streambuf` \<**Elem**, **Tr**> .|
|[output_iterator_tag](../standard-library/output-iterator-tag-struct.md)|Klasa udostępniająca typ zwracany dla `iterator_category` funkcji, która reprezentuje iterator wyjściowy.|
|[random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)|Klasa udostępniająca typ zwracany dla `iterator_category` funkcji, która reprezentuje Iterator dostępu swobodnego.|
|[reverse_iterator](../standard-library/reverse-iterator-class.md)|Szablon klasy opisuje obiekt, który zachowuje się jak Iterator dostępu swobodnego, tylko w odwrotnej postaci.|
|[unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)|Klasa, która uzyskuje dostęp do tablicy przy użyciu niesprawdzonego iteratora dostępu swobodnego. **Uwaga:**  Ta klasa jest rozszerzeniem firmy Microsoft biblioteki standardowej języka C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft.|

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
