---
title: Obsługa używania funkcji wmain
ms.date: 11/04/2016
f1_keywords:
- wWinMain
helpviewer_keywords:
- wide characters [C++], wmain function
- wWinMain function
- wmain function
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
ms.openlocfilehash: 4af389c00f6065df631f891dadcb0b2f350f984d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491198"
---
# <a name="support-for-using-wmain"></a>Obsługa używania funkcji wmain

Wizualizacja C++ obsługuje definiowanie funkcji **wmain** i przekazywanie argumentów szerokich znaków do aplikacji Unicode. Można zadeklarować formalne parametry do **wmain**przy użyciu formatu podobnego do `main`. Następnie można przekazywać argumenty o szerokim znaku oraz, opcjonalnie, wskaźnik środowiska do programu. Parametry `argv` i `envp` do **wmain** są typu `wchar_t*`. Na przykład:

```cpp
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )
```

> [!NOTE]
> Aplikacje w formacie Unicode `wWinMain` MFC używają jako punktu wejścia. W tym przypadku `CWinApp::m_lpCmdLine` jest to ciąg Unicode. Upewnij się, że `wWinMainCRTStartup` ustawiono przy użyciu opcji konsolidatora [/entry](../build/reference/entry-entry-point-symbol.md) .

Jeśli program używa funkcji **Main** , środowisko znaków wielobajtowych jest tworzone przez bibliotekę wykonawczą podczas uruchamiania programu. Dwubajtowa kopia środowiska jest tworzona tylko wtedy, gdy jest to konieczne (na przykład przez wywołanie `_wgetenv` funkcji lub `_wputenv` ). Podczas pierwszego wywołania do `_wputenv`lub pierwszego `_wgetenv` wywołania, jeśli środowisko MBCS już istnieje, jest tworzony odpowiadające mu środowisko ciągu znaków. Środowisko jest wskazywane przez `_wenviron` zmienną globalną, która jest wersją `_environ` znaków dwubajtowych zmiennej globalnej. W tym momencie dwie kopie środowiska (MBCS i Unicode) istnieją jednocześnie i są obsługiwane przez system czasu wykonywania przez cały czas trwania programu.

Podobnie, jeśli program używa funkcji **wmain** , środowisko o szerokim znaku jest tworzone przy uruchamianiu programu i jest wskazywane przez `_wenviron` zmienną globalną. Środowisko MBCS (ASCII) jest tworzone podczas pierwszego wywołania do `_putenv` lub `getenv` i `_environ` jest wskazywane przez zmienną globalną.

## <a name="see-also"></a>Zobacz także

[Obsługa formatu Unicode](../text/support-for-unicode.md)<br/>
[Podsumowanie programowania Unicode](../text/unicode-programming-summary.md)<br/>
[WinMain, funkcja](/windows/win32/api/winbase/nf-winbase-winmain)
