---
title: 2.7 środowisko danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17c60c621defa15c034f57d0af8f14637db54f03
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378140"
---
# <a name="27-data-environment"></a>2.7 Środowisko danych

W tej sekcji przedstawiono dyrektywy i kilka klauzul do kontrolowania środowiska danych podczas wykonywania równoległego regionów, w następujący sposób:

- A **threadprivate** — dyrektywa (zobacz w poniższej sekcji) znajduje się zakres pliku, zakresie przestrzeni nazw lub zakresie bloku statyczne zmienne lokalne do wątku.

- Klauzule, które mogą być określone dla dyrektywy do kontrolowania udostępniania atrybutów zmienne w czasie trwania konstrukcje równoległego lub podziału pracy zostały opisane w [sekcji 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stronie 25.