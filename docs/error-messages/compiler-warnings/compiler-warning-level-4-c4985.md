---
title: Kompilator ostrzeżenie (poziom 4) C4985
ms.date: 11/04/2016
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
ms.openlocfilehash: 73abb166910cc421f042d22d67efc122e416bceb
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024442"
---
# <a name="compiler-warning-level-4-c4985"></a>Kompilator ostrzeżenie (poziom 4) C4985

"Nazwa symbolu": Brak atrybutów w poprzedniej deklaracji.

Microsoft źródła kodu adnotacji języka (SAL) adnotacje na bieżącej metody deklaracji lub definicji różnią się od adnotacji dla wcześniejszych deklaracji. W definicji i deklaracje metody należy użyć tej samej adnotacji SAL.

SAL zawiera zbiór adnotacji, które służy do opisywania, jak funkcja korzysta z jego parametrów, założeń, który ułatwia ich i gwarancje, które to sprawia, że na zakończenie. Adnotacje są definiowane w pliku nagłówkowym sal.h.

Należy zauważyć, że makra SAL nie zostanie rozwinięte, chyba że projekt ma [/ analyze](../../build/reference/analyze-code-analysis.md) określono flagę. Po określeniu **/ analyze**, kompilator może zgłosić C4985, nawet jeśli żadne ostrzeżenia ani błędy pojawiły się bez **/ analyze**.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Użyj tej samej adnotacji SAL w definicji metody i wszystkich jego deklaracji.

## <a name="see-also"></a>Zobacz także

[Adnotacje SAL](../../c-runtime-library/sal-annotations.md)