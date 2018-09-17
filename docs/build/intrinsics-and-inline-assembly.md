---
title: Funkcje wewnętrzne i zestaw wbudowany | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a87e577af339099eda56a3b9d91929a05253a43
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716251"
---
# <a name="intrinsics-and-inline-assembly"></a>Funkcje wewnętrzne i zestaw wbudowany

Jednym z ograniczeń x64 kompilatora ma nie obsługują asemblera wbudowanego. Oznacza to, że funkcji nie można zapisać w C lub C++, albo musi być zapisywane jako procedury lub funkcji wewnętrznych obsługiwanych przez kompilator. Niektóre funkcje są wrażliwe na wydajność, a inne nie. Funkcje wrażliwego na wydajność, powinny zostać wdrożone jako funkcje wewnętrzne.

Funkcje wewnętrzne, obsługiwane przez kompilator są opisane w [funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md).

## <a name="see-also"></a>Zobacz też

[Konwencje kodowania x64](../build/x64-software-conventions.md)