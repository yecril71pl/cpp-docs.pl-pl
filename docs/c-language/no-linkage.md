---
title: Brak połączenia
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: a7c9a5b8f0ba92830500e55818093981a044d2df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218809"
---
# <a name="no-linkage"></a>Brak połączenia

Jeśli deklaracja identyfikatora w bloku nie zawiera **`extern`** specyfikatora klasy magazynowania, identyfikator nie ma powiązania i jest unikatowy dla funkcji.

Następujące identyfikatory nie mają powiązania:

- Identyfikator zadeklarowany jako coś innego niż obiekt lub funkcja

- Identyfikator zadeklarowany jako parametr funkcji

- Identyfikator zakresu bloku dla obiektu zadeklarowanego bez **`extern`** specyfikatora klasy magazynu

Jeśli identyfikator nie ma powiązania, zadeklarowanie tej samej nazwy (w Deklarator lub specyfikatorze typu) na tym samym poziomie zakresu generuje błąd ponownej definicji symbolu.

## <a name="see-also"></a>Zobacz także

[Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)
