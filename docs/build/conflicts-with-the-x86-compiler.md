---
title: Powoduje konflikt z x86 kompilatora | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2b2b9c4cf871e8436a8da34a862d205541e7dc5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="conflicts-with-the-x86-compiler"></a>Konflikty z kompilatorem x86
Typy danych, które są większe niż 4 bajty nie są automatycznie wyrównane na stosie w używania x86 kompilator, aby skompilować aplikację. Ponieważ architekturę x86 kompilatora jest 4-bajtowych stosu wyrównane, żadnych większych niż 4 bajty, na przykład 64-bitową liczbę całkowitą, nie można automatycznie wyrównać je do adresu 8-bajtowych.  
  
 Praca z niewyrównany danych ma wpływ dwa.  
  
-   Może potrwać dłużej, dostęp do lokalizacji niewyrównany niż potrzebny dostęp do lokalizacji wyrównany.  
  
-   Nie można użyć lokalizacji niewyrównany w operacje blokowane.  
  
 Jeśli potrzebujesz więcej wyrównanie strict, użyj `__declspec(align(N)) on your variable declarations`. To powoduje, że kompilator dynamicznie Dopasuj stosu do Twojej specyfikacjami. Jednak dynamicznie dostosowywania stosu w czasie wykonywania może spowodować wolniejszy wykonywanie aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy i Magazyn](../build/types-and-storage.md)   
 [Dopasuj](../cpp/align-cpp.md)