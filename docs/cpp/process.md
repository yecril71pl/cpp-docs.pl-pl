---
title: proces | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- process_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b36ec42447aa076d0623707951f82b7b9c95d563
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704909"
---
# <a name="process"></a>proces

Określa, czy procesu zarządzanej aplikacji powinien mieć pojedynczą kopię określonej zmiennej globalnej, statycznym elementem członkowskim zmiennej lub statyczna zmienna lokalna współużytkowana przez wszystkie domeny aplikacji w procesie. To przede wszystkim był przeznaczony do użycia podczas kompilowania za pomocą **/CLR: pure**, który jest przestarzała w programie Visual Studio 2017 i nieobsługiwane w programie Visual Studio 2017 r. Podczas kompilowania za pomocą **/CLR**, zmienne globalne i statyczne są na proces domyślnie i nie trzeba używać `__declspec(process)`.

Tylko zmiennej globalnej, statycznym elementem członkowskim zmiennej lub statyczna zmienna lokalna typu natywnego może być oznaczony przez `__declspec(process)`.

`process` jest prawidłowy tylko podczas kompilowania za pomocą [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

Każda domena aplikacji ma własną kopię zmiennej globalnej, należy użyć [elementu appdomain](../cpp/appdomain.md).

Zobacz [i domen aplikacji Visual C++](../dotnet/application-domains-and-visual-cpp.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

- [__declspec](../cpp/declspec.md)
- [Słowa kluczowe](../cpp/keywords-cpp.md)
