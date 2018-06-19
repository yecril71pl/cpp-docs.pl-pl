---
title: Optymalizacja wbudowanego asemblera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c494594e3b7c541487f34fd33359b0e31f73dd61
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32050561"
---
# <a name="optimizing-inline-assembly"></a>Optymalizacja wbudowanego asemblera
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Obecność `__asm` blok w funkcji ma wpływ optymalizacji na kilka sposobów. Kompilator nie najpierw próbuje zoptymalizować `__asm` zablokować samej siebie. Pisanie w języku zestawu jest dokładnie, możesz uzyskać. Drugie, obecności `__asm` wpływa na blok zarejestrować zmiennej magazynu. Kompilator pozwala uniknąć rejestracja zmiennych w `__asm` zablokować, jeśli zawartość kasy zostałaby zmieniona przez `__asm` bloku. Na koniec włączenia języka zestawu w funkcji wpływ inne optymalizacje całej funkcji.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Wbudowany asembler](../../assembler/inline/inline-assembler.md)