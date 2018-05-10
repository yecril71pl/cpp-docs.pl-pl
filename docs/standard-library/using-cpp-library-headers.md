---
title: Korzystanie z nagłówków biblioteki C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- headers, naming in C++ include directive
- standard header in C++
- headers
- INCLUDE directive
- headers, C++ Standard Library
- library headers
- C++ Standard Library, headers
ms.assetid: a36e889e-1af2-4cd9-a211-bfc7a3fd8e85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30d31f30971184356374b3991fedda474ca27465
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="using-c-library-headers"></a>Korzystanie z nagłówków biblioteki C++

Dołącz zawartość standardowy nagłówek nazw w dyrektywy include.

```cpp
#include <iostream>// include I/O facilities
```

Możesz dołączać standardowych nagłówków w dowolnej kolejności, standardowy nagłówek więcej niż raz lub dwa lub więcej standardowych nagłówków definiujących makra tej samej lub tego samego typu. Nie dołączaj standardowy nagłówek w deklaracji. Nie definiują makra, które mają takie same nazwy jako słowa kluczowe przed wprowadzeniem standardowy nagłówek.

Nagłówków biblioteki C++ obejmuje wszystkie inne nagłówków biblioteki C++ musi definiować wymagane typy domen. (Zawsze obejmuje jawnie żadnych nagłówków biblioteki C++, które są potrzebne w jednostce tłumaczenia, ale co najmniej przypuszczalnie problem o jego rzeczywistego zależności). Nagłówek standardowy C nigdy nie zawiera inny standardowy nagłówek. Standardowy nagłówek deklaruje lub określa jednostki, w tym dokumencie opisano dla niego.

Każda funkcja w bibliotece jest zadeklarowana w standardowy nagłówek. W odróżnieniu od w standardowe C standardowy nagłówek nigdy nie podano maskowania makro z taką samą nazwę jak funkcja, która maski deklaracji funkcji i osiąga ten sam efekt. Aby uzyskać więcej informacji na maskowania makra, zobacz [konwencje biblioteki C++](../standard-library/cpp-library-conventions.md).

Nazwy wszystkich innych niż `operator delete` i `operator new` w bibliotece C++ nagłówki są zdefiniowane w `std` przestrzeni nazw lub w przestrzeni nazw zagnieżdżone w obrębie `std` przestrzeni nazw. Możesz odwoływać się do nazwy `cin`, na przykład jako `std::cin`. Należy jednak pamiętać, że nazwy makr nie podlegają kwalifikacji przestrzeni nazw, więc zawsze pisać `__STD_COMPLEX` bez kwalifikatora przestrzeni nazw.

W niektórych środowiskach tłumaczenia, łącznie z nagłówków biblioteki C++ może Wózek nośny nazw zewnętrznych zadeklarowany w `std` przestrzeni nazw w globalnej przestrzeni nazw jak również z poszczególnymi `using` deklaracje dla każdej nazwy. W przeciwnym razie wartość nagłówka jest *nie* wprowadzenia nazwy biblioteki do bieżącej przestrzeni nazw.

C++ Standard wymaga, aby C standardowych nagłówków zadeklarować wszystkie nazwy zewnętrzne w przestrzeni nazw `std`, następnie Wózek nośny ich do globalnej przestrzeni nazw z poszczególnymi `using` deklaracje dla każdej nazwy. Ale w niektórych środowiskach tłumaczenia C Standard nagłówki obejmują nie deklaracje przestrzeni nazw, deklarowanie wszystkie nazwy bezpośrednio w globalnej przestrzeni nazw. W związku z tym większość przenośnych metody radzenia sobie z przestrzeni nazw ma dwie reguły:

- Aby assuredly zadeklarować w przestrzeni nazw `std` zewnętrzną nazwę tradycyjnie jest zadeklarowana w \<stdlib.h >, na przykład, Dołącz nagłówek \<cstdlib — >. Wiadomo, że nazwa może być również zadeklarowany w globalnej przestrzeni nazw.

- Aby zadeklarować assuredly w globalnej przestrzeni nazw zewnętrzna nazwa zadeklarowana w \<stdlib.h >, Dołącz nagłówek \<stdlib.h > bezpośrednio. Wiedzieć, że nazwa może być również zadeklarowany w przestrzeni nazw `std`.

W związku z tym jeśli chcesz wywołać `std::abort` spowodują przerwania pracy, należy uwzględnić \<cstdlib — >. Jeśli chcesz wywołać `abort`, należy uwzględnić \<stdlib.h >.

Alternatywnie można zapisać deklaracji:

```cpp
using namespace std;
```

które powoduje przeniesienie wszystkich nazw biblioteki do bieżącej przestrzeni nazw. Jeśli piszesz tej deklaracji natychmiast po wszystkich zawiera dyrektywy, które, Wózek nośny nazwy w globalnej przestrzeni nazw. Zagadnienia dotyczące przestrzeni nazw w pozostałej jednostce tłumaczenia, później możesz zignorować. Można również uniknąć większości różnice tłumaczenia różnych środowiskach.

Chyba że w szczególności, nie mogą określić nazwy w `std` przestrzeni nazw lub w przestrzeni nazw zagnieżdżone w obrębie `std` przestrzeni nazw w programie.

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
