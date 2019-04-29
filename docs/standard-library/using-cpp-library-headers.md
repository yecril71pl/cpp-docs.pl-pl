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
ms.openlocfilehash: b9841d1045a6d2d1126414f1ce4cfc93f9667eef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362373"
---
# <a name="using-c-library-headers"></a>Korzystanie z nagłówków biblioteki C++

Obejmują zawartość standardowy nagłówek nadawania jej nazwy w dyrektywie include.

```cpp
#include <iostream>// include I/O facilities
```

Może zawierać standardowych nagłówków w dowolnej kolejności, standardowy nagłówek więcej niż jeden raz lub dwa lub więcej standardowych nagłówków, które definiują ten sam makro lub tego samego typu. Nie dołączaj standardowy nagłówek w deklaracji. Definiuje makra, które mają takie same nazwy słowa kluczowe przed wprowadzeniem standardowy nagłówek.

Nagłówków biblioteki C++ obejmuje wszystkie inne nagłówków biblioteki C++ musi definiować typy wymaganych domen. (Zawsze obejmuje jawnie żadnych nagłówków biblioteki C++, które są potrzebne w jednostce translacji, jednak co najmniej przypuszczalnie problem o jego rzeczywista zależności). Nagłówek standardowej C nigdy nie zawiera inny standardowy nagłówek. Standardowy nagłówek deklaruje i definiuje tylko jednostek, które są opisane dla niego w tym dokumencie.

Każda funkcja w bibliotece jest zadeklarowany w standardowy nagłówek. W odróżnieniu od w standardowej C standardowy nagłówek nigdy nie zapewnia maskowania makra o takiej samej nazwie jak funkcja maskuje deklaracji funkcji, która osiąga ten sam efekt. Aby uzyskać więcej informacji na temat maskowania makr, zobacz [konwencje biblioteki C++](../standard-library/cpp-library-conventions.md).

Nazwy wszystkich innych niż **operatora delete** i **nowy operator** w bibliotece C++ nagłówki są zdefiniowane w `std` przestrzeni nazw, lub w przestrzeni nazw zagnieżdżone w obrębie `std` przestrzeni nazw. Możesz odwołać się do nazwy `cin`, na przykład jako `std::cin`. Należy jednak pamiętać, że nazwy makr nie podlegają kwalifikacji przestrzeni nazw, więc zawsze pisać `__STD_COMPLEX` bez kwalifikatora przestrzeni nazw.

W niektórych środowiskach tłumaczenia, łącznie z nagłówków biblioteki C++ może przenieść nazw zewnętrznych zadeklarowanych w `std` przestrzeni nazw w globalnej przestrzeni nazw, z poszczególnymi **przy użyciu** deklaracje dla każdej z nazw. W przeciwnym razie jest nagłówek *nie* wprowadzać żadnych nazw bibliotek w bieżącej przestrzeni nazw.

C++ Standard wymaga, że nagłówki C Standard zadeklarować wszystkich nazw zewnętrznych w przestrzeni nazw `std`, następnie przenieść je do globalnej przestrzeni nazw z poszczególnymi **przy użyciu** deklaracje dla każdej z nazw. Jednak w niektórych środowiskach tłumaczenia przez Standard C nagłówki obejmują nie deklaracji przestrzeni nazw, deklarowanie wszystkich nazw bezpośrednio w globalnej przestrzeni nazw. W związku z tym większość przenośnych metody radzenia sobie z przestrzeni nazw jest wykonanie czynności opisanych dwie reguły:

- Aby assuredly zadeklarować w przestrzeni nazw `std` zewnętrzną nazwę, która zazwyczaj jest zadeklarowana w \<stdlib.h >, na przykład zawierać nagłówek \<cstdlib — >. Wiadomo, że nazwy mogą być deklarowane w globalnej przestrzeni nazw.

- Do deklarowania assuredly w globalnej przestrzeni nazw zewnętrzną nazwę zadeklarowanych w \<stdlib.h >, dołączyć nagłówek \<stdlib.h > bezpośrednio. Dowiedzieć się, że nazwy mogą być deklarowane w przestrzeni nazw `std`.

W związku z tym jeśli chcesz wywołać `std::abort` spowodować Nienormalne zakończenie, należy uwzględnić \<cstdlib — >. Jeśli chcesz wywołać `abort`, powinien zawierać \<stdlib.h >.

Alternatywnie można napisać deklaracji:

```cpp
using namespace std;
```

wszystkie nazwy biblioteki która wnosi do bieżącej przestrzeni nazw. Jeśli piszesz tej deklaracji natychmiast po wszystkich zawiera dyrektywy, przenieść nazwy do globalnej przestrzeni nazw. Zagadnienia dotyczące przestrzeni nazw w pozostałej części jednostki translacji, później możesz zignorować. Można także uniknąć większość różnic w środowiskach różnych tłumaczeń.

Jeśli nie postanowiono inaczej, nie mogą definiować nazwy w `std` przestrzeni nazw, lub w przestrzeni nazw zagnieżdżone w obrębie `std` przestrzeni nazw, w ramach programu.

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
