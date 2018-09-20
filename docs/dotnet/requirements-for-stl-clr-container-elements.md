---
title: Wymagania dotyczące elementów kontenera STL/CLR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C++ Standard Library, template class containers
- STL/CLR, containers
- containers, STL/CLR
- containers, C++ Standard Library
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fcba36fdf280cef31efb9a84288475fcbb82b291
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400430"
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