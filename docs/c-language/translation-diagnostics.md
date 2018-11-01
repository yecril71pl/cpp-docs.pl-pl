---
title: 'Tłumaczenie: diagnostyka'
ms.date: 11/04/2016
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
ms.openlocfilehash: 4863b97dc1db7ff295b5f786ca97da2551d0fa62
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665000"
---
# <a name="translation-diagnostics"></a>Tłumaczenie: diagnostyka

**ANSI 2.1.1.3** sposób identyfikacji diagnostyki

Microsoft C generuje komunikaty o błędach w formie:

> *Nazwa pliku* **(** *numer wiersza* **):** *diagnostycznych* **C**  <em>Liczba</em> *wiadomości*

gdzie *filename* to nazwa pliku źródłowego, w którym wystąpił błąd; *numer wiersza* jest numer wiersza, w którym kompilator wykrył błąd; *diagnostycznych* to "error" lub "ostrzeżenie"; *numer* to unikatowy numer czterech cyfr (poprzedzone **C**, jak wspomniano w składni), które identyfikują błąd lub ostrzeżenie; *komunikat* jest komunikat z wyjaśnieniem.

## <a name="see-also"></a>Zobacz też

[Zachowanie zdefiniowane w implementacji](../c-language/implementation-defined-behavior.md)