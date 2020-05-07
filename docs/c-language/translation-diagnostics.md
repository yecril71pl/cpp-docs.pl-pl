---
title: 'Tłumaczenie: diagnostyka'
ms.date: 11/04/2016
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
ms.openlocfilehash: a274b7c5f29b091b2bf29922abfa4d66d3447b47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344970"
---
# <a name="translation-diagnostics"></a>Tłumaczenie: diagnostyka

**2.1.1.3 ANSI** Jak jest identyfikowana Diagnostyka

Microsoft C tworzy komunikaty o błędach w postaci:

> *filename* **(** *numer wiersza* **):** *komunikat* o<em>numerze</em> *diagnostyki* **C**

gdzie *filename* to nazwa pliku źródłowego, w którym wystąpił błąd; *numer wiersza* to numer wiersza, w którym Kompilator wykrył błąd; *Diagnostyka* to "Error" lub "Warning"; *Liczba* jest unikatową cyfrą czterocyfrową (poprzedzoną znakiem **C**, jak pokazano w składni), która identyfikuje błąd lub ostrzeżenie; *komunikat* jest komunikatem wyjaśniającym.

## <a name="see-also"></a>Zobacz też

[Zachowanie zdefiniowane w implementacji](../c-language/implementation-defined-behavior.md)
