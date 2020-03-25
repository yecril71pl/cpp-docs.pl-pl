---
title: Używanie wielu zestawów wyników z jednej procedury składowanej
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
ms.openlocfilehash: 6163eb8bf18edfc3d205f1d012de0c64c5570693
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209290"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>Używanie wielu zestawów wyników z jednej procedury składowanej

Większość procedur składowanych zwraca wiele zestawów wyników. Taka procedura składowana zwykle zawiera jedną lub więcej instrukcji SELECT. Konsument musi wziąć pod uwagę ten dołączenie, aby obsłużyć wszystkie zestawy wyników.

## <a name="to-handle-multiple-result-sets"></a>Aby obsłużyć wiele zestawów wyników

1. Utwórz klasę `CCommand` z `CMultipleResults` jako argumentem szablonu i z metodą dodającą się do wyboru, zazwyczaj akcesorem dynamicznym lub ręcznym. Jeśli używasz innego typu metody dostępu, możesz nie być w stanie określić kolumn wyjściowych dla każdego zestawu wierszy.

1. Wykonaj procedurę składowaną w zwykły sposób i powiąż kolumny (zobacz [jak pobrać dane?](../../data/oledb/fetching-data.md)).

1. Użyj danych.

1. Wywołaj `GetNextResult` klasy `CCommand`. Jeśli jest dostępny inny zestaw wierszy wyników, `GetNextResult` zwraca S_OK i należy ponownie powiązać kolumny, jeśli używasz ręcznego dostępu. Jeśli `GetNextResult` zwraca błąd, nie ma dostępnych żadnych dalszych zestawów wyników.

## <a name="see-also"></a>Zobacz też

[Korzystanie z procedur składowanych](../../data/oledb/using-stored-procedures.md)
