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

**Specyficzne dla firmy Microsoft**

W modelu programowania Unicode można zdefiniować wersję funkcji **Main** o szerokim znaku. Użyj **wmain** zamiast **Main** , jeśli chcesz napisać kod przenośny, który jest zgodny z modelem programowania Unicode.

## <a name="syntax"></a>Składnia

```
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )
```

## <a name="remarks"></a>Uwagi

Należy zadeklarować formalne parametry do **wmain** przy użyciu podobnego formatu do **głównego**. Następnie można przekazywać argumenty o szerokim znaku oraz, opcjonalnie, wskaźnik środowiska do programu. Parametry `argv` i `envp` do **wmain** są typu `wchar_t*`. Przykład:

Jeśli program używa funkcji **Main** , środowisko znaków wielobajtowych jest tworzone przez bibliotekę wykonawczą podczas uruchamiania programu. Dwubajtowa kopia środowiska jest tworzona tylko wtedy, gdy jest to konieczne (na przykład przez wywołanie funkcji `_wgetenv` lub `_wputenv` ). Podczas pierwszego wywołania `_wputenv`do lub pierwszego wywołania, `_wgetenv` Jeśli środowisko MBCS już istnieje, jest tworzone odpowiednie środowisko ciągu znaków dwubajtowych, a następnie wskazywane przez zmienną `_wenviron` globalną, która jest wersja zmiennej `_environ` globalnej o szerokim znaku. W tym momencie dwie kopie środowiska (MBCS i Unicode) istnieją jednocześnie i są obsługiwane przez system operacyjny przez cały czas trwania programu.

Podobnie, jeśli program używa funkcji **wmain** , środowisko o szerokim znaku jest tworzone przy uruchamianiu programu i jest wskazywane przez zmienną `_wenviron` globalną. Środowisko MBCS (ASCII) jest tworzone podczas pierwszego wywołania do `_putenv` lub `getenv`, i jest wskazywane przez zmienną `_environ` globalną.

Aby uzyskać więcej informacji [na temat środowiska MBCS, zobacz](../c-runtime-library/internationalization.md) informacje o liczbie *porządkowej w dokumentacji dotyczącej biblioteki wykonawczej.*

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcja main i wykonywanie programu](../c-language/main-function-and-program-execution.md)
