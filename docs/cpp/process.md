---
title: proces
ms.date: 11/04/2016
f1_keywords:
- process_cpp
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
ms.openlocfilehash: 049360dddff2b9ca2ea460b96e027e86899f1ecb
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344992"
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
