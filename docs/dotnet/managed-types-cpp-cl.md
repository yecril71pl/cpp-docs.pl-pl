---
title: Zarządzane typy (C++ CL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __gc types
- types [C++], CLR
ms.assetid: 1ddd114e-be02-4de7-a4dd-a2d72ad8ff81
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 382228b9e8364d90d7929b4633744071c5eb0c77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408044"
---
# <a name="managed-types-ccl"></a>Typy zarządzane (C++/CL)

Składnia deklaracji typów zarządzanych i tworzenia i używania obiektów tego typu został znacząco zmieniony z zarządzanych rozszerzeń dla języka C++ do Visual C++. Stało się do wspierania ich integracji w systemie typu ISO C++. Te zmiany są przedstawione szczegółowo w następujących podsekcjach.

## <a name="in-this-section"></a>W tej sekcji

[Deklaracja zarządzanego typu klasy](../dotnet/declaration-of-a-managed-class-type.md)<br/>
W tym artykule omówiono sposób deklarowania zarządzanej `class`, `struct`, lub `interface`.

[Deklaracja obiektu klasy odwołania CLR](../dotnet/declaration-of-a-clr-reference-class-object.md)<br/>
W tym artykule omówiono sposób deklarowania obiektu typu klasy odwołania przy użyciu dojścia do śledzenia.

[Deklaracja tablicy CLR](../dotnet/declaration-of-a-clr-array.md)<br/>
Wyjaśnia sposób deklarowania i inicjowania tablicy.

[Zmiany w kolejności inicjowania konstruktorów](../dotnet/changes-in-constructor-initialization-order.md)<br/>
W tym artykule omówiono kluczowe zmiany w kolejności inicjowania konstruktorów w klasie.

[Zmiany w semantyce destruktora](../dotnet/changes-in-destructor-semantics.md)<br/>
W tym artykule omówiono finalizacja deterministyczna `Finalize` a `Dispose`, następstwa dla obiektów odniesienia i użycie jawnego `Finalize`.

**Uwaga:** omówienie delegatów jest odroczone do czasu [delegaci i zdarzenia](../dotnet/delegates-and-events.md) celu pokażesz mu składowych zdarzenia w obrębie klasy zawiera ogólnego [deklaracje składowych w obrębie klasy lub interfejsu (C + +/ CLI) ](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md).

## <a name="see-also"></a>Zobacz też

[Podręcznik migracji C++/CLI](../dotnet/cpp-cli-migration-primer.md)<br/>
[Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[Tablice](../windows/arrays-cpp-component-extensions.md)