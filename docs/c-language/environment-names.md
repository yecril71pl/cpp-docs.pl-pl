---
title: Nazwy środowiska
ms.date: 11/04/2016
ms.assetid: 9af409a5-e724-465a-9a21-88d3586c2e92
ms.openlocfilehash: 43e1254b4c1ee61a92fbb6499d9396e8b15a3047
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148000"
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

## <a name="see-also"></a>Zobacz także

[Funkcje bibliotek](../c-language/library-functions.md)<br/>
[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)
