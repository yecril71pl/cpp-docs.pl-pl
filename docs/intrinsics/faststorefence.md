---
title: __faststorefence | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __faststorefence_cpp
- __faststorefence
dev_langs: C++
helpviewer_keywords:
- __faststorefence intrinsic
- sfence instruction
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 54558f5df65834823e2e8d7da092aeb05e9030be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="faststorefence"></a>__faststorefence
**Dotyczące firmy Microsoft**  
  
 Gwarancji, że wszystkie poprzednie odwołania pamięci, zarówno w tym obciążenia i przechowywania odwołań do pamięci, jest widoczne globalnie, zanim wszystkie odwołania kolejnych pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __faststorefence();  
```  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__faststorefence`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Generuje całej pamięci bariery instrukcji sekwencję czy gwarancje obciążenia i przechowywać operacji wydanych przed wewnętrzne są globalnie nadal widoczny przed realizacją. Efekt jest porównywalna, ale szybciej niż `_mm_mfence` wewnętrznej na x64 wszystkich platform.  
  
 Na platformie AMD64 tej procedury generuje instrukcja jest szybsze ogranicznika magazynu niż `sfence` instrukcji. Kod krytyczny czasowo Użyj tym wewnętrznego, zamiast `_mm_sfence` tylko na platformach AMD64. Na platformach firmy Intel x64 `_mm_sfence` instrukcji jest szybsze.  
  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)