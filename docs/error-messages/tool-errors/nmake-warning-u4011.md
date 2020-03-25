---
title: Ostrzeżenie NMAKE U4011
ms.date: 11/04/2016
f1_keywords:
- U4011
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
ms.openlocfilehash: 6b1701ffc83f849d2482bd14b25d65c04c496899
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193150"
---
# <a name="nmake-warning-u4011"></a>Ostrzeżenie NMAKE U4011

"target": nie wszystkie elementy zależne są dostępne; obiekt docelowy nie został skompilowany

Zależna od danego elementu docelowego nie istniała lub była nieaktualna, a polecenie aktualizacji elementu zależnego zwróciło niezerowy kod zakończenia. Opcja/K poinformowała NMAKE, aby kontynuować przetwarzanie niepowiązanych części kompilacji i wydać kod zakończenia 1 po zakończeniu sesji NMAKE.

To ostrzeżenie jest poprzedzone ostrzeżeniem [U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) dla każdego elementu zależnego, który nie został utworzony ani zaktualizowany.
