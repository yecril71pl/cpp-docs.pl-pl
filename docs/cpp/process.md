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
ms.openlocfilehash: 65ae8eef828a8abd4bf726c99850089c0f30b71b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032571"
---
# <a name="process"></a>proces

Określa, że proces zarządzanej aplikacji powinny mieć pojedynczą kopię określonej zmiennej globalnej, statyczny element członkowski, zmienna lub statyczna zmienna lokalna współużytkowane przez wszystkie domeny aplikacji w procesie. To przede wszystkim był przeznaczony do użycia podczas kompilowania za pomocą **/CLR: pure**, która jest przestarzała w programie Visual Studio 2017 i obsługiwane w programie Visual Studio 2017. Podczas kompilowania za pomocą **/CLR**, zmiennych globalnych i statycznych na proces domyślnie i nie trzeba używać **__declspec(proces)**.

Tylko zmienną globalną, zmienną statycznej składowej lub zmiennej lokalnej statycznej natywnego typu mogą być oznaczone **__declspec(proces)**.

**proces** jest prawidłowy tylko podczas kompilowania za pomocą [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

Jeśli chcesz, aby każda domena aplikacji, aby mieć własną kopię zmiennej globalnej, użyj [appdomain](../cpp/appdomain.md).

Zobacz [domeny aplikacji i programu Visual C++](../dotnet/application-domains-and-visual-cpp.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
