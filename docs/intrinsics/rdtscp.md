---
title: __rdtscp | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __rdtscp
dev_langs:
- C++
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d890afe9e19782f19442e8d95709b91a8680278
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329806"
---
# <a name="rdtscp"></a>__rdtscp
**Microsoft Specific**  
  
 Generuje `rdtscp` instrukcji, zapisuje `TSC_AUX[31:0`] pamięci i zwraca licznika sygnatury czasu 64-bitowych (`TSC)` wynik.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned __int64 __rdtscp(  
   unsigned int * Aux  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out] `Aux`  
 Wskaźnik do lokalizacji, która będzie zawierać zawartość rejestru dotyczące komputera `TSC_AUX[31:0]`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba cykli 64-bitowej liczby całkowitej bez znaku.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__rdtscp`|0Fh rodziny NPT AMD lub nowszy|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Generuje tym wewnętrzna `rdtscp` instrukcji. Aby określić obsługi sprzętowej w tej instrukcji, należy wywołać `__cpuid` wewnętrzne z `InfoType=0x80000001` i sprawdź bit 27 `CPUInfo[3] (EDX)`. Ten bit jest 1, jeśli instrukcja jest obsługiwana i 0, w przeciwnym razie wartość.  Jeśli możesz uruchomić kodu korzystającego z tym wewnętrzna na sprzęcie, który nie obsługuje `rdtscp` instrukcji są nieprzewidywalne wyniki.  
  
> [!CAUTION]
>  W przeciwieństwie do `rdtsc`, `rdtscp` to instrukcja serializacji; Niemniej jednak kompilator można przenieść kod obejścia tego problemu wewnętrznej.  
  
 Interpretacja wartość TSC w tym pokoleniu sprzętu jest inna niż w starszych wersjach [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  Zobacz instrukcje sprzętu, aby uzyskać więcej informacji.  
  
 Znaczenie tej wartości w `TSC_AUX[31:0]` zależy od systemu operacyjnego.  
  
## <a name="example"></a>Przykład  
  
```  
#include <intrin.h>   
#include <stdio.h>  
int main()   
{  
 unsigned __int64 i;  
 unsigned int ui;  
 i = __rdtscp(&ui);  
 printf_s("%I64d ticks\n", i);  
 printf_s("TSC_AUX was %x\n", ui);  
}  
```  
  
```Output  
3363423610155519 ticks  
TSC_AUX was 0  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
 Copyright 2007 zaawansowane Micro urządzeń, Inc. Wszelkie prawa zastrzeżone. Odtworzyć z uprawnieniem z zaawansowanymi Micro urządzeń, Inc.  
  
## <a name="see-also"></a>Zobacz też  
 [__rdtsc](../intrinsics/rdtsc.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)