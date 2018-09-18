---
title: Ostrzeżenie NMAKE U4011 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4011
dev_langs:
- C++
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1038ee86f76789451565ab6799795c851c95a95
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118339"
---
# <a name="nmake-warning-u4011"></a>Ostrzeżenie NMAKE U4011

'target': nie wszystkie elementy zależne, które są dostępne; docelowy nie został skompilowany

Zależnych od ustawień lokalnych z danym obiektem docelowym nie istnieje lub została nieaktualne i polecenia do aktualizowania zależne od zwrócił kod zakończenia różny od zera. Opcja /K informację NMAKE kontynuować przetwarzanie niepowiązanych części kompilacji i wydania kod zakończenia 1, po zakończeniu sesji NMAKE.

To ostrzeżenie jest poprzedzony ostrzeżenie [U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) dla każdego zależnych od ustawień lokalnych, nie może zostać utworzony lub zaktualizowany.