---
title: "linear_congruential_engine — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::linear_congruential_engine
dev_langs:
- C++
helpviewer_keywords:
- linear_congruential_engine class
ms.assetid: 30e00ca6-1933-4701-9561-54f3e810a5a1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f1e7b2362802ff72a029e7ffe91ed792eb056b7
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="linearcongruentialengine-class"></a>linear_congruential_engine — Klasa
Generuje losowe sekwencji przez algorytm congruential liniowej.  
  
## <a name="syntax"></a>Składnia  
```  
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
#### <a name="parameters"></a>Parametry  
 `UIntType`  
 Typ wyniku liczbę całkowitą bez znaku. Dla typów możliwych [ \<losowe >](../standard-library/random.md).  
  
 `A`  
 **Mnożnik**. **Warunek wstępny**: sekcji Zobacz uwagi.  
  
 `C`  
 **Przyrost**. **Warunek wstępny**: sekcji Zobacz uwagi.  
  
 `M`  
 **Modulo**. **Warunek wstępny**: Zobacz uwagi.  
  
## <a name="members"></a>Elementy członkowskie  
  
||||  
|-|-|-|  
|`linear_congruential_engine::linear_congruential_engine`|`linear_congruential_engine::min`|`linear_congruential_engine::discard`|  
|`linear_congruential_engine::operator()`|`linear_congruential_engine::max`|`linear_congruential_engine::seed`|  
  
 `default_seed` jest elementem członkowskim stałej, zdefiniowanej jako `1u`, używana jako domyślna wartość parametru `linear_congruential_engine::seed` i Konstruktor pojedynczej wartości.  
  
 Aby uzyskać więcej informacji na temat aparatu członków zobacz [ \<losowe >](../standard-library/random.md).  
  
## <a name="remarks"></a>Uwagi  
 `linear_congruential_engine` Klasy szablonu jest najprostsza aparat generator, ale nie najszybszym lub najwyższej jakości. Poprawa za pośrednictwem tego aparatu jest [substract_with_carry_engine](../standard-library/subtract-with-carry-engine-class.md). Żadna z tych aparaty jest tak szybko, lub za pomocą jako wysokiej jakości wyniki w postaci [mersenne_twister_engine —](../standard-library/mersenne-twister-engine-class.md).  
  
 Ten aparat tworzy wartości określonych przez użytkownika bez znaku typu całkowitego przy użyciu relacji cyklu ( *okres*) `x(i) = (A * x(i-1) + C) mod M`.  
  
 Jeśli `M` wynosi zero, używana dla tej operacji modulo wartość `numeric_limits<result_type>::max() + 1`. Stan aparatu jest ostatnią wartość zwracana lub wartości początkowej, jeśli dokonano Brak wywołania `operator()`.  
  
 Jeśli `M` jest nie jest zerowa, wartości argumentów szablonu `A` i `C` musi być mniejsza niż `M`.  
  
 Mimo że można bezpośrednio utworzyć generator z tym aparatem, umożliwia także jeden z tych wstępnie zdefiniowanych definicje typów.  
  
 `minstd_rand0`: 1988 minimalnego standardowe aparat (Nowak, Goodman i Tomaszewski, 1969).  
  
```  
typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;  
```  
  
 `minstd_rand`: Zaktualizowany aparat standardowe minimalnego `minstd_rand0` (wstrzymywanie Tomaszewski i Stockmeyer, 1993).  
  
```  
typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;  
```  
  
 Aby uzyskać szczegółowe informacje o algorytm liniowej aparat congruential, zobacz artykuł Wikipedia [liniowej generator congruential](http://go.microsoft.com/fwlink/p/?linkid=402446).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<losowe >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [\<losowe >](../standard-library/random.md)


