---
title: abort — funkcja
ms.date: 12/01/2017
helpviewer_keywords:
- abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
ms.openlocfilehash: 7c87cb4fe7349a0d623c765c20e7e213a8454571
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451236"
---
# <a name="abort-function"></a>abort — funkcja

**Przerwać** funkcji, również są deklarowane w pliku standardowych dołączonych \<stdlib.h >, kończy program w języku C++. Różnica między `exit` i **przerwać** jest fakt, że `exit` pozwala na przetwarzanie zakończenia środowiska wykonawczego języka C++, wyznacz (globalny obiekt zostaną wywołane destruktory), natomiast **przerwać** natychmiast kończy program. Aby uzyskać więcej informacji, zobacz [przerwać](../c-runtime-library/reference/abort.md) w *odwołanie do biblioteki wykonawczej*.

## <a name="see-also"></a>Zobacz także

[Kończenie działania programu](../cpp/program-termination.md)