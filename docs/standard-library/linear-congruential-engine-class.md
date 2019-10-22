---
title: linear_congruential_engine — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::linear_congruential_engine
helpviewer_keywords:
- linear_congruential_engine class
ms.assetid: 30e00ca6-1933-4701-9561-54f3e810a5a1
ms.openlocfilehash: 3c1824eb22ed97e65e0556bc63b374f705f5c591
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689438"
---
# <a name="linear_congruential_engine-class"></a>linear_congruential_engine — Klasa

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

@No__t_1 *UIntType*
Typ wyniku bez znaku liczby całkowitej. W przypadku możliwych typów zobacz [\<random >](../standard-library/random.md).

*@No__t_1*
**Mnożnik**. **Warunek wstępny**: patrz sekcja uwagi.

@No__t_1 *C*
**Zwiększ**wartość. **Warunek wstępny**: patrz sekcja uwagi.

*M* \
**Moduł**. **Warunek wstępny**: Zobacz uwagi.

## <a name="members"></a>Elementy członkowskie

||||
|-|-|-|
|`linear_congruential_engine::linear_congruential_engine`|`linear_congruential_engine::min`|`linear_congruential_engine::discard`|
|`linear_congruential_engine::operator()`|`linear_congruential_engine::max`|`linear_congruential_engine::seed`|

`default_seed` jest stałą członkowską, zdefiniowaną jako `1u`, używaną jako domyślna wartość parametru `linear_congruential_engine::seed` i konstruktora pojedynczego wartości.

Aby uzyskać więcej informacji na temat elementów członkowskich silnika, zobacz [\<random >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Szablon klasy `linear_congruential_engine` jest najprostszym aparatem generatora, ale nie najszybszą lub najwyższą jakością. Udoskonaleniem tego aparatu jest [substract_with_carry_engine](../standard-library/subtract-with-carry-engine-class.md). Żaden z tych aparatów nie działa tak szybko, jak i z wysoką jakością jako [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md).

Ten aparat tworzy wartości określonego przez użytkownika niepodpisanego typu całkowitego przy użyciu relacji cyklicznej ( *okres*) `x(i) = (A * x(i-1) + C) mod M`.

Jeśli *M* jest zerem, wartość użyta dla tej operacji modulo jest `numeric_limits<result_type>::max() + 1`. Stan aparatu jest ostatnią zwracaną wartością lub wartością inicjatora, jeśli nie wykonano wywołania `operator()`.

Jeśli *M* nie jest zerem, wartości argumentów szablonu *a* i *C* muszą być mniejsze niż *M*.

Chociaż można skonstruować Generator z tego aparatu bezpośrednio, można również użyć jednego z tych wstępnie zdefiniowanych elementów typedef.

`minstd_rand0`:1988 minimalnego aparatu standardowego (Lewis przedstawiają, Goodman i Miller, 1969).

```cpp
typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
```

`minstd_rand`: Zaktualizowano minimalny `minstd_rand0` aparatu standardowego (parkowanie, Miller i Stockmeyer, 1993).

```cpp
typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
```

Aby uzyskać szczegółowe informacje na temat algorytmu liniowego aparatu złożony, zobacz artykuł Wikipedia [liniowy złożony Generator](https://go.microsoft.com/fwlink/p/?linkid=402446).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<random >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[\<random >](../standard-library/random.md)
