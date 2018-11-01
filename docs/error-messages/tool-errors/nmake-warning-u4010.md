---
title: Ostrzeżenie NMAKE U4010
ms.date: 11/04/2016
f1_keywords:
- U4010
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
ms.openlocfilehash: aa4d2355b18a3c6cc6fc3151c7662fbbbaa665d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554261"
---
# <a name="nmake-warning-u4010"></a>Ostrzeżenie NMAKE U4010

'target': kompilacja nie powiodła się; /K określony, kontynuowanie...

Polecenia w bloku poleceń dla danego obiektu docelowego zwrócił kod zakończenia różny od zera. Opcja /K informację NMAKE kontynuować przetwarzanie niepowiązanych części kompilacji i wydania kod zakończenia 1, po zakończeniu sesji NMAKE.

W przypadku danego obiektu docelowego, sama zależnych od ustawień lokalnych dla innego celu NMAKE generuje ostrzeżenie [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) po to ostrzeżenie.