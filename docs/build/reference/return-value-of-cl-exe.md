---
title: "Wartość zwracania cl.exe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: cl.exe compiler, return value
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 85ca64178a4914cfbbc8b3a717b87ab5590cd778
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="return-value-of-clexe"></a>Wartość zwracania cl.exe
Program cl.exe zwraca 0 w przypadku sukcesu (bez błędów) i wartość różną od zera w przeciwnym razie.  
  
 Wartość zwracana przez cl.exe może być przydatna, jeśli kompilujesz z pliku skryptu, powershell, .cmd lub .bat. Zaleca się przechwycenie danych wyjściowych kompilatora w przypadku błędów lub ostrzeżeń, tak aby można je było rozwiązać.  
  
 Istnieje zbyt wiele możliwych kodów wyjścia błędów dla cl.exe, aby je wszystkie wymienić. Można wyszukiwać kod błędu w pliku winerror.h lub ntstatus.h pliki uwzględniane w systemie Windows Software Development Kit w % ProgramFiles (x86) %\Windows Kit\\`version`\Include\shared\ katalogu. Kody błędów zwracane w zapisie dziesiętnym muszą zostać przekonwertowane na format szesnastkowy, aby możne je było wyszukać. Na przykład, kod błędu -1073741620 przekonwertowany na liczbę szesnastkową to 0xC00000CC. Ten błąd znajduje się w ntstatus.h, gdzie jest odpowiedni komunikat „Nie można odnaleźć określonej nazwy udziału na zdalnym serwerze”. Aby uzyskać listę kodów błędów systemu Windows, do pobrania, zobacz [&#91; MS-ERREF &#93;: kodów błędów systemu Windows](http://msdn.microsoft.com/library/cc231196).  
  
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