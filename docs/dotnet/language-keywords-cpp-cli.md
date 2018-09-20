---
title: Słowa kluczowe języka (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keywords [C++]
ms.assetid: 021013b2-70ac-4df9-aa77-4af1c67a1a67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0b9deb25e203ea805b1430b2ec8e56f17a50123b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445441"
---
# <a name="language-keywords-ccli"></a>Słowa kluczowe języka (C++/CLI)

Kilka słów kluczowych języka zmieniła się z zarządzanych rozszerzeń dla C++ do Visual C++.

W nowej składni języka Visual C++ podwójnym podkreśleniem zostanie usunięty jako prefiksu z wszystkie słowa kluczowe (z jednym wyjątkiem: `__identifier` są zachowywane). Na przykład właściwość teraz jest zadeklarowany jako `property`, a nie `__property`.

Wprowadzono dwie główne przyczyny przy użyciu prefiksu podwójnego podkreślenia w zarządzanych rozszerzeń:

- Jest to metoda zgodna metodą rozszerzenia lokalne ze standardem ISO C++. Podstawowym celem projektu zarządzanych rozszerzeń było nie wprowadzają niezgodności z językiem standardowych, takich jak nowych słów kluczowych i tokenów. W dużej mierze, który uzasadnione wybór wskaźnika Składnia deklaracji obiektów typów zarządzana dokumentacja dotycząca było z tego powodu.

- Użycie podwójnego podkreślenia, niezależnie od jego aspekt zgodność jest również uzasadnione gwarancji jest nieinwazyjna przy użyciu istniejącej bazy kodu użytkowników języka. Jest to drugi podstawowym celem projektu zarządzanych rozszerzeń.

Pomimo usunięcia podwójnego podkreślenia, Microsoft nadal jest zaangażowana jest zgodna. Jednak pomoc techniczna dotycząca modelu obiektów dynamicznych CLR reprezentuje nowe i zaawansowane paradygmat programowania. Obsługa tego nowego modelu wymaga własnej wysokiego poziomu słów kluczowych i tokenów. Firma Microsoft próbowały zapewnia najwyższej jakości wyrażenia tego nowego modelu, integrując je i Obsługa standardowego języka. Nowy projekt składni zapewnia najwyższej klasy środowisko programistyczne, te dwa modele różnych obiektów.

Podobnie jesteśmy zaniepokojona maksymalizując nieinwazyjna charakter tych nowych słów kluczowych języka. Ma to zostało zrobione przy użyciu słów kluczowych kontekstowych jak i rozmieszczonych w odległości. Zanim przyjrzymy się rzeczywiste nowej składni języka, spróbujmy sensu tych dwóch wersjach w odpowiedzi specjalne — słowo kluczowe.

Kontekstowe słowo kluczowe ma specjalne znaczenie w kontekstach określonego programu. W ramach programu ogólne, na przykład `sealed` jest traktowany jako zwykłe identyfikatora. Jednak po jego wystąpieniu w ramach części deklaracji typu klasy zarządzane odniesienia jest traktowany jako słowo kluczowe w kontekście tej deklaracji klasy. W ten sposób można potencjalny wpływ inwazyjne coś wprowadzenia nowych słów kluczowych w języku, który uważamy, że jest bardzo ważne dla użytkowników z istniejącej bazy kodu. W tym samym czasie pozwala użytkownikom nowe funkcje najwyższej jakości środowisko funkcji dodatkowych języków - coś, co nie było możliwe z zarządzanych rozszerzeń. Na przykład jak `sealed` jest używany zobacz [deklaracja zarządzanego typu klasy](../dotnet/declaration-of-a-managed-class-type.md).

Odstępy między słowem kluczowym, takich jak `value class`, stanowią specjalny przypadek kontekstowego słowa kluczowego. Istniejącego słowa kluczowego go pary za pomocą modyfikatora kontekstowych, rozdzielonych spacją. Pary jest traktowany jako pojedynczą jednostkę, a nie jako dwa osobne słowa kluczowe.

## <a name="see-also"></a>Zobacz też

[Podręcznik migracji C++/CLI](../dotnet/cpp-cli-migration-primer.md)<br/>
[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)