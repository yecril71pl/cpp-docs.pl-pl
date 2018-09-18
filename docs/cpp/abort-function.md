---
title: Abort — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/01/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d6e0b7dc49fbc53eb5e079657d98380d10bedf4c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036491"
---
# <a name="abort-function"></a>abort — funkcja

**Przerwać** funkcji, również są deklarowane w pliku standardowych dołączonych \<stdlib.h >, kończy program w języku C++. Różnica między `exit` i **przerwać** jest fakt, że `exit` pozwala na przetwarzanie zakończenia środowiska wykonawczego języka C++, wyznacz (globalny obiekt zostaną wywołane destruktory), natomiast **przerwać** natychmiast kończy program. Aby uzyskać więcej informacji, zobacz [przerwać](../c-runtime-library/reference/abort.md) w *odwołanie do biblioteki wykonawczej*.

## <a name="see-also"></a>Zobacz także

[Kończenie działania programu](../cpp/program-termination.md)