---
title: proces
ms.date: 11/04/2016
f1_keywords:
- process_cpp
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
ms.openlocfilehash: f684c9c2ddfcb0aa166e1240c5f928ee52218f45
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227208"
---
# `process`

Określa, że proces aplikacji zarządzanej powinien mieć pojedynczą kopię określonej zmiennej globalnej, statyczną zmienną członkowską lub statyczną zmienną lokalną współdzieloną we wszystkich domenach aplikacji w procesie. Jest to przeznaczone głównie do użycia podczas kompilowania z **`/clr:pure`** , który jest przestarzały w programie Visual studio 2015 i nieobsługiwany w programie Visual studio 2017. Podczas kompilowania z **`/clr`** , zmienne globalne i statyczne są domyślnie przetwarzane na proces i nie muszą być używane **`__declspec(process)`** .

Tylko zmienna globalna, statyczna zmienna członkowska lub statyczna zmienna lokalna typu natywnego może być oznaczona przy użyciu **`__declspec(process)`** .

**`process`** jest prawidłowa tylko w przypadku kompilowania przy użyciu [`/clr`](../build/reference/clr-common-language-runtime-compilation.md) .

Jeśli chcesz, aby każda domena aplikacji miała własną kopię zmiennej globalnej, użyj [elementu AppDomain](../cpp/appdomain.md).

Aby uzyskać więcej informacji [, zobacz domeny aplikacji i Visual C++](../dotnet/application-domains-and-visual-cpp.md) .

## <a name="see-also"></a>Zobacz także

[`__declspec`](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
