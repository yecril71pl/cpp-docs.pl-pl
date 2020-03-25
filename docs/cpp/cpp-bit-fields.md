---
title: Pola bitowe języka C++
ms.date: 11/19/2018
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
ms.openlocfilehash: b952ca0aab5c4417f22fd958514894c53a39f800
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170608"
---
# <a name="c-bit-fields"></a>Pola bitowe języka C++

Klasy i struktury mogą zawierać elementy członkowskie, które zajmują mniej miejsca niż typ całkowity. Te elementy członkowskie są określone jako pola bitowe. Składnia dla *deklarator specyfikacji elementu członkowskiego* w polu bitowym jest następująca:

## <a name="syntax"></a>Składnia

*deklarator* **:** *wyrażenie stałe*

## <a name="remarks"></a>Uwagi

(Opcjonalnie) *deklarator* to nazwa, do której element członkowski jest dostępny w programie. Musi być typem całkowitym (z uwzględnieniem typów wyliczeniowych). *Wyrażenie stałe* określa liczbę bitów zajmowanych przez członka w strukturze. Anonimowe pola bitowe — czyli elementy członkowskie pola bitowego bez identyfikatora — mogą służyć do uzupełniania.

> [!NOTE]
> Nienazwane pole bitowe o szerokości 0 wymusza wyrównanie następnego pola bitowego do następnej granicy **typu** , gdzie **Type** jest typem elementu członkowskiego.

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

Układ pamięci koncepcyjnej obiektu typu `Date` pokazano na poniższej ilustracji.

![Układ pamięci obiektu Date](../cpp/media/vc38uq1.png "Układ pamięci obiektu Date") <br/>
Układ pamięci obiektu Date

Należy pamiętać, że `nYear` jest 8 bitów Long i spowodowałoby przepełnienie granicy słowa zadeklarowanego typu, **bez znaku** **.** W związku z tym rozpoczyna się na początku nowego **niepodpisanego znaku** **.** Nie jest konieczne, aby wszystkie pola bitowe mieściły się w jednym obiekcie typu podstawowego; przydzielono nowe jednostki magazynu, zgodnie z liczbą bitów żądaną w deklaracji.

**Specyficzne dla firmy Microsoft**

Kolejność danych zadeklarowanych jako pola bitowe jest od niskiej do wysokiego bitu, jak pokazano na powyższym rysunku.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Jeśli deklaracja struktury zawiera nienazwane pole o długości 0, jak pokazano w poniższym przykładzie,

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

następnie układ pamięci jest przedstawiony na poniższej ilustracji:

![Układ obiektu Date z polem bitowym o zerowej&#45;długości](../cpp/media/vc38uq2.png "Układ obiektu Date z polem bitowym o zerowej&#45;długości") <br/>
Układ obiektu Date z polem bitowym o zerowej długości

Typ podstawowy pola bitowego musi być typem całkowitym, zgodnie z opisem w [typach wbudowanych](../cpp/fundamental-types-cpp.md).

Jeśli inicjator dla odwołania typu `const T&` to lvalue, który odwołuje się do pola bitowego typu `T`, odwołanie nie jest bezpośrednio powiązane z polem bitowym. Zamiast tego odwołanie jest powiązane z tymczasową inicjalizacją do przechowywania wartości pola bitowego.

## <a name="restrictions-on-bit-fields"></a>Ograniczenia dotyczące pól bitowych

Poniższa lista zawiera błędne operacje dotyczące pól bitowych:

- Pobieranie adresu pola bitowego.

- Inicjowanie odwołania**niestałego** za pomocą pola bitowego.

## <a name="see-also"></a>Zobacz też

[Klasy i struktury](../cpp/classes-and-structs-cpp.md)
