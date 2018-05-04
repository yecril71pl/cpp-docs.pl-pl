---
title: Powoduje konflikt z x86 kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7cd72de4922c297b4a230e0dc0fb606b56a2a473
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="conflicts-with-the-x86-compiler"></a>Konflikty z kompilatorem x86
Typy danych, które są większe niż 4 bajty nie są automatycznie wyrównane na stosie w używania x86 kompilator, aby skompilować aplikację. Ponieważ architekturę x86 kompilatora jest 4-bajtowych stosu wyrównane, żadnych większych niż 4 bajty, na przykład 64-bitową liczbę całkowitą, nie można automatycznie wyrównać je do adresu 8-bajtowych.  
  
 Praca z niewyrównany danych ma wpływ dwa.  
  
-   Może potrwać dłużej, dostęp do lokalizacji niewyrównany niż potrzebny dostęp do lokalizacji wyrównany.  
  
-   Nie można użyć lokalizacji niewyrównany w operacje blokowane.  
  
 Jeśli potrzebujesz więcej wyrównanie strict, użyj `__declspec(align(N)) on your variable declarations`. To powoduje, że kompilator dynamicznie Dopasuj stosu do Twojej specyfikacjami. Jednak dynamicznie dostosowywania stosu w czasie wykonywania może spowodować wolniejszy wykonywanie aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy i Magazyn](../build/types-and-storage.md)   
 [align](../cpp/align-cpp.md)