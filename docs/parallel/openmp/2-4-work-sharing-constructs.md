---
title: 2.4 Konstrukcje podziału pracy
ms.date: 11/04/2016
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
ms.openlocfilehash: e7bf8d37ecdc6a3ef451c9d9746fb47a76a16eb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502885"
---
# <a name="24-work-sharing-constructs"></a>2.4 Konstrukcje podziału pracy

Konstrukcji podziału pracy dystrybuuje wykonywania skojarzoną instrukcję wśród członków zespołu, napotykane go. Dyrektyw podziału pracy nie uruchamiaj nowe wątki, i nie bez problemu dorozumianych przy uruchamianiu konstrukcji podziału pracy.

Tworzy sekwencję podziału pracy i **barierę** dyrektywy napotkano musi być taka sama dla każdego wątku w zespole.

OpenMP definiuje następujące konstrukcje podziału pracy i te ustawienia zostały opisane w kolejnych sekcjach:

- **Aby uzyskać** — dyrektywa

- **sekcje** — dyrektywa

- **pojedynczy** — dyrektywa