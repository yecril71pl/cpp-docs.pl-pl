---
title: 'Translation: Diagnostyka'
ms.date: 11/04/2016
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
ms.openlocfilehash: a274b7c5f29b091b2bf29922abfa4d66d3447b47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344970"
---
# <a name="translation-diagnostics"></a>Translation: Diagnostyka

**ANSI 2.1.1.3** sposób identyfikacji diagnostyki

Microsoft C generuje komunikaty o błędach w formie:

> *Nazwa pliku* **(** *numer wiersza* **):** *diagnostycznych* **C**  <em>Liczba</em> *wiadomości*

gdzie *filename* to nazwa pliku źródłowego, w którym wystąpił błąd; *numer wiersza* jest numer wiersza, w którym kompilator wykrył błąd; *diagnostycznych* to "error" lub "ostrzeżenie"; *numer* to unikatowy numer czterech cyfr (poprzedzone **C**, jak wspomniano w składni), które identyfikują błąd lub ostrzeżenie; *komunikat* jest komunikat z wyjaśnieniem.

## <a name="see-also"></a>Zobacz także

[Zachowanie zdefiniowane w implementacji](../c-language/implementation-defined-behavior.md)
