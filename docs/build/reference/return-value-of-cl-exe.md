---
title: Wartość zwracania cl.exe
ms.date: 09/05/2018
helpviewer_keywords:
- cl.exe compiler, return value
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
ms.openlocfilehash: 627d20a85b8f31ab881588533840a888334e9847
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373778"
---
# <a name="return-value-of-clexe"></a>Wartość zwracania cl.exe

Program cl.exe zwraca 0 w przypadku sukcesu (bez błędów) i wartość różną od zera w przeciwnym razie.

Wartość zwracana przez cl.exe może być przydatna, jeśli kompilujesz z pliku skryptu, powershell, .cmd lub .bat. Zaleca się przechwycenie danych wyjściowych kompilatora w przypadku błędów lub ostrzeżeń, tak aby można je było rozwiązać.

Istnieje zbyt wiele możliwych kodów wyjścia błędów dla cl.exe, aby je wszystkie wymienić. Kod błędu można wyszukać w plikach Winerror. h lub Ntstatus. h zawartych w zestawie Windows Software Development Kit w katalogu% ProgramFiles (x86)% \ Windows Kit w \\ <em>wersji</em>\Include\shared\. Kody błędów zwracane w zapisie dziesiętnym muszą zostać przekonwertowane na format szesnastkowy, aby możne je było wyszukać. Na przykład, kod błędu -1073741620 przekonwertowany na liczbę szesnastkową to 0xC00000CC. Ten błąd znajduje się w ntstatus.h, gdzie jest odpowiedni komunikat „Nie można odnaleźć określonej nazwy udziału na zdalnym serwerze”. Aby uzyskać listę kodów błędów systemu Windows do pobrania, zobacz [&#91;MS-ERREF&#93;: kody błędów systemu Windows](https://docs.microsoft.com/openspecs/windows_protocols/MS-ERREF).

Możesz też użyć narzędzia wyszukiwania błędów w Visual Studio, aby się dowiedzieć, co oznacza komunikat o błędzie kompilatora. W powłoce poleceń programu Visual Studio wprowadź **errlook.exe** , aby uruchomić narzędzie; lub w środowisku IDE programu Visual Studio na pasku menu wybierz kolejno opcje **Narzędzia**i **wyszukiwanie błędów**. Wprowadź wartość błędu, aby znaleźć opisowy tekst skojarzony z błędem. Aby uzyskać więcej informacji, zobacz [ERRLOOK Reference](errlook-reference.md).

## <a name="remarks"></a>Uwagi

Oto przykładowy plik .bat, używający wartości zwracanej przez cl.exe.

```cmd
echo off
cl /W4 t.cpp
@if ERRORLEVEL == 0 (
   goto good
)

@if ERRORLEVEL != 0 (
   goto bad
)

:good
   echo "clean compile"
   echo %ERRORLEVEL%
   goto end

:bad
   echo "error or warning"
   echo %ERRORLEVEL%
   goto end

:end
```

## <a name="see-also"></a>Zobacz też

[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
