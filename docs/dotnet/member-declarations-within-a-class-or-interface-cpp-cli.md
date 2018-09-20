---
title: Deklaracje składowych w obrębie klasy lub interfejsu (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- members, declaration syntax
- class members, declaration syntax
ms.assetid: 95d312a4-198b-46f0-b8f5-15253807c55e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 80b872b4c614677c05b0d28b821d3a48255905c5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430640"
---
# <a name="member-declarations-within-a-class-or-interface-ccli"></a>Deklaracje członków w obrębie klasy lub interfejsu (C++/CLI)

Deklaracja właściwości i operatory ma często przerobiona tak, z zarządzanych rozszerzeń języka C++ do Visual C++, ukrywanie podstawowe szczegóły implementacji, które zostały ujawnione w projekcie zarządzanych rozszerzeń. Deklaracje zdarzeń również zostały zmodyfikowane.

Do kategorii zmian, mają bez obsługi zarządzanych rozszerzeń konstruktory statyczne mogą teraz być zdefiniowana poza wierszem (oni musieli się zdefiniowano w tekście w ramach zarządzanych rozszerzeń) i pojęcie Konstruktor delegujący wprowadzono.

## <a name="in-this-section"></a>W tej sekcji

[Deklaracja właściwości](../dotnet/property-declaration.md)<br/>
W tym artykule omówiono zmiany deklaracje właściwości.

[Deklaracja indeksu właściwości](../dotnet/property-index-declaration.md)<br/>
W tym artykule omówiono zmiany deklaracje właściwości indeksowanych.

[Delegaci i zdarzenia](../dotnet/delegates-and-events.md)<br/>
W tym artykule omówiono zmiany składnia do deklarowania delegaci i zdarzenia.

[Pieczętowanie funkcji wirtualnej](../dotnet/sealing-a-virtual-function.md)<br/>
W tym artykule omówiono zmiany składnia pieczętowanie funkcji.

[Operatory przeciążone](../dotnet/overloaded-operators.md)<br/>
W tym artykule omówiono zmiany przeciążenia operatora.

[Zmiany operatorów konwersji](../dotnet/changes-to-conversion-operators.md)<br/>
W tym artykule omówiono zmiany operatorów konwersji.

[Jawne przesłanianie składowej interfejsu](../dotnet/explicit-override-of-an-interface-member.md)<br/>
W tym artykule omówiono zmiany do metody jawne przesłanianie składowej interfejsu.

[Prywatne funkcje wirtualne](../dotnet/private-virtual-functions.md)<br/>
W tym artykule omówiono zmiany w sposobie obsługi prywatne funkcje wirtualne w klasach pochodnych.

[Połączenie static const int nie jest już literałem](../dotnet/static-const-int-linkage-is-no-longer-literal.md)<br/>
Zawiera omówienie zmian w sposobie `static const` całkowitego elementy członkowskie są połączone oraz sposób jawny stałą, za pomocą nowego `literal` — słowo kluczowe.

## <a name="see-also"></a>Zobacz też

[Podręcznik migracji C++/CLI](../dotnet/cpp-cli-migration-primer.md)