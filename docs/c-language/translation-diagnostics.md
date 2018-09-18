---
title: 'Tłumaczenie: Diagnostyka | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d297cfd4f4dee49d3344ae2f159f85682f05ea2f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017589"
---
# <a name="translation-diagnostics"></a>Tłumaczenie: diagnostyka

**ANSI 2.1.1.3** sposób identyfikacji diagnostyki

Microsoft C generuje komunikaty o błędach w formie:

> *Nazwa pliku* **(** *numer wiersza* **):** *diagnostycznych* **C**  <em>Liczba</em> *wiadomości*

gdzie *filename* to nazwa pliku źródłowego, w którym wystąpił błąd; *numer wiersza* jest numer wiersza, w którym kompilator wykrył błąd; *diagnostycznych* to "error" lub "ostrzeżenie"; *numer* to unikatowy numer czterech cyfr (poprzedzone **C**, jak wspomniano w składni), które identyfikują błąd lub ostrzeżenie; *komunikat* jest komunikat z wyjaśnieniem.

## <a name="see-also"></a>Zobacz też

[Zachowanie zdefiniowane w implementacji](../c-language/implementation-defined-behavior.md)