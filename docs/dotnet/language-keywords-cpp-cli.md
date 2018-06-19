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
ms.openlocfilehash: 241205ad25314034d8d36fa7ad1b156b13080fd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33134416"
---
# <a name="language-keywords-ccli"></a>Słowa kluczowe języka (C++/CLI)
Kilka słów kluczowych języka zmieniła się z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 W nowej składni Visual C++, podkreślenie podwójne zostanie usunięty jako prefiksu z wszystkie słowa kluczowe (z jednym wyjątkiem: `__identifier` jest zachowywana). Na przykład właściwość teraz jest zadeklarowany jako `property`, a nie `__property`.  
  
 Wystąpiły dwóch głównych powodów przemawiających za przy użyciu prefiksu o podwójnej precyzji podkreślenia w zarządzanych rozszerzeń:  
  
-   Jest to metoda zgodność zapewnienia lokalnego rozszerzenia standardowe ISO C++. Podstawowym celem projektu rozszerzeń zarządzanych było nie wprowadzają niezgodności z językiem standardowe, takie jak nowych słów kluczowych i tokenów. Z tego powodu było w dużej mierze, który dokonywanie wyboru wskaźnika składnia dla deklaracji obiekty zarządzane odniesienia typów.  
  
-   Użycie podwójnego podkreślenia, oprócz jego aspekt zgodność jest również rozsądną gwarancję jest nieinwazyjna z istniejącą bazą kodu użytkowników języka. Jest to drugi podstawowym celem projektu rozszerzeń zarządzanych.  
  
 Mimo usuwania podwójnego podkreślenia, Microsoft pozostaje starań, aby trwa zgodność. Jednak obsługa nowych i zaawansowanego modelu programowania reprezentuje model obiektów dynamicznych CLR. Obsługa tego nowego modelu wymaga własnego wysokiego poziomu słów kluczowych i tokenów. Firma Microsoft próbowały zapewnienia najwyższej jakości wyrażenia tego nowego modelu podczas integracji go i obsługujące standard języka. Nowy projekt składni zapewnia pierwszej klasie obsługę programowania tych dwóch różnych obiektów modeli.  
  
 Podobnie możemy związane z maksymalizacja nieinwazyjna natury tych nowych słów kluczowych języka. Ma to osiągnąć, przy użyciu słów kluczowych kontekstowe i rozmieszczonych w odległości. Zanim przyjrzymy rzeczywiste nowej składni języka spróbujmy rozsądnie tych dwóch odmian specjalnych słów kluczowych.  
  
 Kontekstowe słowo kluczowe ma specjalne znaczenie w kontekstach określonego programu. W ramach programu ogólne, na przykład `sealed` jest traktowany jako identyfikator zwykłej. Jednak jeśli występuje on w części deklaracji typu klasy zarządzane odniesienia, jest traktowany jako słowo kluczowe w kontekście tej deklaracji klasy. Pozwala to zmniejszyć potencjalny wpływ inwazyjne coś wprowadzenia nowych słów kluczowych w języku, który uważamy, jest bardzo ważne, aby użytkownicy z istniejącego kodu podstawowej. W tym samym czasie pozwala użytkownikom nowych funkcji ma najwyższej jakości środowisko funkcji dodatkowych języków - coś, której nie przy użyciu rozszerzeń zarządzanych. Na przykład jak `sealed` służy zobacz [deklaracji typu klasy zarządzane](../dotnet/declaration-of-a-managed-class-type.md).  
  
 Odstępy między słowem kluczowym, takich jak `value class`, jest specjalny przypadek kontekstowe słowo kluczowe. Istniejącego słowa kluczowego go pary modyfikatorem kontekstowe rozdzielonych spacją. Para jest traktowany jako pojedyncza jednostka, a nie jako dwa osobne słowa kluczowe.  
  
## <a name="see-also"></a>Zobacz też  
 [C + +/ CLI Elementarz migracji](../dotnet/cpp-cli-migration-primer.md)   
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)