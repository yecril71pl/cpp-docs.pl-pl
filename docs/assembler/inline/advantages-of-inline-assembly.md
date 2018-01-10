---
title: Zalety wbudowanego asemblera | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 60b8d458212cd2175f2460c1382ed7f8c2c269bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="advantages-of-inline-assembly"></a>Zalety wbudowanego asemblera
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Asembler wbudowany nie wymagają osobny zestaw i kroki łącze, jest wygodniejsze niż oddzielne asemblera. Kod zestawu wbudowanego można użyć dowolnego C zmienną lub funkcję nazwę, która znajduje się w zakresie, dlatego łatwo zintegrować ją z kodem C z programem. Ponieważ kodu zestawu można łączyć wbudowany w instrukcjach języka C lub C++, możliwość zadania, które są skomplikowane lub niemożliwe w języka C lub C++.  
  
 Używa wbudowanego asemblera obejmują:  
  
-   Pisanie funkcji w języku zestawu.  
  
-   Optymalizacja miejscu krytyczna szybkość fragmentów kodu.  
  
-   Wprowadzenie dostępu bezpośredniego sprzętu, sterowników urządzeń.  
  
-   Pisanie kodu prolog i epilog dla wywołania "naked".  
  
 Wbudowany zestaw jest narzędziem specjalnych. Jeśli planujesz portu aplikacji na różnych komputerach, prawdopodobnie należy umieścić kodu określonych maszyny w oddzielnego modułu. Ponieważ asemblera wbudowanego nie obsługuje wszystkich Microsoft Macro Assembler firmy (MASM) dyrektywy makr i danych, może być bardziej wygodne MASM dla tych modułów.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Wbudowany asembler](../../assembler/inline/inline-assembler.md)