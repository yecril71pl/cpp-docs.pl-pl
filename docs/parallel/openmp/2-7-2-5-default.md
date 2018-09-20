---
title: 2.7.2.5 domyślne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 047110fe80d15d0ff3d979eeec8abf3e42dc35f1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401566"
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