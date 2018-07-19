---
title: ograniczenie (C++ AMP) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- cpu_CPP
- amp_CPP
dev_langs:
- C++
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 175dcbbf94ff28b1f59804eb996254e29dfef243
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947890"
---
# <a name="restrict-c-amp"></a>ograniczenie (C++ AMP)
Specyfikator ograniczenia może być stosowany do funkcji i deklaracji lambda. Wymusza on ograniczenia dotyczące kodu w funkcji i zachowania funkcji w zastosowaniach, które korzystają ze środowiska uruchomieniowego C++ Accelerated Massive Parallelism (C++ AMP).  
  
> [!NOTE]
>  Aby uzyskać informacje o **ograniczyć** — słowo kluczowe, która jest częścią **__declspec** atrybuty klasy magazynu, zobacz [ograniczyć](../cpp/restrict.md).  
  
 **Ograniczyć** klauzuli przybiera następujące formy:  
  
|Klauzula|Opis|  
|------------|-----------------|  
|`restrict(cpu)`|Funkcja może używać w pełni języka C++. Tylko inne funkcje, które są zadeklarowane za pomocą funkcji restrict(cpu) mogą wywołać tę funkcję.|  
|`restrict(amp)`|Funkcja może używać tylko podzbioru języka C++, który może być przyspieszony przez C++ AMP.|  
|Sekwencja `restrict(cpu)` i `restrict(amp)`.|Funkcja musi stosować się do ograniczeń zarówno `restrict(cpu)`, jak i `restrict(amp)`. Funkcja może być wywołana przez funkcje, które są zadeklarowane przy użyciu `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` lub `restrict(amp, cpu)`.<br /><br /> Postać `restrict(A) restrict(B)` może być zapisana jako `restrict(A,B)`.|  
  
## <a name="remarks"></a>Uwagi  
 **Ograniczyć** — słowo kluczowe jest kontekstowym słowem kluczowym. Specyfikatory ograniczeń `cpu` i `amp` nie są słowami zarezerwowanymi. Lista specyfikatorów nie jest rozszerzalna. Funkcja, która nie ma **ograniczyć** klauzula jest taka sama jak funkcja, która ma `restrict(cpu)` klauzuli.  
  
 Funkcja z klauzulą `restrict(amp)` ma następujące ograniczenia:  
  
-   Funkcja może wywołać tylko funkcje z klauzulą `restrict(amp)`.  
  
-   Funkcja musi być możliwa do wbudowania.  
  
-   Funkcja może zadeklarować tylko **int**, **unsigned int**, **float**, i **double** zmiennych oraz klasy i struktury, które zawierają tylko te typy. **wartość logiczna** jest też dozwolony, ale musi być wyrównany 4-bajtowych użycie w typu złożonego.  
  
-   Funkcje lambda nie mogą przechwytywać poprzez odwołanie i nie mogą przechwytywać wskaźników.  
  
-   Odwołania i wskaźniki pojedynczego pośrednictwa są obsługiwane tylko jako zmienne lokalne, argumenty funkcji i typy zwracane.  
  
-   Nie są dozwolone:  
  
    -   Rekursja.  
  
    -   Zmienne zadeklarowane za pomocą [volatile](../cpp/volatile-cpp.md) — słowo kluczowe.  
  
    -   Funkcje wirtualne.  
  
    -   Wskaźniki do funkcji.  
  
    -   Wskaźniki do funkcji członkowskich.  
  
    -   Wskaźniki w strukturach.  
  
    -   Wskaźniki do wskaźników.  
  
    -   **Przejdź do** instrukcji.  
  
    -   Instrukcje oznaczone.  
  
    -   **Spróbuj**, **catch**, lub **throw** instrukcji.  
  
    -   Zmienne globalne.  
  
    -   Zmienne statyczne. Użyj [tile_static — słowo kluczowe](../cpp/tile-static-keyword.md) zamiast tego.  
  
    -   **dynamic_cast** rzutowania.  
  
    -   **Typeid** operatora.  
  
    -   Deklaracje asm.  
  
    -   Elementy vararg.  
  
 Aby uzyskać omówienie ograniczeń funkcji, zobacz [ograniczenia restrict(amp)](http://go.microsoft.com/fwlink/p/?LinkId=251089).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `restrict(amp)`klauzuli.  
  
```cpp 
  
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