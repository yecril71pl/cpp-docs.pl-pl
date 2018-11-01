---
title: Diagnostyka wydrukowana przez funkcję assert
ms.date: 11/04/2016
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
ms.openlocfilehash: 330c694b53957cab2e44da7cb8b52031c33fb5a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549048"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostyka wydrukowana przez funkcję assert

**ANSI 4.2** diagnostyczne drukowanymi przez i zachowanie po przerwaniu dla **asercja** — funkcja

**Asercja** funkcja drukuje komunikat diagnostyczny i wywołania **przerwać** procedury, jeśli wyrażenie ma wartość false (0). Komunikat diagnostyczny ma postać

> **Nie można potwierdzić**: <em>wyrażenie</em>**, plik** <em>filename</em>**, wiersz** *linenumber*

gdzie *filename* jest nazwa pliku źródłowego i *linenumber* jest numer wiersza potwierdzenie, że nie powiodło się w pliku źródłowym. Jeśli zostanie podjęta żadna akcja *wyrażenie* ma wartość true (niezerową).

## <a name="see-also"></a>Zobacz też

[Funkcje bibliotek](../c-language/library-functions.md)