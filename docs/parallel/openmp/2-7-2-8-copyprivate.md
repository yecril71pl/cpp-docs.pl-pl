---
title: 2.7.2.8 — prywatna | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6815afe12344f94ed33d6b9260472f3e29eb72a0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406363"
---
# <a name="2728-copyprivate"></a>2.7.2.8 — prywatna kopia

**Copyprivate** klauzuli udostępnia mechanizm do zmiennej prywatnej umożliwia emitowanie wartości z jednego członka zespołu do innych członków. Jest to alternatywa dla użycia w udostępnionej zmiennej wartości, gdy dostarczanie w udostępnionej zmiennej może sprawiać trudności (na przykład w rekursji, wymagających inną zmienną na każdym poziomie). **Copyprivate** klauzuli może się pojawić tylko **pojedynczego** dyrektywy.

Składnia **copyprivate** klauzula jest w następujący sposób:

```

copyprivate(
variable-list
)

```

Efekt **copyprivate** klauzuli zmiennych na swojej liście zmiennych występuje po wykonaniu strukturalnego bloku skojarzone z **pojedynczego** konstruowania i przed jakąkolwiek wątki zespół pozostało barierę na końcu konstrukcja. Następnie w innych wątków w zespole, dla każdej zmiennej w *liście zmiennych*, zmienna staje się definicją (tak, jakby przypisanie) z wartością odpowiadającego zmiennej w wątku, który jest wykonywany konstrukcja użytkownika ze strukturą blok.

Ograniczenia **copyprivate** klauzuli są następujące:

- Zmienna, która została określona w **copyprivate** klauzuli nie musi znajdować się w **prywatnej** lub **firstprivate** klauzulę dla tego samego **pojedynczego**dyrektywy.

- Jeśli **pojedynczego** dyrektywy z **copyprivate** klauzuli napotkaniu dynamicznego zakresu równoległego regionu, wszystkie zmienne określone w **copyprivate** musi mieć klauzulę prywatny w otaczającym kontekście.

- Zmienna, która została określona w **copyprivate** klauzula musi mieć operatora przypisania kopiowania jednoznaczną dostępne.