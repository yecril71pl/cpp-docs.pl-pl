---
title: "Zarządzane typów (C++-CL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __gc types
- types [C++], CLR
ms.assetid: 1ddd114e-be02-4de7-a4dd-a2d72ad8ff81
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9e7bbd9687c3cc696b35e0284d55a18f59c898cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="managed-types-ccl"></a>Typy zarządzane (C++/CL)
Składnia deklaracji typy zarządzane i tworzenia i stosowania obiekty z następujących typów znacznie zmieniono z rozszerzeń zarządzanych dla języka C++ dla Visual C++. To zostało zrobione wspierania integracji ich w systemie typów ISO C++. Te zmiany są przedstawione szczegółowo w poniższych podsekcjach.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Deklaracja zarządzanego typu klasy](../dotnet/declaration-of-a-managed-class-type.md)  
 W tym artykule omówiono sposób zadeklarować zarządzanego `class`, `struct`, lub `interface`.  
  
 [Deklaracja obiektu klasy odwołania CLR](../dotnet/declaration-of-a-clr-reference-class-object.md)  
 Omówiono sposób deklaruje odwołanie do obiektu typu klasy przy użyciu dojścia do śledzenia.  
  
 [Deklaracja tablicy CLR](../dotnet/declaration-of-a-clr-array.md)  
 Wyjaśniono, jak deklarowanie i zainicjowania tablicy.  
  
 [Zmiany w kolejności inicjowania konstruktorów](../dotnet/changes-in-constructor-initialization-order.md)  
 W tym artykule omówiono zmiany klucza w kolejności inicjowania konstruktorów klasy.  
  
 [Zmiany w semantyce destruktora](../dotnet/changes-in-destructor-semantics.md)  
 W tym artykule omówiono deterministyczna finalizacji `Finalize` i `Dispose`, konsekwencje obiektów odniesienia i stosowania jawnego `Finalize`.  
  
 **Uwaga:** dyskusji obiektów delegowanych jest odroczona do [delegaci i zdarzenia](../dotnet/delegates-and-events.md) w celu przedstawienia ich z członków zdarzenia w klasie temat ogólny z [deklaracje członków w obrębie klasy lub interfejsu (C + +/ CLI) ](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md).  
  
## <a name="see-also"></a>Zobacz też  
 [C + +/ CLI Elementarz migracji](../dotnet/cpp-cli-migration-primer.md)   
 [Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)   
 [Tablice](../windows/arrays-cpp-component-extensions.md)