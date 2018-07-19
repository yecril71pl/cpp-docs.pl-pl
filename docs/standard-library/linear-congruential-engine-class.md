---
title: linear_congruential_engine — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::linear_congruential_engine
dev_langs:
- C++
helpviewer_keywords:
- linear_congruential_engine class
ms.assetid: 30e00ca6-1933-4701-9561-54f3e810a5a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d4069dc5151dd231773e926aadf17de7c03d3770
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958282"
---
# <a name="linearcongruentialengine-class"></a>linear_congruential_engine — Klasa

Generuje losową sekwencję przez liniowego algorytmu liczb pseudolosowych.

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

*UIntType* typ wyniku liczby całkowitej bez znaku. Aby możliwych typów, zobacz [ \<losowy >](../standard-library/random.md).

*A* **mnożnik**. **Warunek wstępny**: sekcję Zobacz uwagi.

*C* **przyrostu**. **Warunek wstępny**: sekcję Zobacz uwagi.

*M* **modulo**. **Warunek wstępny**: Zobacz uwagi.

## <a name="members"></a>Elementy członkowskie

||||
|-|-|-|
|`linear_congruential_engine::linear_congruential_engine`|`linear_congruential_engine::min`|`linear_congruential_engine::discard`|
|`linear_congruential_engine::operator()`|`linear_congruential_engine::max`|`linear_congruential_engine::seed`|

`default_seed` jest elementem członkowskim stałą, definiowany jako `1u`, który jest używany jako wartość domyślna parametru `linear_congruential_engine::seed` i konstruktora pojedynczej wartości.

Aby uzyskać więcej informacji na temat elementów członkowskich aparatu zobacz [ \<losowy >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

`linear_congruential_engine` Klasy szablonu jest najprostszym aparatu generator, ale nie najszybszy lub najwyższej jakości. Poprawa przez ten aparat jest [substract_with_carry_engine](../standard-library/subtract-with-carry-engine-class.md). Żadna z tych aparaty nie jest tak szybko, lub jako wysokiej jakości wyniki w postaci [mersenne_twister_engine —](../standard-library/mersenne-twister-engine-class.md).

Ten aparat tworzy wartości określonych przez użytkownika typ bez znaku typu całkowitego przy użyciu relacji cyklu ( *okres*) `x(i) = (A * x(i-1) + C) mod M`.

Jeśli *M* wynosi zero, wartość używana dla tej operacji modulo jest `numeric_limits<result_type>::max() + 1`. Stan aparatu jest ostatnią wartość zwracana lub wartość początkową, jeśli wprowadzono Brak wywołania `operator()`.

Jeśli *M* jest nie jest zerowa, wartości argumentów szablonu *A* i *C* musi być mniejsza niż *M*.

Chociaż można utworzyć generatora z tego aparatu bezpośrednio, umożliwia także jeden z tych wstępnie zdefiniowanych definicji typów.

`minstd_rand0`: 1988 minimalne standardowa aparat (Lewis Goodman i Miller 1969).

```cpp
typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
```

`minstd_rand`: Zaktualizowany aparat standard minimalny `minstd_rand0` (Park Miller i Stockmeyer, 1993).

```cpp
typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
```

Aby uzyskać szczegółowe informacje dotyczące algorytmu aparatu bloku liniowy złożony, zobacz artykułu w Wikipedii [liniowej generatora liczb pseudolosowych](http://go.microsoft.com/fwlink/p/?linkid=402446).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowy >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[\<losowy >](../standard-library/random.md)<br/>
