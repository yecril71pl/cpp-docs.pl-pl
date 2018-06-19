---
title: Dane binarne C++ zgodność programu Visual Studio 2015 i Visual Studio 2017 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/21/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dcd315631d74c652177dba99cbe533ad91f68474
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33838985"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2017"></a>Dane binarne C++ zgodność programu Visual Studio 2015 i Visual Studio 2017


W poprzednich wersjach programu Visual Studio zgodności plików binarnych między plików obiektów (pliki obj), biblioteki statyczne (biblioteki), dynamiczne bibliotekach (dll) i pliki wykonywalne (exe) utworzony przy użyciu różnych wersji kompilatora zestaw narzędzi i środowiska uruchomieniowego bibliotek nie gwarancji. To została zmieniona w programie Visual Studio 2017 r. W programie Visual Studio 2015 i Visual Studio 2017 główny numer zestawu narzędzi języka C++ jest 14 (w wersji 140 dla programu Visual Studio 2015 i v141 dla programu Visual Studio 2017 r). Ta właściwość odzwierciedla fakt, że zarówno bibliotek środowiska uruchomieniowego, jak i aplikacje skompilowane z danej wersji kompilatora są--najbardziej części--zgodne dane binarne. Oznacza to, na przykład, że można utworzyć biblioteki DLL w programie Visual Studio 2017 r i pobrać go z aplikacji kompilowane przy użyciu programu Visual Studio 2015 lub biblioteki pakietu redystrybucyjnego programu Visual Studio 2017 za pomocą aplikacji utworzony za pomocą zestawu narzędzi 2015.  

Istnieją dwa wyjątki od tej reguły. Zgodność binarną nie jest gwarantowana w tych przypadkach:  

1) Gdy biblioteki statyczne lub obiektu pliki są kompilowane przy użyciu przełącznika kompilatora /GL.  

2) Podczas używania bibliotek skompilowanej za pomocą narzędzi, których wersja jest nowsza niż zestaw narzędzi używanych do kompilowania i łączenie aplikacji. Na przykład program, który jest skompilowany i połączone z zestawu narzędzi 19.12 mogą używać biblioteki, w których są kompilowane przy użyciu 19.0 się za pośrednictwem 19.12. Łączenie 19.x programy z bibliotekami utworzonego przez Visual Studio 2013 lub wcześniej nie jest obsługiwane.


## <a name="see-also"></a>Zobacz też  

[Historia zmian w usłudze Visual C++](..\porting\visual-cpp-change-history-2003-2015.md)


