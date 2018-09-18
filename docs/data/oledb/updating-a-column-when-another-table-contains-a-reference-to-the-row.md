---
title: Aktualizowanie kolumny, gdy inna tabela zawiera odwołanie do wiersza | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6d2d3509b51d083290339514083a541ef9a86b64
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030667"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Aktualizowanie kolumny, gdy inna tabela zawiera odwołanie do wiersza

Niektórzy dostawcy może wykryć, które kolumny w zmiany wiersza, ale nie wielu dostawców. W rezultacie aktualizowanie kolumny, może spowodować błąd po odwołanie do wiersza, który próbujesz zaktualizować. Aby rozwiązać ten problem, Utwórz oddzielne dostępu, zawierający tylko kolumny, które chcesz zmienić. Należy przekazać liczbę tej metody dostępu `SetData`.  
  
## <a name="see-also"></a>Zobacz też  

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)