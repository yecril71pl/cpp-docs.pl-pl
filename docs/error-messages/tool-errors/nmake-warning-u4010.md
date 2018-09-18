---
title: Ostrzeżenie NMAKE U4010 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4010
dev_langs:
- C++
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a640245db460f4cd8cd658c097955a69a59d1fb7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117507"
---
# <a name="nmake-warning-u4010"></a>Ostrzeżenie NMAKE U4010

'target': kompilacja nie powiodła się; /K określony, kontynuowanie...

Polecenia w bloku poleceń dla danego obiektu docelowego zwrócił kod zakończenia różny od zera. Opcja /K informację NMAKE kontynuować przetwarzanie niepowiązanych części kompilacji i wydania kod zakończenia 1, po zakończeniu sesji NMAKE.

W przypadku danego obiektu docelowego, sama zależnych od ustawień lokalnych dla innego celu NMAKE generuje ostrzeżenie [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) po to ostrzeżenie.