---
title: Typy wartości i ich zachowania (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- value types
ms.assetid: 5cb872a6-1e0a-429d-853d-df4ab47e8f2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4d2d980e48a6f948c35faf0c4e42969795ef8dc7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404660"
---
# <a name="value-types-and-their-behaviors-ccli"></a>Typy wartości i ich zachowania (C++/CLI)

Typy wartości zostały zmienione na różne sposoby z zarządzanych rozszerzeń języka C++ do Visual C++. W tej sekcji przyjrzymy się typ wyliczenia CLR i wartości typu klasy, wraz z przyjrzeć się pakowanie i dostęp do wystąpienia spakowany w stosie CLR, a także poznać wskaźników wnętrza i przypinania. Wprowadzono zmiany rozbudowane języka w tym obszarze.

## <a name="in-this-section"></a>W tej sekcji

[Typ wyliczenia CLR](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
W tym artykule omówiono zmiany w deklaracji i zachowaniem typów wyliczeniowych.

[Niejawna konwersja boxing typów wartości](../dotnet/implicit-boxing-of-value-types.md)<br/>
W tym artykule omówiono motywacji niejawna konwersja boxing typów wartości i wynikające z niego zmiany w zachowaniu.

[Śledzenie dojścia do wartości spakowanej](../dotnet/a-tracking-handle-to-a-boxed-value.md)<br/>
W tym artykule omówiono sposób niejawnej konwersji boxing wartości typów przekłada się na śledzenie dojścia do wartości spakowanej obiektu.

[Semantyka typów wartości](../dotnet/value-type-semantics.md)<br/>
W tym artykule omówiono zmiany semantyka typów wartości, łącznie z dziedziczonych metod wirtualnych, konstruktory domyślne klas, wskaźników wnętrza i Unieruchamianie wskaźników.

## <a name="see-also"></a>Zobacz też

[Podręcznik migracji C++/CLI](../dotnet/cpp-cli-migration-primer.md)<br/>
[Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)