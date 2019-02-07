---
title: Flaga kierunku
ms.date: 11/04/2016
f1_keywords:
- c.flags
helpviewer_keywords:
- direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
ms.openlocfilehash: e5177f206e46227fa693ef8d4bd1848b06374af7
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849909"
---
# <a name="direction-flag"></a>Flaga kierunku

Flaga kierunku jest specyficzne dla wszystkich procesorów CPU x86-zgodnego z Intel flagą procesora CPU. Ma to zastosowanie do wszystkich instrukcji zestawu, korzystających z przedstawiciela (powtórzeń) prefiksem, na przykład MOVS MOVSD, MOVSW i inne. Jeśli flaga kierunku jest wyczyszczone, zwiększa się adresy podane odpowiednie instrukcje.

Procedury czasu wykonywania C zakładają, że flaga kierunku jest wyczyszczone. Jeśli używane są inne funkcje za pomocą funkcji wykonawczej języka C, upewnij się, że innych funkcji pozostaw Flaga kierunku samodzielnie lub przywrócenia stanu. Oczekiwano Flaga kierunku się jasne po wejściu sprawia, że kod wykonywalny, szybsze i wydajniejsze.

Funkcje biblioteki C Run-Time, takich jak procedury manipulowania ciągami i manipulowanie buforem oczekiwać, że flaga kierunku, aby możliwy.

## <a name="see-also"></a>Zobacz też

[Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)
