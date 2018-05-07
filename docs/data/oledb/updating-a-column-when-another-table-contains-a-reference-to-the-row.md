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
ms.openlocfilehash: 17d260f522432a78729c9998c518398dfa41275a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Aktualizowanie kolumny, gdy inna tabela zawiera odwołanie do wiersza
Niektórzy dostawcy może wykryć kolumny, które w przypadku zmiany wiersza, ale nie wielu dostawców. W związku z tym aktualizowanie kolumny może spowodować błąd, gdy występuje odwołanie do wiersza, który próbujesz zaktualizować. Aby rozwiązać ten problem, Utwórz oddzielne dostępu, zawierający tylko kolumny, które chcesz zmienić. Przekazać liczbę tej metody dostępu `SetData`.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)