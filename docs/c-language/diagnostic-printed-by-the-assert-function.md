---
title: Diagnostyka wydrukowana przez funkcję assert
ms.date: 11/04/2016
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
ms.openlocfilehash: 666ba22d642b772fe8ad336f57ab1bdd82bd2e18
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151003"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostyka wydrukowana przez funkcję assert

**ANSI 4.2** diagnostyczne drukowanymi przez i zachowanie po przerwaniu dla **asercja** — funkcja

**Asercja** funkcja drukuje komunikat diagnostyczny i wywołania **przerwać** procedury, jeśli wyrażenie ma wartość false (0). Komunikat diagnostyczny ma postać

> **Nie można potwierdzić**: <em>wyrażenie</em>**, plik** <em>filename</em>**, wiersz** *linenumber*

gdzie *filename* jest nazwa pliku źródłowego i *linenumber* jest numer wiersza potwierdzenie, że nie powiodło się w pliku źródłowym. Jeśli zostanie podjęta żadna akcja *wyrażenie* ma wartość true (niezerową).

## <a name="see-also"></a>Zobacz także

[Funkcje bibliotek](../c-language/library-functions.md)
