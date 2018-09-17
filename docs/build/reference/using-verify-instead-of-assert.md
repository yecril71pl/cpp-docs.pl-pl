---
title: Korzystanie z VERIFY zamiast ASSERT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- assert
dev_langs:
- C++
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea6ea90460f3fd28724ee1fd34dfdeb3f6ae80b2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711779"
---
# <a name="using-verify-instead-of-assert"></a>Korzystanie z VERIFY zamiast ASSERT

Załóżmy, że po uruchomieniu wersji debugowania aplikacji MFC, że nie występują problemy. Jednak wydanej wersji ta sama aplikacja ulegnie awarii, zwraca niepoprawne wyniki i/lub wykazuje nietypowe zachowanie.

Ten problem może być spowodowany umieszczenia ważne kodu w instrukcję ASSERT, aby sprawdzić, czy wykonuje poprawnie. Ponieważ Assert-instrukcje są ujęte w komentarz w kompilacji wydania programu MFC, kod nie działa w kompilacji wydania.

Jeśli używasz ASSERT aby upewnić się, że wywołanie funkcji zakończyła się pomyślnie, należy rozważyć użycie [Sprawdź](../../mfc/reference/diagnostic-services.md#verify) zamiast tego. VERIFY-makro ocenia argumentów w obu debugowania i wersji kompilacji aplikacji.

Preferowane innej techniki, to przypisać wartość zwracaną przez funkcję do zmiennej tymczasowej, a następnie przetestować zmiennej w instrukcji ASERCJI.

Sprawdź następujący fragment kodu:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

Ten kod uruchamia się doskonale w wersji debugowania aplikacji MFC. Jeśli wywołanie `calloc( )` pojawi się komunikat diagnostyczny, który zawiera plik i numer wiersza kończy się niepowodzeniem,. Jednak w przypadku kompilacji detalicznej aplikacji MFC:

- wywołanie `calloc( )` nigdy nie wystąpi, pozostawiając `buf` niezainicjowana, lub

- `strcpy_s( )` kopiuje "`Hello, World`" w losowych część pamięci, prawdopodobnie uległa awarii aplikacji i nie powodując system przestanie odpowiadać, lub

- `free()` próbuje zwolnić pamięć, która nigdy nie została przydzielona.

Aby użyć ASSERT poprawnie, przykładowy kod należy je zmienić następujące czynności:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
buf = (char *) calloc(sizeOfBuffer, sizeof(char) );
ASSERT( buf != NULL );
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

Możesz też zamiast tego użyj Sprawdź, czy:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

## <a name="see-also"></a>Zobacz też

[Naprawianie problemów kompilacji wydania](../../build/reference/fixing-release-build-problems.md)