---
title: Konwersje z innych typów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e919782022ee64f657611a14d6eae6173a67b8c0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32382682"
---
# <a name="conversions-from-other-types"></a>Konwersje z innych typów

Ponieważ **wyliczenia** wartość jest **int** wartości zgodnie z definicją konwersje do i z **wyliczenia** wartości są takie same jak te dotyczące **int** typu. Dla kompilatora Microsoft C całkowitą jest taka sama jak **długi**.

**Microsoft Specific**

Nie konwersji między typami struktura lub związek są dozwolone.

Każda wartość może zostać przekonwertowana na typ **void**, ale wynik takich konwersji może być używana wyłącznie w kontekście, gdzie wartość wyrażenia jest usuwane, takie jak instrukcja wyrażenia.

**Void** typ nie ma wartości, zgodnie z definicją. W związku z tym nie można przekonwertować żadnego innego typu, i innych typów nie można przekonwertować na **void** przez przypisanie. Jednak jawnie rzutowania wartości na typ **void**, zgodnie z opisem w [konwersje rzutowania typów](../c-language/type-cast-conversions.md).

**KOŃCOWY określonych firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Konwersje przypisań](../c-language/assignment-conversions.md)  
