---
title: Używanie wielu zestawów wyników z jednej procedury składowanej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6393901839e8450ebc45b11f1d4bd2250da2ca56
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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