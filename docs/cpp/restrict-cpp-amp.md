---
title: ograniczenie (C++ AMP) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- cpu_CPP
- amp_CPP
dev_langs:
- C++
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 60ac40e2cb64c307574d14c1f7cc7a5290c740ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="restrict-c-amp"></a>ograniczenie (C++ AMP)
Specyfikator ograniczenia może być stosowany do funkcji i deklaracji lambda. Wymusza on ograniczenia dotyczące kodu w funkcji i zachowania funkcji w zastosowaniach, które korzystają ze środowiska uruchomieniowego C++ Accelerated Massive Parallelism (C++ AMP).  
  
> [!NOTE]
>  Aby uzyskać informacje o `restrict` — słowo kluczowe, który jest częścią `__declspec` atrybuty klasy magazynu, zobacz [ograniczyć](../cpp/restrict.md).  
  
 Klauzula `restrict` przybiera następujące formy:  
  
|Klauzula|Opis|  
|------------|-----------------|  
|`restrict(cpu)`|Funkcja może używać w pełni języka C++. Tylko inne funkcje, które są zadeklarowane za pomocą funkcji restrict(cpu) mogą wywołać tę funkcję.|  
|`restrict(amp)`|Funkcja może używać tylko podzbioru języka C++, który może być przyspieszony przez C++ AMP.|  
|Sekwencja `restrict(cpu)` i `restrict(amp)`.|Funkcja musi stosować się do ograniczeń zarówno `restrict(cpu)`, jak i `restrict(amp)`. Funkcja może być wywołana przez funkcje, które są zadeklarowane przy użyciu `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` lub `restrict(amp, cpu)`.<br /><br /> Postać `restrict(A) restrict(B)` może być zapisana jako `restrict(A,B)`.|  
  
## <a name="remarks"></a>Uwagi  
 Słowo kluczowe `restrict` jest kontekstowym słowem kluczowym. Specyfikatory ograniczeń `cpu` i `amp` nie są słowami zarezerwowanymi. Lista specyfikatorów nie jest rozszerzalna. Funkcja bez klauzuli `restrict` jest taka sama, jak funkcja z klauzulą `restrict(cpu)`.  
  
 Funkcja z klauzulą `restrict(amp)` ma następujące ograniczenia:  
  
-   Funkcja może wywołać tylko funkcje z klauzulą `restrict(amp)`.  
  
-   Funkcja musi być możliwa do wbudowania.  
  
-   Funkcja może zadeklarować tylko zmienne `int`, `unsigned int`, `float` i `double` oraz klasy i struktury, które zawierają te typy. `bool` jest też dozwolony, ale musi być wyrównany do 4-bajtów w razie użycia typu złożonego.  
  
-   Funkcje lambda nie mogą przechwytywać poprzez odwołanie i nie mogą przechwytywać wskaźników.  
  
-   Odwołania i wskaźniki pojedynczego pośrednictwa są obsługiwane tylko jako zmienne lokalne, argumenty funkcji i typy zwracane.  
  
-   Nie są dozwolone:  
  
    -   Rekursja.  
  
    -   Zmiennych zadeklarowano za [volatile](../cpp/volatile-cpp.md) — słowo kluczowe.  
  
    -   Funkcje wirtualne.  
  
    -   Wskaźniki do funkcji.  
  
    -   Wskaźniki do funkcji członkowskich.  
  
    -   Wskaźniki w strukturach.  
  
    -   Wskaźniki do wskaźników.  
  
    -   Instrukcje `goto`.  
  
    -   Instrukcje oznaczone.  
  
    -   Instrukcje `try`, `catch` lub `throw`.  
  
    -   Zmienne globalne.  
  
    -   Zmienne statyczne. Użyj [tile_static — słowo kluczowe](../cpp/tile-static-keyword.md) zamiast tego.  
  
    -   Rzutowania `dynamic_cast`.  
  
    -   Operator `typeid`.  
  
    -   Deklaracje asm.  
  
    -   Elementy vararg.  
  
 Omówienie funkcji ograniczenia, zobacz [restrict(amp) ograniczenia](http://go.microsoft.com/fwlink/p/?LinkId=251089).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `restrict(amp)`klauzuli.  
  
```  
  
void functionAmp() restrict(amp) {}   
void functionNonAmp() {}   
  
void callFunctions() restrict(amp)   
{   
    // int is allowed.  
    int x;  
    // long long int is not allowed in an amp-restricted function. This generates a compiler error.  
    // long long int y;   
  
    // Calling an amp-restricted function is allowed.  
    functionAmp();   
  
    // Calling a non-amp-restricted function is not allowed.  
    // functionNonAmp();   
  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)