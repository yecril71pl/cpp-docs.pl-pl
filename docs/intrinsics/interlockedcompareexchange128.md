---
title: _InterlockedCompareExchange128 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
dev_langs: C++
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0cbf4e29e02670b4532a4be82864cf3cf040df73
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="interlockedcompareexchange128"></a>_InterlockedCompareExchange128
**Dotyczące firmy Microsoft**  
  
 Przeprowadza porównanie blokowanego 128-bitowe i exchange.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned char _InterlockedCompareExchange128(  
   __int64 volatile * Destination,  
   __int64 ExchangeHigh,  
   __int64 ExchangeLow,  
   __int64 * ComparandResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [w, out]`Destination`  
 Wskaźnik do miejsca docelowego, który jest tablicą dwóch 64-bitowych liczb całkowitych traktowane jako pole 128-bitowego. Miejsce docelowe danych musi być 16-bajtowych wyrównane, aby uniknąć ogólny błąd ochrony.  
  
 [in]`ExchangeHigh`  
 64-bitowa liczba całkowita, która mogą być wymieniane z wysoką część miejsca docelowego.  
  
 [in]`ExchangeLow`  
 64-bitowa liczba całkowita, która mogą być wymieniane z niskim część miejsca docelowego.  
  
 [w, out]`ComparandResult`  
 Wskaźnik do macierzy dwa 64-bitowych liczb całkowitych (traktowane jako pole 128-bitowego) do porównania z serwerem docelowym.  W danych wyjściowych to zostanie zastąpiony oryginalnej wartości elementu docelowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 1, jeśli wzorzec 128-bitowego to oryginalnej wartości elementu docelowego. `ExchangeHigh`i `ExchangeLow` zastąpić docelowy 128-bitowego.  
  
 0, jeśli argument porównania nie jest równa oryginalnej wartości elementu docelowego. Wartość elementu docelowego jest bez zmian i wartość atrybutu porównania jest zastępowany wartość miejsca docelowego.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_InterlockedCompareExchange128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Generuje tym wewnętrzna `cmpxchg16b` instrukcji (z `lock` prefiks) do wykonania porównania zablokowanym 128-bitowe i exchange. Wczesne wersje AMD 64-bitowym sprzęcie nie obsługują tej instrukcji. Aby sprawdzić sprzęt obsługę `cmpxchg16b` instrukcji, wywołanie `__cpuid` wewnętrzne z `InfoType=0x00000001 (standard function 1)`. Bit 13 `CPUInfo[2]` (ECX) wynosi 1, jeśli instrukcja jest obsługiwana.  
  
> [!NOTE]
>  Wartość `ComparandResult` zawsze jest zastępowany. Po `lock` instrukcji tym wewnętrzna natychmiast kopiuje początkowej wartości `Destination` do `ComparandResult`. Z tego powodu `ComparandResult` i `Destination` powinny wskazywać na lokalizacje osobną pamięć, aby uniknąć nieoczekiwanego zachowania.  
  
 Chociaż można używać `_InterlockedCompareExchange128` do synchronizacji niskiego poziomu wątku nie należy synchronizować ponad 128 bitów, jeśli można używać mniejszych funkcji synchronizacji (takich jak innych `_InterlockedCompareExchange` funkcje wewnętrzne) zamiast tego. Użyj `_InterlockedCompareExchange128` Jeśli chcesz atomic dostęp do 128-bitową wartość w pamięci.  
  
 Jeśli możesz uruchomić kodu korzystającego z tym wewnętrzna na sprzęcie, który nie obsługuje `cmpxchg16b` instrukcji są nieprzewidywalne wyniki.  
  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `_InterlockedCompareExchange128` Zamień wyższe słowo macierzy dwa 64-bitowych liczb całkowitych sumę jego słowa wysoki i niski i zwiększyć niski programu word. Dostęp do tablicy BigInt.Int atomic, ale w tym przykładzie używa pojedynczego wątku i ignoruje blokowania dla uproszczenia.  
  
```  
// cmpxchg16b.c  
// processor: x64  
// compile with: /EHsc /O2  
#include <stdio.h>  
#include <intrin.h>  
  
typedef struct _LARGE_INTEGER_128 {  
    __int64 Int[2];  
} LARGE_INTEGER_128, *PLARGE_INTEGER_128;  
  
volatile LARGE_INTEGER_128 BigInt;  
  
// This AtomicOp() function atomically performs:  
//   BigInt.Int[1] += BigInt.Int[0]  
//   BigInt.Int[0] += 1  
void AtomicOp ()  
{  
    LARGE_INTEGER_128 Comparand;  
    Comparand.Int[0] = BigInt.Int[0];  
    Comparand.Int[1] = BigInt.Int[1];  
    do {  
        ; // nothing  
    } while (_InterlockedCompareExchange128(BigInt.Int,  
                                            Comparand.Int[0] + Comparand.Int[1],  
                                            Comparand.Int[0] + 1,  
                                            Comparand.Int) == 0);  
}  
  
// In a real application, several threads contend for the value  
// of BigInt.  
// Here we focus on the compare and exchange for simplicity.  
int main(void)  
{  
   BigInt.Int[1] = 23;  
   BigInt.Int[0] = 11;  
   AtomicOp();  
   printf("BigInt.Int[1] = %d, BigInt.Int[0] = %d\n",  
      BigInt.Int[1],BigInt.Int[0]);  
}  
```  
  
```Output  
BigInt.Int[1] = 34, BigInt.Int[0] = 12  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
 Copyright 2007 zaawansowane Micro urządzeń, Inc. Wszelkie prawa zastrzeżone. Odtworzyć z uprawnieniem z zaawansowanymi Micro urządzeń, Inc.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Funkcje wewnętrzne _InterlockedCompareExchange](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)   
 [Konflikty z kompilatorem x86](../build/conflicts-with-the-x86-compiler.md)