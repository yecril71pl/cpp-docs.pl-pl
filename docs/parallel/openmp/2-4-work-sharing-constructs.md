---
title: 2.4 konstrukcje podziału pracy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 719b33698b708761f0cd56e65a70a6ea8fa3b053
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411121"
---
# <a name="24-work-sharing-constructs"></a>2.4 Konstrukcje podziału pracy

Konstrukcji podziału pracy dystrybuuje wykonywania skojarzoną instrukcję wśród członków zespołu, napotykane go. Dyrektyw podziału pracy nie uruchamiaj nowe wątki, i nie bez problemu dorozumianych przy uruchamianiu konstrukcji podziału pracy.

Tworzy sekwencję podziału pracy i **barierę** dyrektywy napotkano musi być taka sama dla każdego wątku w zespole.

OpenMP definiuje następujące konstrukcje podziału pracy i te ustawienia zostały opisane w kolejnych sekcjach:

- **Aby uzyskać** — dyrektywa

- **sekcje** — dyrektywa

- **pojedynczy** — dyrektywa