---
title: 2.6.1 opanować konstrukcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d82ae673e428c635172f35f9b0f682aa65dc2b8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445636"
---
# <a name="261-master-construct"></a>2.6.1 — konstrukcja główna

**Wzorca** dyrektywy identyfikuje konstrukcja, która określa ze strukturą blok, który jest wykonywany przez główny wątek zespołu. Składnia **wzorca** dyrektywy jest następująca:

```
#pragma omp master new-linestructured-block
```

Inne wątki w zespole nie wykonuj skojarzone ze strukturalnego bloku. Bez problemu dorozumianych na wpis do lub wyjście z konstrukcja master nie istnieje.