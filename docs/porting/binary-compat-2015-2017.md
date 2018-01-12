---
title: "Dane binarne C++ zgodność programu Visual Studio 2015 i Visual Studio 2017 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d527a4e0647fe0e8471e168841a93512f4d1a9e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2017"></a>Dane binarne C++ zgodność programu Visual Studio 2015 i Visual Studio 2017


W poprzednich wersjach programu Visual Studio zgodności plików binarnych między plików obiektów (pliki obj), biblioteki statyczne (biblioteki), dynamiczne bibliotekach (dll) i pliki wykonywalne (exe) utworzony przy użyciu różnych wersji kompilatora zestaw narzędzi i środowiska uruchomieniowego bibliotek nie gwarancji. To została zmieniona w programie Visual Studio 2017 r. W programie Visual Studio 2015 i Visual Studio 2017 główny numer zestawu narzędzi języka C++ jest 14 (w wersji 140 dla programu Visual Studio 2015 i v141 dla programu Visual Studio 2017 r). Ta właściwość odzwierciedla fakt, że zarówno bibliotek środowiska uruchomieniowego, jak i aplikacje skompilowane z danej wersji kompilatora są--najbardziej części--zgodne dane binarne. Oznacza to, na przykład, że można utworzyć biblioteki DLL w programie Visual Studio 2017 r i pobrać go z aplikacji kompilowane przy użyciu programu Visual Studio 2015 lub biblioteki pakietu redystrybucyjnego programu Visual Studio 2017 za pomocą aplikacji utworzony za pomocą zestawu narzędzi 2015.  

Istnieją dwa wyjątki od tej reguły. Zgodność binarną nie jest gwarantowana w tych przypadkach:  

1) Gdy biblioteki statyczne lub obiektu pliki są kompilowane przy użyciu przełącznika kompilatora /GL.  

2) Gdy aplikacja zużyje pakietu redystrybucyjnego bibliotek, których numer wersji jest mniejsza niż zestaw narzędzi, która jest używana do kompilowania aplikacji. Innymi słowy Jeśli kompilacja programu przy użyciu v141 zestaw narzędzi platformy dowolnego pakietu redystrybucyjnego bibliotek, które korzysta z aplikacji musi być skompilowany z v141 lub nowszej.  

## <a name="see-also"></a>Zobacz też  

[Historia zmian w usłudze Visual C++](..\porting\visual-cpp-change-history-2003-2015.md)


