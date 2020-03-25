---
title: Ostrzeżenie PRJ0049 dotyczące kompilacji projektu
ms.date: 11/04/2016
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
ms.openlocfilehash: e857a50215dc7516c0e2ec45a97638c76f40f43b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191756"
---
# <a name="project-build-warning-prj0049"></a>Ostrzeżenie PRJ0049 dotyczące kompilacji projektu

Przywoływany element docelowy "\<Reference >" wymaga .NET Framework \<MinFrameworkVersion > i nie zostanie uruchomiony na platformie docelowej tego projektu

Aplikacje utworzone za pomocą programu Visual Studio 2008 mogą określić, która wersja .NET Framework powinna być docelowa. W przypadku dodania odwołania do zestawu lub projektu, który zależy od wersji .NET Framework, która jest nowsza niż wersja domowa, to ostrzeżenie zostanie wyświetlone w czasie kompilacji.

### <a name="to-correct-this-warning"></a>Aby poprawić to ostrzeżenie

1. Wybierz jedną z następujących opcji:

   - Zmień platformę dostosowanej w oknie dialogowym **strony właściwości** projektu, tak aby była nowsza lub równa minimalnej wersji platformy wszystkich zestawów i projektów, do których istnieją odwołania. Aby uzyskać więcej informacji, zobacz [Dodawanie odwołań](../../build/adding-references-in-visual-cpp-projects.md).

   - Usuń odwołanie do zestawu lub projektu o minimalnej wersji platformy, która jest nowsza niż platforma domowa. Te elementy zostaną oznaczone ikoną ostrzeżenia na **stronach właściwości**projektu.

## <a name="see-also"></a>Zobacz też

[Błędy i ostrzeżenia kompilowania projektu (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
