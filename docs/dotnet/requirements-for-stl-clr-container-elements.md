---
title: "Wymagania dotyczące elementów kontenera STL/CLR | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- C++ Standard Library, template class containers
- STL/CLR, containers
- containers, STL/CLR
- containers, C++ Standard Library
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3317e3c9349963fc24b37b421def05c475732fd8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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