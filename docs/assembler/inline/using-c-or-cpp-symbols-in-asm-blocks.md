---
title: Użycie symboli C lub C++ w blokach __asm | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 746614de653649747bf20ae4c223e5687ee53f5c
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="using-c-or-c-symbols-in-asm-blocks"></a>Użycie symboli C lub C++ w blokach __asm
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 `__asm` Bloku może odwoływać się do żadnych symboli C lub C++ w zakresie, w którym pojawi się blok. (C i C++ symbole są nazwy zmiennych, nazwy funkcji i etykiety; które jest, nazw, które nie są stałe symboliczne lub `enum` elementów członkowskich. Nie można wywołać elementu członkowskiego C++ funkcji.)  
  
 Kilka ograniczeń dotyczą użycie symboli C i C++:  
  
-   Każda instrukcja języka zestawu może zawierać tylko jeden C lub C++ symbolu. Wiele symboli może występować w tej samej instrukcji zestawu tylko z **długość**, **typu**, i **rozmiar** wyrażenia.  
  
-   Funkcje, do którego odwołuje się `__asm` bloku musi być zadeklarowany we wcześniejszej części programu (prototypowana). W przeciwnym razie kompilator nie rozróżnia między nazwami funkcji i etykiet w `__asm` bloku.  
  
-   `__asm` Blok nie można używać żadnych symboli C lub C++ z taką samą pisownię jako słowa zastrzeżone MASM (niezależnie od wielkości liter). Słowa zastrzeżone MASM obejmują takie jak nazwy instrukcji **PUSH** i zarejestrować nazwy, takie jak SI.  
  
-   Tagi struktury i Unii nie są rozpoznawane w `__asm` bloków.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)