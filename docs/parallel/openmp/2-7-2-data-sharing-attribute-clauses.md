---
title: 2.7.2 klauzule atrybutu udostępniania danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 47347d3c-18bd-441f-99cf-7737564c417f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b8c53cace8d50f10fe638ea8604c46e457f69ee
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392530"
---
# <a name="272-data-sharing-attribute-clauses"></a>2.7.2 Klauzule atrybutu udostępniania danych

Kilka dyrektyw zaakceptować klauzul, które umożliwiają użytkownikowi na kontrolowanie udostępniania atrybutów zmienne w czasie trwania regionu. Klauzule atrybutu udostępniania dotyczą tylko zmienne w zakresie leksykalnym dyrektywy, na której znajduje się klauzuli. Nie wszystkie z następujących klauzul są dozwolone dla wszystkich dyrektyw. Lista klauzul, które są ważne w szczególności dyrektywy są opisane za pomocą dyrektywy.

Jeśli zmienna jest widoczna, gdy równoległego lub konstrukcji podziału pracy zostanie osiągnięty, a zmienna nie została określona w klauzuli udostępniania atrybutu lub **threadprivate** dyrektywy, następnie zmienna jest udostępniony. Statyczne zmienne zadeklarowane wewnątrz zakresu dynamicznego równoległego regionu są udostępnione. Sterty przydzielonej pamięci (na przykład za pomocą **malloc()** w języku C lub C++ lub **nowe** operatora w języku C++) jest udostępniony. (Wskaźnik pamięci, jednak może być prywatne lub udostępniony.) Zmienne z automatycznym okresem magazynu zadeklarowaną w ramach zakresu dynamicznego równoległego regionu są prywatne.

Zaakceptuj większość klauzul *liście zmiennych* argumentu, który znajduje się lista rozdzielonych przecinkami zmiennych, które są widoczne. Jeśli zmienna do której odwołuje się klauzulą atrybutu udostępniania danych ma typ pochodzący od szablonu i istnieją nie inne odwołania do tej zmiennej w programie, zachowanie jest niezdefiniowane.

Wszystkie zmienne, które są wyświetlane w klauzulach dyrektywy muszą być widoczne. Klauzule może być powtarzany zgodnie z potrzebami, ale zmiennej nie może być określone w więcej niż jedną klauzulę, z tą różnicą, że zmienna może być określony w obu **firstprivate** i **lastprivate** klauzuli.

W poniższych sekcjach opisano klauzule atrybutu udostępniania danych:

- **prywatne**, [sekcji 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stronie 25.

- **firstprivate**, [sekcji 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) na stronie 26.

- **lastprivate**, [2.7.2.3 ostatnia sekcja](../../parallel/openmp/2-7-2-3-lastprivate.md) na stronie 27.

- **udostępnione**, [sekcji 2.7.2.4](../../parallel/openmp/2-7-2-4-shared.md) na stronie 27.

- **domyślne**, [sekcji 2.7.2.5](../../parallel/openmp/2-7-2-5-default.md) na stronie 28.

- **redukcja**, [sekcji 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md) na stronie 28.

- **copyin**, [sekcji 2.7.2.7](../../parallel/openmp/2-7-2-7-copyin.md) na stronie 31.

- **copyprivate**, [sekcji 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) na stronie 32.