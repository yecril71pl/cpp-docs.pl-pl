---
title: Ostrzeżenie kompilatora (poziom 4) C4985
ms.date: 11/04/2016
f1_keywords:
- C4985
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
ms.openlocfilehash: 75feda6fb2c88b663aa6ade0efdfffc7def1568f
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810731"
---
# <a name="compiler-warning-level-4-c4985"></a>Ostrzeżenie kompilatora (poziom 4) C4985

"Nazwa symbolu": atrybuty nieobecne w poprzedniej deklaracji.

Adnotacje języka kodu źródłowego firmy Microsoft (SAL) na bieżącej deklaracji metody lub definicji różnią się od adnotacji we wcześniejszej deklaracji. Te same adnotacje SAL muszą być używane w definicji i deklaracji metody.

SAL zawiera zestaw adnotacji, za pomocą których można opisać, w jaki sposób funkcja używa swoich parametrów, przyjętych przez nią założeń oraz gwarancji, które wykonuje po zakończeniu. Adnotacje są zdefiniowane w pliku nagłówkowym sal. h.

Zwróć uwagę, że makra SAL nie zostaną rozwinięte, chyba że projekt ma określoną flagę [/analyze](../../build/reference/analyze-code-analysis.md) . Po określeniu parametru **/analyze**kompilator może zgłosić C4985, nawet jeśli nie pojawiły się żadne ostrzeżenia ani błędy bez **/analyze**.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Użyj tej samej adnotacji SAL dla definicji metody i wszystkich jej deklaracji.

## <a name="see-also"></a>Zobacz także

[Adnotacje SAL](../../c-runtime-library/sal-annotations.md)