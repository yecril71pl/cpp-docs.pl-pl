---
title: Korzystanie z nagłówków biblioteki C++
ms.date: 11/04/2016
helpviewer_keywords:
- headers, naming in C++ include directive
- standard header in C++
- headers
- INCLUDE directive
- headers, C++ Standard Library
- library headers
- C++ Standard Library, headers
ms.assetid: a36e889e-1af2-4cd9-a211-bfc7a3fd8e85
ms.openlocfilehash: 9cc0bb51b159f6668adad05ebd2d386364ae2f81
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450061"
---
# <a name="using-c-library-headers"></a>Korzystanie z nagłówków biblioteki C++

Zawartość standardowego nagłówka jest uwzględniana przez nadanie jej nazwy w dyrektywie include.

```cpp
#include <iostream>// include I/O facilities
```

Można uwzględnić standardowe nagłówki w dowolnej kolejności, w standardowym nagłówku więcej niż jeden raz lub dwa lub więcej nagłówków standardowych, które definiują to samo makro lub ten sam typ. Nie dołączaj standardowego nagłówka w deklaracji. Nie należy definiować makr, które mają takie same nazwy jak słowa kluczowe, zanim dołączysz standardowy nagłówek.

Nagłówek C++ biblioteki zawiera wszystkie inne C++ nagłówki biblioteki, które muszą definiować wymagane typy. (Zawsze dołączaj C++ jawnie wszystkie nagłówki biblioteki potrzebne w jednostce translacji, jednak Lest nie powiodła się z rzeczywistymi zależnościami). Standardowy nagłówek C nigdy nie zawiera innego nagłówka standardowego. Nagłówek standardowy deklaruje lub definiuje tylko te jednostki, które zostały opisane w tym dokumencie.

Każda funkcja w bibliotece jest zadeklarowana w standardowym nagłówku. W przeciwieństwie do standardowego języka C, standardowy nagłówek nigdy nie udostępnia makro maskujące o takiej samej nazwie jak funkcja, która maskuje deklarację funkcji i osiąga ten sam efekt. Aby uzyskać więcej informacji na temat maskowania makr, zobacz [ C++ konwencje biblioteki](../standard-library/cpp-library-conventions.md).

Wszystkie nazwy inne niż **operator delete** i **operator new** w C++ `std` nagłówkach biblioteki są zdefiniowane w przestrzeni nazw lub w przestrzeni nazw zagnieżdżonej `std` w przestrzeni nazw. Odwołujesz się do `cin`nazwy, na przykład, `std::cin`jako. Należy jednak pamiętać, że nazwy makr nie podlegają kwalifikacji przestrzeni nazw, więc zawsze należy pisać `__STD_COMPLEX` bez kwalifikatora przestrzeni nazw.

W niektórych środowiskach tłumaczenia, łącznie z C++ nagłówkiem biblioteki, można również podstawiać `std` nazwy zewnętrzne zadeklarowane w przestrzeni nazw do globalnej przestrzeni nazw, przy **użyciu** poszczególnych nazw. W przeciwnym razie nagłówek nie *wprowadza żadnych* nazw bibliotek do bieżącej przestrzeni nazw.

C++ Standard wymaga, aby nagłówki w standardzie C deklarują wszystkie nazwy zewnętrzne `std`w przestrzeni nazw, a następnie podstawiać je do globalnej przestrzeni nazw z **użyciem** deklaracji poszczególnych nazw. Ale w niektórych środowiskach tłumaczenia standardowe nagłówki C nie obejmują deklaracji przestrzeni nazw, deklarując wszystkie nazwy bezpośrednio w globalnej przestrzeni nazw. Z tego względu najbardziej przenośnym sposobem postępowania z przestrzeniami nazw jest przestrzeganie dwóch reguł:

- Aby zapewnić zagwarantowanie w `std` przestrzeni nazw zewnętrznej nazwy, która jest tradycyjnie zadeklarowana w \<STDLIB. h >, na przykład \<, Uwzględnij nagłówek cstdlib >. Należy pamiętać, że nazwa może być również zadeklarowana w globalnej przestrzeni nazw.

- Aby w sposób gwarantowany zadeklarować w globalnej przestrzeni nazw nazwę zewnętrzną zadeklarowaną w \<STDLIB. h >, należy bezpośrednio dodać nagłówek \<STDLIB. > h. Należy pamiętać, że nazwa może być również zadeklarowana `std`w przestrzeni nazw.

W ten sposób, jeśli chcesz wywołać `std::abort` , aby spowodować nietypowe zakończenie, należy \<uwzględnić cstdlib >. Jeśli chcesz wywołać `abort`, należy dołączyć \<STDLIB. h >.

Alternatywnie można napisać deklarację:

```cpp
using namespace std;
```

powoduje to przeniesienie wszystkich nazw bibliotek do bieżącej przestrzeni nazw. Jeśli napiszesz tę deklarację bezpośrednio po wszystkich dyrektywach include, nastąpi przełączenie nazw do globalnej przestrzeni nazw. Następnie można zignorować uwagi dotyczące przestrzeni nazw w pozostałej części jednostki translacji. Należy również unikać większości różnic w różnych środowiskach tłumaczenia.

O ile nie wskazano inaczej, nie można definiować nazw w `std` przestrzeni nazw lub w przestrzeni nazw zagnieżdżonej `std` w przestrzeni nazw w ramach programu.

## <a name="see-also"></a>Zobacz także

[C++Omówienie biblioteki standardowej](../standard-library/cpp-standard-library-overview.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
