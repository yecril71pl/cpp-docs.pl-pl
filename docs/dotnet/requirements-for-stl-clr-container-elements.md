---
title: Wymagania dotyczące elementów kontenera STL/CLR
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- C++ Standard Library, template class containers
- STL/CLR, containers
- containers, STL/CLR
- containers, C++ Standard Library
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
ms.openlocfilehash: 0744d38a08dbd972b786e1cc74c112322ecf181f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428577"
---
# <a name="requirements-for-stlclr-container-elements"></a>Wymagania dotyczące elementów kontenera STL/CLR

Wszystkie typy odwołań, które są wstawiane do kontenerów STL/CLR musi mieć co najmniej następujące elementy:

- Konstruktor kopiujący publicznych.

- Operator przypisania publicznego.

- Destruktorem publicznym.

Ponadto kontenery asocjacyjne, takie jak [ustaw](../dotnet/set-stl-clr.md) i [mapy](../dotnet/map-stl-clr.md) musi mieć zdefiniowany publiczny operator porównania, która jest `operator<` domyślnie. Niektóre operacje na kontenerach również mogą wymagać publicznego konstruktora domyślnego i publicznego operatora równoważności należy zdefiniować.

Podobnie jak typy odwołań typów wartości i uchwytów, aby odwołać się do typów, które mają zostać wstawione w pojemniku asocjacyjnych musi mieć operator porównania takich jak `operator<` zdefiniowane. Wymagania dotyczące konstruktora kopiującego publicznych, operator przypisania publicznego i publicznego destruktora nie istnieją dla typów wartości lub obsługuje typy odwołań.

## <a name="see-also"></a>Zobacz też

[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)