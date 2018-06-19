---
title: Wartość zwracania cl.exe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, return value
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc8b5deab86597aca6e35b3d6f2d1adcca18be69
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374596"
---
# <a name="return-value-of-clexe"></a>Wartość zwracania cl.exe
Program cl.exe zwraca 0 w przypadku sukcesu (bez błędów) i wartość różną od zera w przeciwnym razie.  
  
 Wartość zwracana przez cl.exe może być przydatna, jeśli kompilujesz z pliku skryptu, powershell, .cmd lub .bat. Zaleca się przechwycenie danych wyjściowych kompilatora w przypadku błędów lub ostrzeżeń, tak aby można je było rozwiązać.  
  
 Istnieje zbyt wiele możliwych kodów wyjścia błędów dla cl.exe, aby je wszystkie wymienić. Można wyszukiwać kod błędu w pliku winerror.h lub ntstatus.h pliki uwzględniane w systemie Windows Software Development Kit w % ProgramFiles (x86) %\Windows Kit\\`version`\Include\shared\ katalogu. Kody błędów zwracane w zapisie dziesiętnym muszą zostać przekonwertowane na format szesnastkowy, aby możne je było wyszukać. Na przykład, kod błędu -1073741620 przekonwertowany na liczbę szesnastkową to 0xC00000CC. Ten błąd znajduje się w ntstatus.h, gdzie jest odpowiedni komunikat „Nie można odnaleźć określonej nazwy udziału na zdalnym serwerze”. Aby uzyskać listę kodów błędów systemu Windows, do pobrania, zobacz [ &#91;MS-ERREF&#93;: kodów błędów systemu Windows](http://msdn.microsoft.com/library/cc231196).  
  
 Możesz też użyć narzędzia wyszukiwania błędów w Visual Studio, aby się dowiedzieć, co oznacza komunikat o błędzie kompilatora. W powłoce poleceń programu Visual Studio, wprowadź **errlook.exe** Uruchom narzędzie; lub w programie Visual Studio IDE na pasku menu wybierz opcję **narzędzia**, **błąd podczas wyszukiwania**. Wprowadź wartość błędu, aby znaleźć opisowy tekst skojarzony z błędem. Aby uzyskać więcej informacji, zobacz [odwołanie ERRLOOK](../../build/reference/errlook-reference.md).  
  
## <a name="remarks"></a>Uwagi  
 Oto przykładowy plik .bat, używający wartości zwracanej przez cl.exe.  
  
```  
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
 [Składnia wiersza polecenia kompilatora](../../build/reference/compiler-command-line-syntax.md)