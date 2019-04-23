---
title: Aktualizowanie kolumny, gdy inna tabela zawiera odwołanie do wiersza
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
ms.openlocfilehash: 46de5f54a3ec6525f779a6b55a700429a2a84fef
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039218"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Aktualizowanie kolumny, gdy inna tabela zawiera odwołanie do wiersza

Niektórzy dostawcy może wykryć, które kolumny w zmiany wiersza, ale nie wielu dostawców. W rezultacie aktualizowanie kolumny, może spowodować błąd po odwołanie do wiersza, który próbujesz zaktualizować. Aby rozwiązać ten problem, Utwórz oddzielne dostępu, zawierający tylko kolumny, które chcesz zmienić. Należy przekazać liczbę tej metody dostępu `SetData`.

## <a name="see-also"></a>Zobacz także

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)