---
title: wmain — korzystanie
ms.date: 11/04/2016
helpviewer_keywords:
- wmain function
ms.assetid: d0300812-adc4-40c6-bba3-b2da25468c80
ms.openlocfilehash: d467d50a7188cd665f64de8b6f0ce6e6a37df752
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290823"
---
# <a name="using-wmain"></a>wmain — korzystanie

**Microsoft Specific**

W modelu programowania Unicode, można zdefiniować wersja znaków dwubajtowych **głównego** funkcji. Użyj **wmain** zamiast **głównego** Jeśli chcesz tworzyć przenośny kod, zgodną Unicode model programowania.

## <a name="syntax"></a>Składnia

```
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )
```

## <a name="remarks"></a>Uwagi

Możesz deklarować Parametry formalne dla **wmain** formacie podobne do **głównego**. Możesz następnie przekazać argumenty znaków dwubajtowych i, opcjonalnie, wskaźnik znaku dwubajtowego środowiska do programu. `argv` i `envp` parametry **wmain** typu `wchar_t*`. Na przykład:

Jeśli program używa **głównego** funkcji środowiska znak wielobajtowy jest tworzony przez biblioteki wykonawczej w momencie uruchamiania programu. Tworzona jest kopia znaków dwubajtowych, środowiska, tylko wtedy, gdy jest to wymagane (na przykład przez wywołanie `_wgetenv` lub `_wputenv` funkcji). W pierwszym wywołaniu `_wputenv`, lub na pierwsze wywołanie `_wgetenv` Jeśli istnieje już środowisko MBCS, odpowiednie środowisko ciąg znaków dwubajtowych jest tworzony i następnie jest wskazywany przez `_wenviron` zmiennej globalnej, czyli znaków dwubajtowych Wersja `_environ` zmiennej globalnej. W tym momencie dwie kopie środowiska (MBCS i Unicode) mogły współistnieć i są obsługiwane przez system operacyjny w całym cyklu życia programu.

Podobnie jeśli program używa **wmain** funkcji, jest tworzony w momencie uruchamiania programu środowiska szerokich znaków i jest wskazywany przez `_wenviron` zmiennej globalnej. Środowisko MBCS (ASCII) jest tworzona przy pierwszym wywołaniu do `_putenv` lub `getenv`i jest wskazywany przez `_environ` zmiennej globalnej.

Aby uzyskać więcej informacji na temat środowiska MBCS, zobacz [internacjonalizacji](../c-runtime-library/internationalization.md) w *odwołanie do biblioteki wykonawczej.*

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcja main i wykonywanie programu](../c-language/main-function-and-program-execution.md)
