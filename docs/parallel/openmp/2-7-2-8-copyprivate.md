---
title: 2.7.2.8 — prywatna kopia
ms.date: 11/04/2016
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
ms.openlocfilehash: d4df1b4216014d3cd15be1480d2f83334fddb72d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622914"
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