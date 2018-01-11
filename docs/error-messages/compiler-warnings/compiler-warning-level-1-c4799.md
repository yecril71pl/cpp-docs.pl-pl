---
title: "Kompilatora (poziom 1) ostrzeżenie C4799 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4799
dev_langs: C++
helpviewer_keywords: C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9f41535c01d67e28baa2569ace2684865407a1d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4799"></a>Kompilator C4799 ostrzegawcze (poziom 1)  
  
> Nie EMMS na końcu funkcji "*funkcja*"  
  
Funkcja ma co najmniej jednej instrukcji MMX, ale nie ma `EMMS` instrukcji. W przypadku multimediów instrukcji `EMMS` instrukcji lub `_mm_empty` wewnętrzne powinny również wyczyść word tag multimedialnych na końcu MMX kodu.  
  
C4799 może wystąpić, gdy przy użyciu ivec.h, wskazując, że kod nie używa poprawnie wykonania instrukcji EMMS przed zwróceniem. Jest to fałszywe ostrzeżenie dla tych nagłówków. Użytkownik może wyłączyć, definiując _SILENCE_IVEC_C4799 w ivec.h. Należy jednak pamiętać, że to nie będą mogli kompilatora od wydawania poprawne ostrzeżenia tego typu.  
  
Aby uzyskać odpowiednie informacje, zobacz [ustawić instrukcji MMX firmy Intel](../../assembler/inline/intel-s-mmx-instruction-set.md).