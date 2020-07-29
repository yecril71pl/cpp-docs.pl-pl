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
ms.openlocfilehash: a73ebebb4fdde5dd72f148390d004c32b9f4dff7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215481"
---
# <a name="using-c-library-headers"></a>Korzystanie z nagłówków biblioteki C++

Zawartość standardowego nagłówka jest uwzględniana przez nadanie jej nazwy w dyrektywie include.

```cpp
#include <iostream>// include I/O facilities
```

Można uwzględnić standardowe nagłówki w dowolnej kolejności, w standardowym nagłówku więcej niż jeden raz lub dwa lub więcej nagłówków standardowych, które definiują to samo makro lub ten sam typ. Nie dołączaj standardowego nagłówka w deklaracji. Nie należy definiować makr, które mają takie same nazwy jak słowa kluczowe, zanim dołączysz standardowy nagłówek.

Nagłówek biblioteki C++ zawiera wszystkie inne nagłówki biblioteki C++, które muszą definiować wymagane typy. (Zawsze dołączaj jawnie wszystkie nagłówki biblioteki C++ potrzebne w jednostce translacji, jednak Lest nie powiodła się z rzeczywistymi zależnościami). Standardowy nagłówek C nigdy nie zawiera innego nagłówka standardowego. Nagłówek standardowy deklaruje lub definiuje tylko te jednostki, które zostały opisane w tym dokumencie.

Każda funkcja w bibliotece jest zadeklarowana w standardowym nagłówku. W przeciwieństwie do standardowego języka C, standardowy nagłówek nigdy nie udostępnia makro maskujące o takiej samej nazwie jak funkcja, która maskuje deklarację funkcji i osiąga ten sam efekt. Aby uzyskać więcej informacji na temat maskowania makr, zobacz [konwencje biblioteki C++](../standard-library/cpp-library-conventions.md).

Wszystkie nazwy inne niż **operator delete** i **operator new** w nagłówkach biblioteki C++ są zdefiniowane w `std` przestrzeni nazw lub w przestrzeni nazw zagnieżdżonej w `std` przestrzeni nazw. Odwołujesz się do nazwy `cin` , na przykład, jako `std::cin` . Należy jednak pamiętać, że nazwy makr nie podlegają kwalifikacji przestrzeni nazw, więc zawsze należy pisać `__STD_COMPLEX` bez kwalifikatora przestrzeni nazw.

W niektórych środowiskach tłumaczenia, łącznie z nagłówkiem biblioteki C++, można również podstawiać zewnętrzne nazwy zadeklarowane w `std` przestrzeni nazw do globalnej przestrzeni nazw, z uwzględnieniem poszczególnych **`using`** nazw. W przeciwnym razie nagłówek nie *wprowadza żadnych* nazw bibliotek do bieżącej przestrzeni nazw.

Standard C++ wymaga, aby nagłówki standardowe C deklarują wszystkie nazwy zewnętrzne w przestrzeni nazw `std` , a następnie podstawiać je do globalnej przestrzeni nazw przy użyciu poszczególnych **`using`** deklaracji dla każdej nazwy. Ale w niektórych środowiskach tłumaczenia standardowe nagłówki C nie obejmują deklaracji przestrzeni nazw, deklarując wszystkie nazwy bezpośrednio w globalnej przestrzeni nazw. Z tego względu najbardziej przenośnym sposobem postępowania z przestrzeniami nazw jest przestrzeganie dwóch reguł:

- Aby zapewnić zadeklarować w przestrzeni nazw `std` zewnętrzną nazwę, która jest tradycyjnie zadeklarowana w \<stdlib.h> , na przykład, Dołącz nagłówek \<cstdlib> . Należy pamiętać, że nazwa może być również zadeklarowana w globalnej przestrzeni nazw.

- Aby zapewnić zadeklarować w globalnej przestrzeni nazw nazwę zewnętrzną zadeklarowaną w \<stdlib.h> , Dołącz nagłówek \<stdlib.h> bezpośrednio. Należy pamiętać, że nazwa może być również zadeklarowana w przestrzeni nazw `std` .

W ten sposób, jeśli chcesz wywołać `std::abort` , aby spowodować nietypowe zakończenie, należy uwzględnić \<cstdlib> . Jeśli chcesz wywołać `abort` , należy uwzględnić \<stdlib.h> .

Alternatywnie można napisać deklarację:

```cpp
using namespace std;
```

powoduje to przeniesienie wszystkich nazw bibliotek do bieżącej przestrzeni nazw. Jeśli napiszesz tę deklarację bezpośrednio po wszystkich dyrektywach include, nastąpi przełączenie nazw do globalnej przestrzeni nazw. Następnie można zignorować uwagi dotyczące przestrzeni nazw w pozostałej części jednostki translacji. Należy również unikać większości różnic w różnych środowiskach tłumaczenia.

O ile nie wskazano inaczej, nie można definiować nazw w `std` przestrzeni nazw lub w przestrzeni nazw zagnieżdżonej w `std` przestrzeni nazw w ramach programu.

## <a name="see-also"></a>Zobacz także

[Omówienie standardowej biblioteki języka C++](../standard-library/cpp-standard-library-overview.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
