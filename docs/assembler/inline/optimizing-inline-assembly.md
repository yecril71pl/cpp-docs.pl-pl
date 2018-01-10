---
title: Optymalizacja wbudowanego asemblera | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 21f6954ece6adcc60fbb3a8620dd427e7c21042a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="optimizing-inline-assembly"></a>Optymalizacja wbudowanego asemblera
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Obecność `__asm` blok w funkcji ma wpływ optymalizacji na kilka sposobów. Kompilator nie najpierw próbuje zoptymalizować `__asm` zablokować samej siebie. Pisanie w języku zestawu jest dokładnie, możesz uzyskać. Drugie, obecności `__asm` wpływa na blok zarejestrować zmiennej magazynu. Kompilator pozwala uniknąć rejestracja zmiennych w `__asm` zablokować, jeśli zawartość kasy zostałaby zmieniona przez `__asm` bloku. Na koniec włączenia języka zestawu w funkcji wpływ inne optymalizacje całej funkcji.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Wbudowany asembler](../../assembler/inline/inline-assembler.md)