---
title: Używanie wielu zestawów wyników z jednej procedury składowanej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/24/2018
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
ms.openlocfilehash: ac30f74a593f79cea7f252c454f19b85260e27b8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078516"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>Używanie wielu zestawów wyników z jednej procedury składowanej

Większość procedur składowanych zwrócić wielu zestawów wyników. Procedurę składowaną zwykle zawiera jeden lub więcej wybierz instrukcji. Konsument musi należy wziąć pod uwagę ten dołączania do obsługi wszystkich zestawów wyników.

## <a name="to-handle-multiple-result-sets"></a>Aby obsługiwać wiele wyników zestawów

1. Tworzenie `CCommand` klasy `CMultipleResults` jako argument szablonu i za pomocą metody dostępu, co pozwala zwykle dynamiczne lub ręczne metody dostępu. Jeśli używasz innego typu dostępu, nie może być możliwe ustalenie kolumny wyjściowe dla każdego zestawu wierszy.

1. Wykonaj procedurę składowaną w zwykły sposób i powiąż kolumny (zobacz [jak mogę pobrać dane?](../../data/oledb/fetching-data.md)).

1. Przy użyciu danych.

1. Wywołaj `GetNextResult` na `CCommand` klasy. Jeśli inny wynik zestawu wierszy jest dostępna, `GetNextResult` zwraca wartość S_OK i powiąż kolumny powinna ponownie, jeśli używasz ręczne metody dostępu. Jeśli `GetNextResult` zwraca błąd, są dostępne zestawy nie dalsze wyników.

## <a name="see-also"></a>Zobacz też

[Korzystanie z procedur składowanych](../../data/oledb/using-stored-procedures.md)