---
title: Kompilator ostrzeżenie (poziom 4) C4985 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d67b7394ef9bd38409ca45abe6ed7d347f5a37d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092676"
---
# <a name="compiler-warning-level-4-c4985"></a>Kompilator ostrzeżenie (poziom 4) C4985

"Nazwa symbolu": Brak atrybutów w poprzedniej deklaracji.

Microsoft źródła kodu adnotacji języka (SAL) adnotacje na bieżącej metody deklaracji lub definicji różnią się od adnotacji dla wcześniejszych deklaracji. W definicji i deklaracje metody należy użyć tej samej adnotacji SAL.

SAL zawiera zbiór adnotacji, które służy do opisywania, jak funkcja korzysta z jego parametrów, założeń, który ułatwia ich i gwarancje, które to sprawia, że na zakończenie. Adnotacje są definiowane w pliku nagłówkowym sal.h.

Należy zauważyć, że makra SAL nie zostanie rozwinięte, chyba że projekt ma [/ analyze](../../build/reference/analyze-code-analysis.md) określono flagę. Po określeniu **/ analyze**, kompilator może zgłosić C4985, nawet jeśli żadne ostrzeżenia ani błędy pojawiły się bez **/ analyze**.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Użyj tej samej adnotacji SAL w definicji metody i wszystkich jego deklaracji.

## <a name="see-also"></a>Zobacz też

[Adnotacje SAL](../../c-runtime-library/sal-annotations.md)