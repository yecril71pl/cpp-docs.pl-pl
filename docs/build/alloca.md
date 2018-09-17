---
title: alloca | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 2b209335-e3a0-4934-93f0-3b5925d22918
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0c73abcb52b991ee6bd4de839861aa4ef684181
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702749"
---
# <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) musi być 16-bajtowy wyrównany, a ponadto trzeba użyć wskaźnika ramki.

Stos, który jest przydzielany musi zawierać przestrzeń poniżej parametrów później wywoływanej funkcji, zgodnie z opisem w [alokacji stosu](../build/stack-allocation.md).

## <a name="see-also"></a>Zobacz też

[Wykorzystanie stosu](../build/stack-usage.md)