---
title: __assume | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __assume
- __assume_cpp
dev_langs: C++
helpviewer_keywords: __assume keyword [C++]
ms.assetid: d8565123-b132-44b1-8235-5a8c8bff85a7
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 890b46f044c018f68226f3698c65603f931f01fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="assume"></a>__assume
**Dotyczące firmy Microsoft**  
  
 Przekazuje Optymalizator wskazówkę.  
  
## <a name="syntax"></a>Składnia  
  
```  
__assume(  
   expression  
)  
```  
  
#### <a name="parameters"></a>Parametry  
 `expression`  
 Dowolne wyrażenie przyjęto, że mogła zwrócić wartość true.  
  
## <a name="remarks"></a>Uwagi  
 Optymalizator przyjęto założenie, że warunek reprezentowany przez `expression` ma wartość true w momencie, gdzie pojawi się ze słowem kluczowym i pozostaje wartość true, dopóki `expression` jest modyfikowany (na przykład przez przypisanie do zmiennej). Selektywne użycia wskazówek przekazany do Optymalizator przez `__assume` może poprawić optymalizacji.  
  
 Jeśli `__assume` instrukcji są zapisywane jako sprzeczności (wyrażeniem zawsze FALSE), jest on zawsze traktowany `__assume(0)`. Jeśli kod nie działa zgodnie z oczekiwaniami, upewnij się, że `expression` zdefiniowanego jest prawidłowa i czy ma wartość true, zgodnie z wcześniejszym opisem. Aby uzyskać więcej informacji na temat Oczekiwano `__assume(0)` zachowania, zobacz uwagi nowsze.  
  
> [!WARNING]
>  Program nie może zawierać nieprawidłową `__assume` instrukcji w ścieżce dostępny. Jeśli kompilator może dotrzeć nieprawidłową `__assume` instrukcji, program może spowodować nieprzewidywalne i potencjalnie niebezpiecznych zachowanie.  
  
 `__assume`nie jest oryginalne wewnętrznej. Nie musi być zadeklarowana jako funkcja i nie można używać w `#pragma intrinsic` dyrektywy. Chociaż nie jest wygenerowano kodu, jest wpływ na kod wygenerowany przez optymalizator.  
  
 Użyj `__assume` w [ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) tylko wtedy, gdy assert nie jest możliwe do odzyskania. Nie używaj `__assume` w assert, dla którego masz kod odzyskiwania kolejny błąd ponieważ kompilator może zoptymalizować optymalizacji kodu obsługi błędu.  
  
 `__assume(0)` Instrukcja jest szczególnych przypadkach. Użyj `__assume(0)` wskaż ścieżkę kodu, który nie można nawiązać połączenia. Poniższy przykład przedstawia użycie `__assume(0)` aby wskazać, że nie można nawiązać połączenia w przypadku domyślnego instrukcji switch. To pokazano sposób użycia najczęstszych `__assume(0)`.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__assume`|x86, ARM,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
## <a name="example"></a>Przykład  
  
```  
// compiler_intrinsics__assume.cpp  
#ifdef DEBUG  
# define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__) )  
#else  
# define ASSERT(e)    ( __assume(e) )  
#endif  
  
void func1(int i)  
{  
}  
  
int main(int p)  
{  
   switch(p){  
      case 1:  
         func1(1);  
         break;  
      case 2:  
         func1(-1);  
         break;  
      default:  
         __assume(0);  
            // This tells the optimizer that the default  
            // cannot be reached. As so, it does not have to generate  
            // the extra code to check that 'p' has a value   
            // not represented by a case arm. This makes the switch   
            // run faster.  
   }  
}  
```  
  
 Korzystanie z `__assume(0)` Optymalizator informuje, że przypadek domyślny nie można nawiązać połączenia. W przykładzie pokazano, że programistę wie, że możliwe tylko danych wejściowych dla `p` będzie mieć wartość 1 lub 2. Jeśli do została przekazana wartość inna `p`, program staje się nieprawidłowa i powoduje, że nieprzewidywalne zachowanie.  
  
 W `__assume(0)` instrukcji, kompilator nie generuje kod, aby sprawdzić czy `p` ma wartość, która nie jest uwzględniona w instrukcji case. Aby to zrobić `__assume(0)` instrukcja musi być pierwszą instrukcją w treści na przypadek domyślny.  
  
 Ponieważ kompilator generuje kod na podstawie `__assume`, ten kod może nie działać prawidłowo, jeśli wyrażenie w elemencie `__assume` instrukcji ma wartość false w czasie wykonywania. Jeśli nie masz pewności, że wyrażenie będzie zawsze wartość true w czasie wykonywania, możesz użyć `assert` funkcji, aby zabezpieczyć ten kod.  
  
```  
#define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__)), __assume(e) )  
```  
  
 Niestety, to użycie `assert` zabezpiecza kompilator przed wykonaniem optymalizacji przypadek domyślny, który został opisany wcześniej w tym dokumencie. Alternatywnie można użyć oddzielnych makra, w następujący sposób.  
  
```  
#ifdef DEBUG  
# define NODEFAULT   ASSERT(0)  
#else  
# define NODEFAULT   __assume(0)  
#endif  
  
   default:  
      NODEFAULT;  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)