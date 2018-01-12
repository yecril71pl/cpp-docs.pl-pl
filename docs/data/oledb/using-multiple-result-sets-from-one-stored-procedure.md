---
title: "Używanie wielu zestawów wyników z jednej procedury składowanej | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ec887f01e377ffa6295086bbeeb56dcd884d6276
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>Używanie wielu zestawów wyników z jednej procedury składowanej
Większość procedur składowanych zwrócić wielu zestawów wyników. Procedury składowanej zwykle zawiera jeden lub więcej wybierz instrukcje. Konsument musi należy wziąć pod uwagę tak, aby obsłużyć wszystkich zestawów wyników.  
  
### <a name="to-handle-multiple-result-sets"></a>Do obsługi wielu wyników ustawia  
  
1.  Utwórz `CCommand` klasy z `CMultipleResults` jako argument szablonu, a akcesor wybranych przez użytkownika. Zazwyczaj jest ręczne lub dynamiczne metody dostępu. Jeśli używasz innego typu dostępu, nie można określić kolumn wyjściowych dla każdego zestawu wierszy.  
  
2.  W zwykły sposób wykonywania procedury składowanej i powiąż kolumny (zobacz [jak pobrać danych?](../../data/oledb/fetching-data.md)).  
  
3.  Korzystanie z danych.  
  
4.  Wywołanie `GetNextResult` na `CCommand` klasy. Jeśli inny wynik zestawu wierszy jest dostępna, `GetNextResult` zwraca S_OK i powiąż kolumny powinna ponownie, jeśli używasz ręczne metody dostępu. Jeśli `GetNextResult` zwraca błąd, są dostępne zestawy nie dalsze wyników.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z procedur składowanych](../../data/oledb/using-stored-procedures.md)