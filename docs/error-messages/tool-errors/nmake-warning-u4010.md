---
title: Ostrzeżenie NMAKE U4010
ms.date: 11/04/2016
f1_keywords:
- U4010
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
ms.openlocfilehash: f68da1893eec6325ccccfd0e2e2dd0e612f28eb9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193137"
---
# <a name="nmake-warning-u4010"></a>Ostrzeżenie NMAKE U4010

"target": kompilacja nie powiodła się; Określono/k, kontynuowanie...

Polecenie w bloku poleceń dla danego elementu docelowego zwróciło niezerowy kod zakończenia. Opcja/K poinformowała NMAKE, aby kontynuować przetwarzanie niepowiązanych części kompilacji i wydać kod zakończenia 1 po zakończeniu sesji NMAKE.

Jeśli dany obiekt docelowy jest, zależny od innego elementu docelowego, NMAKE wystawia ostrzeżenie [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) po tym ostrzeżeniu.
