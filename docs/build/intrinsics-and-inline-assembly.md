---
title: Funkcje wewnętrzne i zestaw wbudowany
ms.date: 11/04/2016
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
ms.openlocfilehash: 033225259c0a33414fe45eba313bb1f1c94eb379
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515105"
---
# <a name="intrinsics-and-inline-assembly"></a>Funkcje wewnętrzne i zestaw wbudowany

Jednym z ograniczeń x64 kompilatora ma nie obsługują asemblera wbudowanego. Oznacza to, że funkcji nie można zapisać w C lub C++, albo musi być zapisywane jako procedury lub funkcji wewnętrznych obsługiwanych przez kompilator. Niektóre funkcje są wrażliwe na wydajność, a inne nie. Funkcje wrażliwego na wydajność, powinny zostać wdrożone jako funkcje wewnętrzne.

Funkcje wewnętrzne, obsługiwane przez kompilator są opisane w [funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md).

## <a name="see-also"></a>Zobacz też

[Konwencje kodowania x64](../build/x64-software-conventions.md)