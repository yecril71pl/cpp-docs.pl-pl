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
ms.openlocfilehash: 523b3e8d3f9c04a933f37032fcea670d75dafccf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33162439"
---
# <a name="requirements-for-stlclr-container-elements"></a>Wymagania dotyczące elementów kontenera STL/CLR
Wszystkie typy odwołań, które są wstawiane do kontenery STL/CLR musi mieć co najmniej następujące elementy:  
  
-   Konstruktor kopiujący publicznego.  
  
-   Operator przypisania publicznego.  
  
-   Destruktorem publicznym.  
  
 Ponadto asocjacyjnej kontenerów, takich jak [ustawić](../dotnet/set-stl-clr.md) i [mapy](../dotnet/map-stl-clr.md) musi mieć operator porównania publiczne zdefiniowane, czyli `operator<` domyślnie. Niektóre operacje kontenerów może wymagać publicznego konstruktora domyślnego i operator publiczny równoważność ma zostać zdefiniowana.  
  
 Jak typów referencyjnych, typy wartości i uchwytów odwoływać się do typów, które mają zostać wstawione do kontenera asocjacyjnej musi mieć operator porównania takich jak `operator<` zdefiniowane. Wymagania dotyczące konstruktora kopiującego publiczne, operator przypisania publicznego i destruktorem publicznym nie istnieją dla typów wartości lub uchwytów typy referencyjne.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)