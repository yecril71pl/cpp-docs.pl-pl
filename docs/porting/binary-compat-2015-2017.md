---
title: Plik binarny C++ zgodność programu Visual Studio 2015 i Visual Studio 2017 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: d7f96206288828a3e38422786585b3d66787860d
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2018
ms.locfileid: "42465513"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2017"></a>Plik binarny C++ zgodność programu Visual Studio 2015 i Visual Studio 2017

W poprzednich wersjach programu Visual Studio zgodność binarną między pliki obiektów (OBJs), biblioteki statyczne (biblioteki), dynamicznej biblioteki dll i plików wykonywalnych (exe) skompilowanych przy użyciu różnych wersji bibliotek środowiska uruchomieniowego i zestaw narzędzi kompilatora nie gwarantowana. To została zmieniona w programie Visual Studio 2017. W programie Visual Studio 2015 i Visual Studio 2017 numer główny zestaw narzędzi języka C++ jest 14 (dla programu Visual Studio 2015 w wersji 140 i wersji 141 dla programu Visual Studio 2017). Odzwierciedla fakt, że aplikacje skompilowane z danej wersji kompilatora i biblioteki środowiska uruchomieniowego są — w przeważającej części — zgodne dane binarne. Oznacza to, na przykład, że można utworzyć biblioteki DLL w programie Visual Studio 2017 i używanie go z poziomu aplikacji skompilowanych przy użyciu programu Visual Studio 2015 lub możliwe używanie bibliotek pakiet redystrybucyjny programu Visual Studio 2017 z aplikacją utworzoną za pomocą zestawu narzędzi 2015.  

Istnieją jednak dwa wyjątki od tej reguły. Zgodność binarną nie jest gwarantowana w następujących przypadkach:  

1. Gdy bibliotek statycznych lub pliki obiektów są kompilowane przy użyciu `/GL` przełącznika kompilatora.  

2. Podczas korzystania z biblioteki utworzonych za pomocą narzędzi, których wersja jest wyższa niż zestaw narzędzi umożliwia kompilowanie i łączenie aplikacji. Na przykład program, który jest skompilowany i jest połączony z zestawem narzędzi 19.12 mogą korzystać z bibliotek, które są kompilowane przy użyciu wersji 19.0 się za pośrednictwem 19.12. Łączenie 19.x programy z bibliotekami produkowane przez Visual Studio 2013 lub wcześniej nie jest obsługiwane.

## <a name="see-also"></a>Zobacz też  

[Historia zmian Visual C++](..\porting\visual-cpp-change-history-2003-2015.md)