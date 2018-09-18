---
title: Błąd narzędzi konsolidatora LNK1277 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1277
dev_langs:
- C++
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 542c48bd23b3f84ab301404987c77d964f51823e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082539"
---
# <a name="linker-tools-error-lnk1277"></a>Błąd narzędzi konsolidatora LNK1277

Obiekt nie odnaleziono rekordu w pliku pgd (nazwa_pliku)

Korzystając z [/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), ścieżka pliki wejściowe lib, def lub .obj różnił się od ścieżki, na którym zostały znalezione podczas pginstrument. Po pginstrument to może wyjaśnić przez zmianę w zmiennej środowiskowej LIB. Pełna ścieżka do plików wejściowych jest przechowywany w pliku .pgd.

/LTCG:PGOPTIMIZE wymaga taka sama jak faza pginstrument dane wejściowe.

Aby rozwiązać tego ostrzeżenia, wykonaj jedną z następujących czynności:

- Uruchom pginstrument, wykonaj ponownie wszystkie przebiegi testowe i uruchom /LTCG:PGOPTIMIZE.

- Jakie były po uruchomieniu pginstrument, należy zmienić zmiennej środowiskowej LIB.

Nie zaleca się, że obejść LNK1277 przy użyciu /LTCG:PGUPDATE.