---
title: Stos użycia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 827a129c0b7a444cc5b48ba68a3e360712e1c08e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721542"
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