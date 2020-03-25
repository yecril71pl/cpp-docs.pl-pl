---
title: Ostrzeżenie narzędzi konsolidatora LNK4020
ms.date: 05/29/2018
f1_keywords:
- LNK4020
helpviewer_keywords:
- LNK4020
ms.openlocfilehash: e818909cc0b590b0f7727846cfd7b469e8bc0e3f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194229"
---
# <a name="linker-tools-warning-lnk4020"></a>Ostrzeżenie narzędzi konsolidatora LNK4020

> rekord typu w pliku "*filename*" jest uszkodzony; Niektóre symbole i typy mogą być niedostępne z debugera

*Nazwa* pliku PDB ma uszkodzony rekord typu.

Ten problem jest często pomocniczy dla innych problemów z kompilacją; o ile nie jest to pierwszy zgłoszony problem kompilacji, najpierw należy zająć się innymi błędami i ostrzeżeniami. Jeśli jest to pierwszy zgłoszony problem, może być konieczne wyczyszczenie katalogów kompilacji i ponowne skompilowanie projektu. Jeśli używasz równoległych procesów kompilacji, zobacz, czy błąd będzie nadal występować podczas serializacji kompilacji.
