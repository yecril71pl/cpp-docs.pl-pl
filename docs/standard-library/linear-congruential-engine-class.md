---
title: linear_congruential_engine — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::linear_congruential_engine
helpviewer_keywords:
- linear_congruential_engine class
ms.assetid: 30e00ca6-1933-4701-9561-54f3e810a5a1
ms.openlocfilehash: f5b448fbf158cf9e9cfb8331c6ec7a228859fffc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447586"
---
# <a name="linearcongruentialengine-class"></a>linear_congruential_engine — Klasa

Generuje losową sekwencję za pomocą liniowego algorytmu złożony.

## <a name="syntax"></a>Składnia

```cpp
class linear_congruential_engine{
   public:  // types
   typedef UIntType result_type;
   // engine characteristics
   static constexpr result_type multiplier = a;
   static constexpr result_type increment = c;
   static constexpr result_type modulus = m;
   static constexpr result_type min() { return c == 0u  1u: 0u; }
   static constexpr result_type max() { return m - 1u; }
   static constexpr result_type default_seed = 1u;
   // constructors and seeding functions
   explicit linear_congruential_engine(result_type s = default_seed);
   template <class Sseq>
   explicit linear_congruential_engine(Sseq& q);
   void seed(result_type s = default_seed);
   template <class Sseq>
   void seed(Sseq& q);
   // generating functions
   result_type operator()();
   void discard(unsigned long long z);
   };
```

### <a name="parameters"></a>Parametry

*UInttype*\
Typ wyniku bez znaku liczby całkowitej. W przypadku możliwych typów zobacz [ \<losowe >](../standard-library/random.md).

*Z*\
**Mnożnik**. **Warunek wstępny**: Zobacz sekcję Uwagi.

*S*\
**Zwiększ**wartość. **Warunek wstępny**: Zobacz sekcję Uwagi.

*MOL*\
**Moduł**. **Warunek wstępny**: Zobacz uwagi.

## <a name="members"></a>Elementy członkowskie

||||
|-|-|-|
|`linear_congruential_engine::linear_congruential_engine`|`linear_congruential_engine::min`|`linear_congruential_engine::discard`|
|`linear_congruential_engine::operator()`|`linear_congruential_engine::max`|`linear_congruential_engine::seed`|

`default_seed`jest stałą składową, zdefiniowaną `1u`jako domyślną `linear_congruential_engine::seed` wartością parametru i konstruktorem pojedynczej wartości.

Aby uzyskać więcej informacji na temat elementów członkowskich silnika, zobacz [ \<Random >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Klasa `linear_congruential_engine` szablonu jest najprostszym aparatem generatora, ale nie najszybszą lub najwyższą jakością. Udoskonaleniem tego aparatu jest [substract_with_carry_engine](../standard-library/subtract-with-carry-engine-class.md). Żaden z tych aparatów nie działa tak szybko, jak i z wysoką jakością jako [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md).

Ten aparat tworzy wartości określonego przez użytkownika niepodpisanego typu całkowitego przy użyciu relacji powtarzania (kropka) `x(i) = (A * x(i-1) + C) mod M`.

Jeśli *M* jest zerem, wartość użyta dla tej operacji modulo `numeric_limits<result_type>::max() + 1`jest. Stan aparatu jest ostatnią zwracaną wartością lub wartością inicjatora, jeśli nie wykonano wywołania `operator()`.

Jeśli *M* nie jest zerem, wartości argumentów szablonu *a* i *C* muszą być mniejsze niż *M*.

Chociaż można skonstruować Generator z tego aparatu bezpośrednio, można również użyć jednego z tych wstępnie zdefiniowanych elementów typedef.

`minstd_rand0`: 1988 minimalne standardowe aparatu (Lewis przedstawiają, Goodman i Miller, 1969).

```cpp
typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
```

`minstd_rand`: Zaktualizowano minimalny silnik `minstd_rand0` standardowy (Park, Miller i Stockmeyer, 1993).

```cpp
typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
```

Aby uzyskać szczegółowe informacje na temat algorytmu liniowego aparatu złożony, zobacz artykuł Wikipedia [liniowy złożony Generator](https://go.microsoft.com/fwlink/p/?linkid=402446).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[\<random>](../standard-library/random.md)
