---
title: Modyfikatory specyficzne dla firmy Microsoft | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f9533ffc2d21c3e8ee006fc97f7c61f4cb41115
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="microsoft-specific-modifiers"></a>Modyfikatory specyficzne dla firmy Microsoft
W tej sekcji opisano specyficzne dla firmy Microsoft rozszerzeń języka C++ w następujących obszarach:  
  
-   [Adresowanie na podstawie](../cpp/based-addressing.md), do rozwiązania jako podstawowy, z którego można przesunąć innych wskaźników za pomocą wskaźnika  
  
-   [Funkcja konwencji wywoływania](../cpp/calling-conventions.md)  
  
-   Rozszerzone atrybuty klasy magazynu zadeklarowana z [__declspec](../cpp/declspec.md) — słowo kluczowe  
  
-   [__W64](../cpp/w64.md) — słowo kluczowe  
  
 Wiele słów kluczowych specyficzne dla firmy Microsoft mogą służyć do modyfikowania deklaratorów do typów pochodnych. Aby uzyskać więcej informacji na temat deklaratorów, zobacz [Deklaratorów](http://msdn.microsoft.com/en-us/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838).  
  
### <a name="microsoft-specific-keywords"></a>Słowa kluczowe specyficzne dla firmy Microsoft  
  
|Słowo kluczowe|Znaczenie|Używany do tworzenia typów pochodnych?|  
|-------------|-------------|---------------------------------|  
|[__based](../cpp/based-grammar.md)|Poprzedzający nazwę deklaruje 32-bitowego przesunięcia z podstawową 32-bitowych zawarte w deklaracji.|Tak|  
|[__cdecl](../cpp/cdecl.md)|Nazwa, znajdujący się wykorzystuje C nazewnictwa i Konwencje wywoływania.|Tak|  
|[__declspec](../cpp/declspec.md)|Określa nazwę, która jest zgodna, atrybuty klasy magazynu specyficzne dla firmy Microsoft.|Nie|  
|[__fastcall](../cpp/fastcall.md)|Poprzedzający nazwę deklaruje funkcję, która korzysta z rejestrów, jeśli jest dostępna, zamiast stos przekazywanie argumentów.|Tak|  
|[__restrict](../cpp/extension-restrict.md)|Podobnie jak __declspec ([ograniczyć](../cpp/restrict.md)), ale do użytku w zmiennych.|Nie|  
|[__stdcall](../cpp/stdcall.md)|Poprzedzający nazwę określa funkcja obserwujące standardowej konwencji wywoływania.|Tak|  
|[__w64](../cpp/w64.md)|Oznacza typ danych jako większy na kompilator 64-bitowy.|Nie|  
|[__unaligned](../cpp/unaligned.md)|Określa, czy wskaźnik do typu lub innych danych nie jest wyrównany...|Nie|  
|[__vectorcall](../cpp/vectorcall.md)|Poprzedzający nazwę deklaruje funkcję, która używa rejestrów, w tym rejestry SSE, jeśli jest dostępna, zamiast stos przekazywanie argumentów.|Tak|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)