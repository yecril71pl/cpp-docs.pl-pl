---
title: Wykorzystanie stosu
ms.date: 11/04/2016
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: 5ee9da50a03e1137ed6543cd349481148c9127d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452224"
---
# <a name="stack-usage"></a>Wykorzystanie stosu

Cała pamięć poza bieżący adres RSP jest uznawany za volatile: system operacyjny lub debugera, może spowodować zastąpienie tej pamięci podczas sesji debugowania użytkownika lub program obsługi przerwania. W efekcie RSP musi zawsze być ustawiona przed podjęciem próby odczytu lub zapisu wartości do ramki stosu.

W tej sekcji omówiono alokację miejsca na stosie dla zmiennych lokalnych i **alloca** wewnętrzne.

- [Alokacja stosu](../build/stack-allocation.md)

- [Konstrukcja obszaru stosu parametru dynamicznego](../build/dynamic-parameter-stack-area-construction.md)

- [Typy funkcji](../build/function-types.md)

- [malloc, wyrównanie](../build/malloc-alignment.md)

- [alloca](../build/alloca.md)

## <a name="see-also"></a>Zobacz też

[Konwencje kodowania x64](../build/x64-software-conventions.md)