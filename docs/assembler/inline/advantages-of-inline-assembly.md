---
title: Zalety wbudowanego asemblera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 998ec5ff04911d3e476f0864f81f82b804969a82
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
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