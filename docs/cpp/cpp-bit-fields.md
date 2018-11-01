---
title: Pola bitowe języka C++
ms.date: 11/04/2016
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
ms.openlocfilehash: df4e5a068f76c35dc22b3915ad7e4ace421ca10b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644975"
---
# <a name="c-bit-fields"></a>Pola bitowe języka C++

Klasy i struktury mogą zawierać elementy członkowskie, które zajmują mniej miejsca niż typ całkowity. Te elementy członkowskie są określane jako pola bitowe. Składnia służąca do pola bitowego *deklarator składowej* specyfikacji w następujący sposób:

## <a name="syntax"></a>Składnia

*deklarator* **:** *wyrażenia stałego*

## <a name="remarks"></a>Uwagi

(Opcjonalnie) *deklaratora* nazywa się za pomocą którego element członkowski jest dostępny w programie. Musi ona typ całkowity (w tym typy wyliczone). *Wyrażenie_stałe* określa liczbę bitów zajmuje elementu członkowskiego struktury. Pola bitowe anonimowe — oznacza to, że pole bitowe członków nie identyfikatorem — może służyć do wypełnienia.

> [!NOTE]
> Pole bitowe nienazwane szerokości 0 wymusza wyrównanie następne pole bitowe do następnego **typu** granic, gdzie **typu** jest typ elementu członkowskiego.

Poniższy przykład deklaruje strukturę, która zawiera pola bitowe:

```cpp
// bit_fields1.cpp
// compile with: /LD
struct Date {
   unsigned short nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned short nMonthDay : 6;    // 0..31  (6 bits)
   unsigned short nMonth    : 5;    // 0..12  (5 bits)
   unsigned short nYear     : 8;    // 0..100 (8 bits)
};
```

Koncepcyjny układ pamięci obiektu typu `Date` przedstawiono na poniższej ilustracji.

![Układ pamięci obiektu daty](../cpp/media/vc38uq1.png "vc38UQ1") Data obiektów pamięci układu

Należy pamiętać, że `nYear` ma długość 8 bitów i spowodowałoby przepełnienie granicy słowa zadeklarowanym typem **niepodpisane** **krótki**. W związku z tym, rozpoczyna się na początku nowego **niepodpisane** **krótki**. Nie jest konieczne, że wszystkie pola, które mieszczą się w jeden obiekt typu podstawowego; bitowe nowe jednostki w pamięci są przydzielane zgodnie z liczbą bitów w deklaracji.

**Microsoft Specific**

Porządkowanie danych zadeklarowany jako pola bitowe jest niski, wysoki-bitowych, jak pokazano na rysunku powyżej.

**END specyficzny dla Microsoft**

Jeśli deklaracja struktury zawiera pole bez nazwy długość wynosi 0, jak pokazano w poniższym przykładzie

```cpp
// bit_fields2.cpp
// compile with: /LD
struct Date {
   unsigned nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned nMonthDay : 6;    // 0..31  (6 bits)
   unsigned           : 0;    // Force alignment to next boundary.
   unsigned nMonth    : 5;    // 0..12  (5 bits)
   unsigned nYear     : 8;    // 0..100 (8 bits)
};
```

następnie układ pamięci jest, jak pokazano na poniższej ilustracji:

![Układ obiektu daty z zerem&#45;długość pola bitowego](../cpp/media/vc38uq2.png "vc38UQ2") układu obiektu daty za pomocą pola bitowe o zerowej długości

Podstawowy typ pola bitowego musi być typu całkowitego, zgodnie z opisem w [podstawowych typów](../cpp/fundamental-types-cpp.md).

Jeśli inicjator dla odwołania do typu `const T&` jest l-wartością, która odwołuje się do pola bitowego typu `T`, odwołanie nie jest powiązany z pola bitowego bezpośrednio. Zamiast tego odwołania jest powiązany do tymczasowej inicjowane na wartość pola bitowego.

## <a name="restrictions-on-bit-fields"></a>Ograniczenia dotyczące pól bitowych

Poniżej przedstawiono szczegółową listę błędne operacji w polach bitowych:

- Pobieranie adresu pola bitowego.

- Inicjowanie innej niż**const** odwołania z polem bitowym.

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../cpp/classes-and-structs-cpp.md)