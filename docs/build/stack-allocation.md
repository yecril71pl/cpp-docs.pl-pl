---
title: Alokacja stosu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 098e51f2-eda6-40d0-b149-0b618aa48b47
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e0210239f2d915fcc3445a74cfdf5b0d1796df7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701502"
---
# <a name="stack-allocation"></a>Alokacja stosu

Prologu funkcji jest odpowiedzialny za przydzielanie miejsca na stosie dla zmiennych lokalnych, zapisane rejestrów, stos parametry i parametry rejestru.

Parametr obszar jest zawsze w dolnej części stosu (nawet jeśli jest używany alloca), dzięki czemu zawsze będzie sąsiadujące adres zwrotny podczas każde wywołanie funkcji. Zawiera on co najmniej cztery wpisy, ale zawsze wystarczającej ilości miejsca dla wszystkich parametrów wymaganych przez dowolną funkcję, która może zostać wywołana. Należy zauważyć, że dla parametrów rejestru miejsca jest zawsze przydzielana, nawet wtedy, gdy same parametry nigdy nie są umieszczone na stosie; / / wywoływany ma żadnej gwarancji, że miejsca przydzielonego dla jego parametrów. Adresy domowe są wymagane dla argumentów rejestru, więc ciągły obszar jest dostępna w przypadku, gdy wywołana funkcja musi przyjąć adresu listy argumentów (va_list) lub poszczególnych argumentu. Ten obszar zawiera również wygodne miejsce do zapisania rejestru argumentów podczas wykonywania thunk i opcję debugowania (na przykład, ułatwia argumenty znaleźć podczas debugowania, jeśli są one przechowywane na adresy domowe w kodzie prologu). Nawet wtedy, gdy wywołana funkcja ma następujące parametry mniej niż 4, te lokalizacje stosu 4 skutecznie własnością wywołanej funkcji i może być używany przez funkcję o nazwie do innych celów, oprócz zapisywanie parametru wartości rejestru.  Ten sposób obiekt wywołujący może nie zostać zapisana informacje w tym regionie stosu w wywołaniu funkcji.

Jeśli w funkcji miejsca jest przydzielany dynamicznie (alloca), następnie nieulotnej rejestru muszą być używane jako wskaźnik ramki, aby oznaczyć bazy stałej części stosu i rejestru musi być zapisany i inicjowana w prologu. Należy pamiętać, że użycie alloca wywołania do tej samej / / wywoływany z tego samego obiektu wywołującego może mieć różne adresy domowe ich parametrów rejestru.

Stos zostanie zachowany 16-bajtowy wyrównane, z wyjątkiem w prologu (na przykład po zostanie przypisany adres zwrotny) i z wyjątkiem wskazanych w [typy funkcji](../build/function-types.md) dla klasy funkcje ramki.

Poniżej przedstawiono, że przykładowy układ stosu, w którym wywołania funkcji element niebędący liściem funkcji prologu funkcji B. A ma już przydzielone miejsce dla wszystkich parametrów rejestru i stosu wymagane przez B na dole stosu. Wywołanie wypycha adres zwrotny i prologu B przydziela miejsce dla jego zmiennych lokalnych, nieulotnej rejestrów i miejsce wymagane do jej do wywołania funkcji. Jeśli B używa alloca, miejsce jest przydzielane między lokalnego rejestru zmiennej/nieulotnej Zapisz obszar i obszaru stosu parametru.

![Przykład konwersji AMD](../build/media/vcamd_conv_ex_5.png "AMD przykład konwersji")

Gdy funkcja B wywołuje inną funkcję, adres zwrotny jest wypychane bezpośrednio pod adres domowy dla RCX.

## <a name="see-also"></a>Zobacz też

[Wykorzystanie stosu](../build/stack-usage.md)