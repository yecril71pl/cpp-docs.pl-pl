---
title: Przekazywanie parametru | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e838ee5f-c2fe-40b0-9a23-8023c949c820
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ec0c5b6fe00430c8b08fefdd8781b677004085e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369360"
---
# <a name="parameter-passing"></a>Przekazywanie parametru
Pierwszy argumenty cztery liczby całkowitej są przekazywane w rejestrach. Liczby całkowite są przekazywane (w kolejności od lewej do prawej) w RCX, RDX, R8 i R9. Argumenty 5 i nowszym są przekazywane na stosie. Wszystkie argumenty mają wyrównany do prawej w rejestrach. Jest to zrobić, jeśli wywoływany można zignorować górny bitów rejestru musi być i może uzyskać dostęp tylko część konieczne rejestru.  
  
 Zmiennoprzecinkowe i podwójnej precyzji argumenty są przekazywane w XMM0 — XMM3 (do 4) z miejscem liczba całkowita (RCX, RDX, R8 i R9), który jest zwykle używane do tego miejsca kardynalnej są ignorowane (Zobacz przykład) i na odwrót.  
  
 [__m128](../cpp/m128.md) typów, tablic i ciągi nigdy nie są przekazywane przez wartość bezpośrednia, ale raczej wskaźnik jest przekazywana do pamięci przydzielonej przez obiekt wywołujący. Struktury/Unii o rozmiarze 8, 16, 32 lub 64 bitów i __m64 są przekazywane, tak jakby były liczb całkowitych o tej samej wielkości. Struktury/unie innych niż te rozmiary są przekazywane jako wskaźnik do pamięci przydzielonej przez obiekt wywołujący. W przypadku tych typów agregacji przekazane jako wskaźnik (łącznie z \__m128), przydzielone przez obiekt wywołujący pamięci tymczasowej będzie wyrównany 16-bajtowych.  
  
 Funkcje wewnętrzne, nie zostanie przydzielone miejsce na stosie, które nie wymagają innych funkcji można użyć innych rejestrów volatile, aby przekazać argumenty dodatkowe rejestru, ponieważ istnieje ścisłej powiązanie między kompilator i implementacji funkcji wewnętrznej. Jest to dodatkowe możliwości dla poprawy wydajności.  
  
 Wywoływany odpowiada zrzucanie Parametry rejestru do ich miejsca w tle w razie potrzeby.  
  
 W poniższej tabeli przedstawiono, jak parametry są przekazywane:  
  
|Typ parametru|Jak przekazany|  
|--------------------|----------------|  
|Liczba zmiennoprzecinkowa|Pierwsze 4 parametry - XMM0 za pośrednictwem XMM3. Inne przekazany na stosie.|  
|Liczba całkowita|Pierwsze 4 parametry - R8 RCX, RDX, R9. Inne przekazany na stosie.|  
|Wartości zagregowanych (8, 16, 32 lub 64-bitowy) i __m64|Pierwsze 4 parametry - R8 RCX, RDX, R9. Inne przekazany na stosie.|  
|Wartości zagregowanych (inny)|Przez wskaźnik. Pierwsze 4 parametry przekazywane jako wskaźniki w RCX, RDX, R8 i R9|  
|__m128|Przez wskaźnik. Pierwsze 4 parametry przekazywane jako wskaźniki w RCX, RDX, R8 i R9|  
  
## <a name="example-of-argument-passing-1---all-integers"></a>Przykład 1 - wszystkie liczby całkowite przekazywanie argumentów  
  
```  
func1(int a, int b, int c, int d, int e);    
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack  
```  
  
## <a name="example-of-argument-passing-2---all-floats"></a>Przykład 2 - wszystkich elementów przestawnych przekazywanie argumentów  
  
```  
func2(float a, double b, float c, double d, float e);    
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack  
```  
  
## <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Przykład 3 - mieszane wskazówki i elementów przestawnych przekazywanie argumentów  
  
```  
func3(int a, double b, int c, float d);    
// a in RCX, b in XMM1, c in R8, d in XMM3  
```  
  
## <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>Przykład 4 przekazywanie argumentów-__m64, \__m128 i agregacji  
  
```  
func4(__m64 a, _m128 b, struct c, float d);  
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencja wywoływania](../build/calling-convention.md)