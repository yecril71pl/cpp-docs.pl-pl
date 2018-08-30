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
ms.openlocfilehash: 3925044f8cf827c38610308226cd6c32008a59a1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206099"
---
# <a name="return-value-of-clexe"></a>Wartość zwracania cl.exe
Program cl.exe zwraca 0 w przypadku sukcesu (bez błędów) i wartość różną od zera w przeciwnym razie.  
  
 Wartość zwracana przez cl.exe może być przydatna, jeśli kompilujesz z pliku skryptu, powershell, .cmd lub .bat. Zaleca się przechwycenie danych wyjściowych kompilatora w przypadku błędów lub ostrzeżeń, tak aby można je było rozwiązać.  
  
 Istnieje zbyt wiele możliwych kodów wyjścia błędów dla cl.exe, aby je wszystkie wymienić. Możesz wyszukać kod błędu w plikach winerror.h lub ntstatus.h, zawartych w Windows Software Development Kit w % ProgramFiles (x86) %\Windows zestawy\\`version`\Include\shared\ katalogu. Kody błędów zwracane w zapisie dziesiętnym muszą zostać przekonwertowane na format szesnastkowy, aby możne je było wyszukać. Na przykład, kod błędu -1073741620 przekonwertowany na liczbę szesnastkową to 0xC00000CC. Ten błąd znajduje się w ntstatus.h, gdzie jest odpowiedni komunikat „Nie można odnaleźć określonej nazwy udziału na zdalnym serwerze”. Aby pobrać listę kodów błędów, Windows, zobacz [ &#91;MS-ERREF&#93;: kody błędów Windows](https://msdn.microsoft.com/library/cc231196).  
  
 Możesz też użyć narzędzia wyszukiwania błędów w Visual Studio, aby się dowiedzieć, co oznacza komunikat o błędzie kompilatora. W powłoce poleceń programu Visual Studio, wprowadź **errlook.exe** Aby uruchomić narzędzie lub w programie Visual Studio IDE na pasku menu wybierz **narzędzia**, **wyszukiwanie błędów**. Wprowadź wartość błędu, aby znaleźć opisowy tekst skojarzony z błędem. Aby uzyskać więcej informacji, zobacz [odwołanie ERRLOOK](../../build/reference/errlook-reference.md).  
  
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