---
title: Ostrzeżenie LNK4020 narzędzi konsolidatora
ms.date: 05/29/2018
f1_keywords:
- LNK4020
helpviewer_keywords:
- LNK4020
ms.openlocfilehash: 7810fd9a97a8f6e22ad362819a024358a9f4b07c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609745"
---
# <a name="linker-tools-warning-lnk4020"></a>Ostrzeżenie LNK4020 narzędzi konsolidatora

> rekord typu w elemencie "*filename*" jest uszkodzony; niektóre symbole i typy mogą być niedostępne z debugera

Plik PDB *filename* został uszkodzony typu rekordu.

Ten problem jest często pomocniczego do innych problemów z kompilacją; chyba że jest to pierwszy problemu zgłoszonego kompilacji, przeciwdziałania inne błędy i ostrzeżenia pierwszy. Jeśli jest to pierwszy zgłoszonego problemu, może być konieczne czyszczenie katalogów kompilacji i ponownie skompiluj projekt. Jeśli używasz procesów kompilacji równoległych, zobacz, jeśli błąd się powtarza, podczas kompilacji.