---
title: Nazwy środowiska
ms.date: 11/04/2016
ms.assetid: 9af409a5-e724-465a-9a21-88d3586c2e92
ms.openlocfilehash: 67c49c256945eb60b10b9bc19b0dca8ba0b73a84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516977"
---
# <a name="environment-names"></a>Nazwy środowiska

**ANSI 4.10.4.4** zbiór środowiska nazwy i metodę zmieniania lista środowisk, używane przez [getenv](../c-runtime-library/reference/getenv-wgetenv.md) — funkcja

Zestaw nazw środowiska jest nieograniczona.

Aby zmienić zmienne środowiskowe z poziomu używanego programu C, należy wywołać [_putenv](../c-runtime-library/reference/putenv-wputenv.md) funkcji. Aby zmienić zmienne środowiskowe z wiersza polecenia w Windows, należy użyć polecenia SET (na przykład USTAWIĆ LIB = D:\ BIBLIOTEKI).

Zmienne środowiskowe ustawione z poziomu używanego programu C istnieje tylko tak długo, jak ich host powłoki poleceń systemu operacyjnego jest uruchomiony (CMD. Plik EXE lub COMMAND.COM). Na przykład wiersz

```
system( SET LIB = D:\LIBS );
```

Uruchom kopię powłoki poleceń (CMD. Z rozszerzeniem EXE), ustawić zmiennej środowiskowej LIB i powrócić do programu C, kończenie dodatkową kopię CMD. PLIK EXE. Kończenie tej kopii CMD. Plik EXE usuwa tymczasowej zmiennej środowiskowej LIB.

Podobnie, zmiany wprowadzone przez `_putenv` funkcji ostatnio tylko do momentu zakończenia programu.

## <a name="see-also"></a>Zobacz też

[Funkcje bibliotek](../c-language/library-functions.md)<br/>
[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)