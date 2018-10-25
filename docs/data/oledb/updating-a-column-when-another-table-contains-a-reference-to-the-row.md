---
title: Aktualizowanie kolumny, gdy inna tabela zawiera odwołanie do wiersza | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/24/2018
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
ms.openlocfilehash: 7998897c80e392326213324804c1809656e051f3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071826"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Aktualizowanie kolumny, gdy inna tabela zawiera odwołanie do wiersza

Niektórzy dostawcy może wykryć, które kolumny w zmiany wiersza, ale nie wielu dostawców. W rezultacie aktualizowanie kolumny, może spowodować błąd po odwołanie do wiersza, który próbujesz zaktualizować. Aby rozwiązać ten problem, Utwórz oddzielne dostępu, zawierający tylko kolumny, które chcesz zmienić. Należy przekazać liczbę tej metody dostępu `SetData`.

## <a name="see-also"></a>Zobacz też

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)