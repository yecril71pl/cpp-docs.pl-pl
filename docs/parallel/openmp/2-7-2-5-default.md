---
title: 2.7.2.5 — domyślne
ms.date: 11/04/2016
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
ms.openlocfilehash: efb10913b74ebfae37c95d057955c87bdcfca9a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580248"
---
# <a name="2725-default"></a>2.7.2.5 — domyślne

**Domyślne** klauzuli umożliwia użytkownikowi mają wpływ na atrybuty udostępnianie danych zmiennych. Składnia **domyślne** klauzula jest w następujący sposób:

```
default(shared | none)
```

Określanie **default(shared)** jest odpowiednikiem jawnego określania każdej zmiennej aktualnie widoczne w **udostępnionego** klauzuli, chyba że jest to **threadprivate** lub **cons**`t`-kwalifikowaną. W przypadku braku jawnego **domyślne** klauzuli, zachowanie domyślne jest taka sama jak if **default(shared)** zostały określone.

Określanie **default(none)** wymaga, że co najmniej jedną z następujących muszą być spełnione dla każdego odwołania do zmiennej w zakresie leksykalnym konstrukcja równoległa:

- Zmienna jawnie znajduje się w konstrukcji, która zawiera odwołanie do klauzuli atrybutu udostępniania danych.

- Ta zmienna została zgłoszona w ramach równoległego konstrukcji.

- Zmienna jest **threadprivate**.

- Zmienna posiada **const**-kwalifikowaną typu.

- Zmienna jest zmienna sterująca pętli for **dla** pętli, który poprzedza **dla** lub **równoległe w** dyrektywy i odwołanie do zmiennej pojawia się wewnątrz pętli .

Określenie zmiennej na **firstprivate**, **lastprivate**, lub **redukcji** klauzuli ujęty dyrektywy powoduje niejawne odwołanie do zmiennej w załączonym kontekst. Takie odwołań niejawnych są również w zależności od wymagań wymienionych powyżej.

Tylko jeden **domyślne** klauzuli mogą być określone dla **równoległe** dyrektywy.

Zmienna domyślnego atrybutu udostępniania danych, można zastąpić przy użyciu **prywatnej**, **firstprivate**, **lastprivate**, **redukcji**, i **udostępnionego** zdań, jak pokazano na poniższym przykładzie:

```
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```