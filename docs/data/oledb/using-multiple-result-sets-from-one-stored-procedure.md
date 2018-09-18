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
ms.openlocfilehash: 3e75a100bb5b56b613419160a3ea063bce42bbdb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092326"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>Używanie wielu zestawów wyników z jednej procedury składowanej

Większość procedur składowanych zwrócić wielu zestawów wyników. Procedurę składowaną zwykle zawiera jeden lub więcej wybierz instrukcji. Konsument musi wziąć pod uwagę takie rozwiązanie pozwoli obsługiwać wszystkich zestawów wyników.  
  
### <a name="to-handle-multiple-result-sets"></a>Aby obsługiwać wiele wyników zestawów  
  
1. Tworzenie `CCommand` klasy `CMultipleResults` jako argument szablonu i za pomocą metody dostępu wybranego. Zazwyczaj jest dynamiczne lub ręczne metody dostępu. Jeśli używasz innego typu dostępu, nie może być możliwe ustalenie kolumny wyjściowe dla każdego zestawu wierszy.  
  
1. Wykonaj procedurę składowaną w zwykły sposób i powiąż kolumny (zobacz [jak mogę pobrać dane?](../../data/oledb/fetching-data.md)).  
  
1. Przy użyciu danych.  
  
1. Wywołaj `GetNextResult` na `CCommand` klasy. Jeśli inny wynik zestawu wierszy jest dostępna, `GetNextResult` zwraca wartość S_OK i powiąż kolumny powinna ponownie, jeśli używasz ręczne metody dostępu. Jeśli `GetNextResult` zwraca błąd, są dostępne zestawy nie dalsze wyników.  
  
## <a name="see-also"></a>Zobacz też  

[Korzystanie z procedur składowanych](../../data/oledb/using-stored-procedures.md)