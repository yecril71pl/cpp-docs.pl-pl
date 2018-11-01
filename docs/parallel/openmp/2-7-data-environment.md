---
title: 2.7 Środowisko danych
ms.date: 11/04/2016
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
ms.openlocfilehash: b65dfc7d7694b36ef4f89351579cd73e07ab537c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491974"
---
# <a name="27-data-environment"></a>2.7 Środowisko danych

W tej sekcji przedstawiono dyrektywy i kilka klauzul do kontrolowania środowiska danych podczas wykonywania równoległego regionów, w następujący sposób:

- A **threadprivate** — dyrektywa (zobacz w poniższej sekcji) znajduje się zakres pliku, zakresie przestrzeni nazw lub zakresie bloku statyczne zmienne lokalne do wątku.

- Klauzule, które mogą być określone dla dyrektywy do kontrolowania udostępniania atrybutów zmienne w czasie trwania konstrukcje równoległego lub podziału pracy zostały opisane w [sekcji 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stronie 25.