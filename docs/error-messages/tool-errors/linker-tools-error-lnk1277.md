---
title: Błąd narzędzi konsolidatora LNK1277
ms.date: 11/04/2016
f1_keywords:
- LNK1277
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
ms.openlocfilehash: 137aa15dd9dad4b08d52af55da60a9cdf8b58055
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160552"
---
# <a name="linker-tools-error-lnk1277"></a>Błąd narzędzi konsolidatora LNK1277

Obiekt nie odnaleziono rekordu w pliku pgd (nazwa_pliku)

Korzystając z [/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), ścieżka pliki wejściowe lib, def lub .obj różnił się od ścieżki, na którym zostały znalezione podczas pginstrument. Po pginstrument to może wyjaśnić przez zmianę w zmiennej środowiskowej LIB. Pełna ścieżka do plików wejściowych jest przechowywany w pliku .pgd.

/LTCG:PGOPTIMIZE wymaga taka sama jak faza pginstrument dane wejściowe.

Aby rozwiązać tego ostrzeżenia, wykonaj jedną z następujących czynności:

- Uruchom pginstrument, wykonaj ponownie wszystkie przebiegi testowe i uruchom /LTCG:PGOPTIMIZE.

- Jakie były po uruchomieniu pginstrument, należy zmienić zmiennej środowiskowej LIB.

Nie zaleca się, że obejść LNK1277 przy użyciu /LTCG:PGUPDATE.