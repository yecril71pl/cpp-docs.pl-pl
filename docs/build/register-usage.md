---
title: Użycie metody Register | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: ce58e2cf-afd3-4068-980e-28a209298265
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 705a8fef3043498c041ea7e5490a7b22c1db8e5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="register-usage"></a>Użycie metody Register
[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] Architektura zapewnia 16 ogólnego przeznaczenia rejestrów (zwanego rejestruje liczba całkowita), a także 16 XMM/YMM rejestrów zmiennoprzecinkowych dostępne. Rejestruje volatile są pliki tymczasowe rejestrów domniemania przez obiekt wywołujący, aby zostać zniszczone w wywołaniu. Rejestruje nieulotnej są wymagane do zachowania ich wartości w wywołaniu funkcji i musi zostać zapisany przez funkcję wywołującą, jeśli używana.  
  
 W poniższej tabeli opisano, jak każdy rejestr jest używany przez wywołania funkcji:  
  
||||  
|-|-|-|  
|Rejestruj|Stan|Zastosowanie|  
|RAX|Volatile|Zwracana wartość rejestru|  
|RCX|Volatile|Pierwszy argument liczba całkowita|  
|RDX|Volatile|Drugi argument liczba całkowita|  
|R8|Volatile|Trzeci argument liczba całkowita|  
|R9|Volatile|Czwarty argument liczba całkowita|  
|R10:R11|Volatile|Muszą zostać zachowane, w razie potrzeby przez obiekt wywołujący; używane w instrukcjach syscall/sysret|  
|R12:R15|Nieulotnej|Muszą być chronione przez wywoływany|  
|RDI|Nieulotnej|Muszą być chronione przez wywoływany|  
|RSI|Nieulotnej|Muszą być chronione przez wywoływany|  
|RBX|Nieulotnej|Muszą być chronione przez wywoływany|  
|RBP|Nieulotnej|Może być używany jako wskaźnik ramki; muszą być chronione przez wywoływany|  
|ŹRÓDŁO|Nieulotnej|Wskaźnik stosu|  
|XMM0, YMM0|Volatile|Pierwszy argument FP; pierwszy argument typu wektora podczas `__vectorcall` jest używany|  
|XMM1, YMM1|Volatile|Drugi argument FP; drugi argument typu wektora podczas `__vectorcall` jest używany|  
|XMM2, YMM2|Volatile|Trzeci argument FP; trzeci argument typu wektora podczas `__vectorcall` jest używany|  
|XMM3, YMM3|Volatile|Czwarty argument FP; czwarty argument typu wektora podczas `__vectorcall` jest używany|  
|XMM4, YMM4|Volatile|Muszą zostać zachowane, w razie potrzeby przez obiekt wywołujący; argument typu wektora piątej podczas `__vectorcall` jest używany|  
|XMM5, YMM5|Volatile|Muszą zostać zachowane, w razie potrzeby przez obiekt wywołujący; argument typu wektora szóstego podczas `__vectorcall` jest używany|  
|XMM6:XMM15, YMM6:YMM15|Nieulotnej (XMM) Volatile (górnej połowie YMM)|Muszą być chronione przez wywoływany. Rejestruje YMM muszą zostać zachowane, w razie potrzeby przez obiekt wywołujący.|  
  
## <a name="see-also"></a>Zobacz też  
 [x64 konwencje kodowania](../build/x64-software-conventions.md)   
 [__vectorcall](../cpp/vectorcall.md)
