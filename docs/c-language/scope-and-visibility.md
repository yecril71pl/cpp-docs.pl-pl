---
title: Zakres i widoczność
ms.date: 11/04/2016
helpviewer_keywords:
- scope, levels
- visibility
- file scope [C++]
ms.assetid: a019eb7c-66ed-46a7-bc9f-89a963930a56
ms.openlocfilehash: 4010025a5a80fa513c8f86c41612350b2a23c15e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656732"
---
# <a name="scope-and-visibility"></a>Zakres i widoczność

„Widoczność” identyfikatora określa części programu, w których można się do niego odwoływać (jego „zakres”). Identyfikator jest widoczny (tzn. może zostać użyty) tylko w częściach programu wchodzących w skład jego „zakresu”, który może być ograniczony (w celu zwiększenia restrykcyjności) do pliku, funkcji, bloku lub prototypu funkcji, w którym występuje. Zakres identyfikatora jest częścią programu, w której może być używana nazwa. Jest to czasami nazywane „zakresem słownikowym”. Istnieją cztery rodzaje zakresów: funkcji, pliku, bloku i prototypu funkcji.

Wszystkie identyfikatory z wyjątkiem etykiet mają zakres uzależniony od poziomu, na którym występuje deklaracja. Dla każdego rodzaju zakresu, widocznością identyfikatorów w programie rządzą następujące zasady:

Zakres pliku deklarator lub Specyfikator typu dla identyfikatora z zakresem pliku pojawia się poza każdym blokiem lub listą parametrów i jest dostępny z dowolnego miejsca w jednostce translacji po jej deklaracji. Nazwy identyfikatorów z zakresem pliku są często nazywane „global” lub „external”. Zakres globalnego identyfikatora rozpoczyna się w miejscu jego definicji lub deklaracji i kończy się na końcu jednostki translacji.

Etykieta zakresu A funkcji jest jedynym rodzajem identyfikatora, który ma zakres funkcji. Etykieta jest niejawnie zadeklarowana przez jej użycie w instrukcji. Nazwy etykiet muszą być unikatowe w obrębie danej funkcji. (Aby uzyskać więcej informacji dotyczących etykiet i nazw etykiet, zobacz [goto i Labeled — instrukcje](../c-language/goto-and-labeled-statements-c.md).)

Zakres bloku, który deklarator lub Specyfikator typu dla identyfikatora z zakresem bloku pojawia się wewnątrz bloku lub listy deklaracji parametrów formalnych w definicji funkcji. Jest widoczny tylko od punktu jego deklaracji lub definicji do końca bloku, zawierającego jego deklarację lub definicję. Jej zakres jest ograniczony do tego bloku i wszelkich bloków zagnieżdżonych w tym bloku i kończy się nawiasem klamrowym, który zamyka skojarzony blok. Takie identyfikatory są czasami nazywane „zmiennymi lokalnymi”.

Zakres prototypu funkcji deklarator lub Specyfikator typu dla identyfikatora z zakresem prototypu funkcji pojawia się w obrębie listy deklaracji parametrów prototypu funkcji (nie jest częścią deklaracji funkcji). Jej zakres kończy się z końcem deklaratora funkcji.

Właściwe deklaracje do tworzenia zmiennych widocznych w innych plikach źródłowych są opisane w [klasy magazynu](../c-language/c-storage-classes.md). Jednakże, zmienne i funkcje zadeklarowane na zewnętrznym poziomie ze **statyczne** Specyfikator klasy magazynowania są widoczne tylko w pliku źródłowym, w której są zdefiniowane. Wszystkie pozostałe funkcje są widoczne globalnie.

## <a name="see-also"></a>Zobacz też

[Okres istnienia, zakres, widoczność i połączenie](../c-language/lifetime-scope-visibility-and-linkage.md)