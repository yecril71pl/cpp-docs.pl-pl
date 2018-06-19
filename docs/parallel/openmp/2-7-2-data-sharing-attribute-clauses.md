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
ms.openlocfilehash: ecc6efac6e3d7356e51dc0ec57009ca9e5a71890
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691911"
---
# <a name="272-data-sharing-attribute-clauses"></a>2.7.2 Klauzule atrybutu udostępniania danych
Kilka dyrektyw zaakceptować klauzule, które umożliwiają użytkownikom kontrolowanie udostępniania atrybutów zmienne w czasie trwania regionu. Klauzule atrybutu udostępniania mają zastosowanie tylko do zmiennych w zakresie leksykalne dyrektywy, na której znajduje się klauzuli. Nie wszystkie z poniższych klauzul są dozwolone w wszystkie dyrektywy. Lista klauzule, które są prawidłowe w szczególności dyrektywy opisano z dyrektywą.  
  
 Jeśli zmienna jest widoczny, gdy równoległego lub napotkano konstrukcji podziału pracy, a zmienna nie została określona w klauzuli udostępniania atrybutu lub **threadprivate** dyrektywy, następnie zmienna jest udostępniony. Zmienne statyczne zadeklarowany w ramach równoległego regionu zakres dynamiczny są udostępnione. Przydzielonej pamięci sterty (na przykład za pomocą **malloc()** C lub C++ lub **nowe** operatora w języku C++) są udostępniane. (Wskaźnik pamięci, jednak może być prywatne lub współużytkowane.) Zmienne z automatycznym okresem magazynu zadeklarowaną w ramach równoległego regionu zakres dynamiczny są prywatne.  
  
 Większość klauzule zaakceptować *zmiennej listy* argumentu, który jest rozdzielaną przecinkami listę zmiennych, które są widoczne. Jeśli zmienna przywoływany w klauzuli udostępniania danych atrybutu ma typ tworzony na podstawie szablonu i istnieją nie inne odwołania do tej zmiennej w programie, zachowanie jest niezdefiniowany.  
  
 Wszystkie zmienne, które są wyświetlane w klauzulach dyrektywy musi być widoczny. Klauzule może się powtarzać, zgodnie z potrzebami, ale nie zmienna może zostać określona w więcej niż jedną klauzulę z tą różnicą, że zmienna można określić zarówno **firstprivate** i **lastprivate** klauzuli.  
  
 W poniższych sekcjach opisano klauzule atrybutu udostępniania danych:  
  
-   **prywatne**, [sekcji 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stronie 25.  
  
-   **firstprivate**, [sekcji 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) na stronie 26.  
  
-   **lastprivate**, [sekcji 2.7.2.3 ostatnia](../../parallel/openmp/2-7-2-3-lastprivate.md) na stronie 27.  
  
-   **udostępniony**, [sekcji 2.7.2.4](../../parallel/openmp/2-7-2-4-shared.md) na stronie 27.  
  
-   **domyślne**, [sekcji 2.7.2.5](../../parallel/openmp/2-7-2-5-default.md) na stronie 28.  
  
-   **redukcja**, [sekcji 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md) na stronie 28.  
  
-   **copyin**, [sekcji 2.7.2.7](../../parallel/openmp/2-7-2-7-copyin.md) na stronie 31.  
  
-   **copyprivate**, [sekcji 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) na stronie 32.