---
title: Diagnostyka wydrukowana przez funkcję assert
ms.date: 11/04/2016
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
ms.openlocfilehash: 666ba22d642b772fe8ad336f57ab1bdd82bd2e18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234226"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostyka wydrukowana przez funkcję assert

**ANSI 4,2** Diagnostyka wydrukowana przez i zakończenie działania funkcji **Assert**

Funkcja **Assert** drukuje komunikat diagnostyczny i wywołuje procedurę **Abort** , jeśli wyrażenie ma wartość false (0). Komunikat diagnostyczny ma postać

> **Potwierdzenie nie powiodło się**: <em>wyrażenie</em>**, plik** <em>filename</em>**, line** *LineNumber*

gdzie *filename* jest nazwą pliku źródłowego, a *LineNumber* jest numerem wiersza potwierdzenia, który zakończył się niepowodzeniem w pliku źródłowym. Jeśli *wyrażenie* ma wartość true (niezerowe), nie jest wykonywana żadna akcja.

## <a name="see-also"></a>Zobacz też

[Funkcje bibliotek](../c-language/library-functions.md)
