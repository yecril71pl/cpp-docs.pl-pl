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
ms.openlocfilehash: 113624b15a0c2c6062feb7113c4771fda6d6cf39
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384704"
---
# <a name="requirements-for-stlclr-container-elements"></a>Wymagania dotyczące elementów kontenera STL/CLR

Wszystkie typy odwołań, które są wstawiane do kontenerów STL/CLR musi mieć co najmniej następujące elementy:

- Konstruktor kopiujący publicznych.

- Operator przypisania publicznego.

- Destruktorem publicznym.

Ponadto kontenery asocjacyjne, takie jak [ustaw](../dotnet/set-stl-clr.md) i [mapy](../dotnet/map-stl-clr.md) musi mieć zdefiniowany publiczny operator porównania, która jest `operator<` domyślnie. Niektóre operacje na kontenerach również mogą wymagać publicznego konstruktora domyślnego i publicznego operatora równoważności należy zdefiniować.

Podobnie jak typy odwołań typów wartości i uchwytów, aby odwołać się do typów, które mają zostać wstawione w pojemniku asocjacyjnych musi mieć operator porównania takich jak `operator<` zdefiniowane. Wymagania dotyczące konstruktora kopiującego publicznych, operator przypisania publicznego i publicznego destruktora nie istnieją dla typów wartości lub obsługuje typy odwołań.

## <a name="see-also"></a>Zobacz także

[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
