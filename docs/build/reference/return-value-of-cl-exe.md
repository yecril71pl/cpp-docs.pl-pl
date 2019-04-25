---
title: Wartość zwracania cl.exe
ms.date: 09/05/2018
helpviewer_keywords:
- cl.exe compiler, return value
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
ms.openlocfilehash: 1617208a8d99e3c5643330f75faf9beed9ce5f1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319021"
---
# <a name="return-value-of-clexe"></a>Wartość zwracania cl.exe

Program cl.exe zwraca 0 w przypadku sukcesu (bez błędów) i wartość różną od zera w przeciwnym razie.

Wartość zwracana przez cl.exe może być przydatna, jeśli kompilujesz z pliku skryptu, powershell, .cmd lub .bat. Zaleca się przechwycenie danych wyjściowych kompilatora w przypadku błędów lub ostrzeżeń, tak aby można je było rozwiązać.

Istnieje zbyt wiele możliwych kodów wyjścia błędów dla cl.exe, aby je wszystkie wymienić. Możesz wyszukać kod błędu w plikach winerror.h lub ntstatus.h, zawartych w Windows Software Development Kit w % ProgramFiles (x86) %\Windows zestawy\\<em>wersji</em>\Include\shared\ katalogu. Kody błędów zwracane w zapisie dziesiętnym muszą zostać przekonwertowane na format szesnastkowy, aby możne je było wyszukać. Na przykład, kod błędu -1073741620 przekonwertowany na liczbę szesnastkową to 0xC00000CC. Ten błąd znajduje się w ntstatus.h, gdzie jest odpowiedni komunikat „Nie można odnaleźć określonej nazwy udziału na zdalnym serwerze”. Aby pobrać listę kodów błędów, Windows, zobacz [ &#91;MS-ERREF&#93;: Kody błędów Windows](https://msdn.microsoft.com/library/cc231196).

Możesz też użyć narzędzia wyszukiwania błędów w Visual Studio, aby się dowiedzieć, co oznacza komunikat o błędzie kompilatora. W powłoce poleceń programu Visual Studio, wprowadź **errlook.exe** Aby uruchomić narzędzie lub w programie Visual Studio IDE na pasku menu wybierz **narzędzia**, **wyszukiwanie błędów**. Wprowadź wartość błędu, aby znaleźć opisowy tekst skojarzony z błędem. Aby uzyskać więcej informacji, zobacz [odwołanie ERRLOOK](errlook-reference.md).

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

## <a name="see-also"></a>Zobacz także

[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
