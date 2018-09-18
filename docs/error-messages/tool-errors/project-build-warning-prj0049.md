---
title: Ostrzeżenie prj0049 dotyczące kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 169ba63318f630ac6a63b18d34fd6a7d829f4f90
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110890"
---
# <a name="project-build-warning-prj0049"></a>Ostrzeżenie PRJ0049 dotyczące kompilacji projektu

Przywoływany element docelowy "\<odwołanie >" wymaga programu .NET Framework \<MinFrameworkVersion > i nie będzie można uruchamiać na platformę docelową tego projektu

Aplikacje utworzone przy użyciu programu Visual Studio 2008 można określić, która wersja programu .NET Framework powinien dotyczyć. Jeśli dodasz odwołanie do zestawu lub projektu, który zależy od wersji programu .NET Framework, która jest nowsza niż wersja docelowa, otrzymasz ostrzeżenie w czasie kompilacji.

### <a name="to-correct-this-warning"></a>Aby poprawić to ostrzeżenie

1. Wybierz jedną z następujących opcji:

   - Zmiana platformy docelowej w projekcie **stron właściwości** okno dialogowe, tak aby jest późniejsza niż lub równa minimalnej wersję wszystkie zestawy referencyjne i projektów. Aby uzyskać więcej informacji, zobacz [Dodawanie odwołań do](../../ide/adding-references-in-visual-cpp-projects.md).

   - Usuń odwołanie do zestawu lub projektu, który ma minimalne framework w wersji, która jest nowsza niż docelową platformę framework. Te elementy zostaną oznaczone ikoną ostrzeżenia w projekcie **stron właściwości**.

## <a name="see-also"></a>Zobacz też

[Błędy i ostrzeżenia kompilowania projektu (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)