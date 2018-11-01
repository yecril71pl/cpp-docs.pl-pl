---
title: Specyfikatory zastąpienia (C + +/ CLI i C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
ms.openlocfilehash: 9d839b9530cff144cda7897b0c96af48c14454a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639859"
---
# <a name="override-specifiers--ccli-and-ccx"></a>Specyfikatory zastąpienia (C + +/ CLI i C + +/ CX)

*Specyfikatory przesłonięć* zmodyfikować sposób dziedziczone typy i członkowie typów dziedziczonych zachowują się w typach pochodnych.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat nadpisania specyfikatorów zobacz:

- [abstract](../windows/abstract-cpp-component-extensions.md)

- [New (nowe gniazdo w vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)

- [override](../windows/override-cpp-component-extensions.md)

- [sealed](../windows/sealed-cpp-component-extensions.md)

- [Zastąpienie specyfikatorów i kompilacji macierzystych](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)

**abstrakcyjna** i **zapieczętowanego** są również prawidłowe w typach deklaracji, gdzie nie działają jak zastępujące specyfikatory.

Aby uzyskać informacje dotyczące jawnego przesyłania funkcji klasy podstawowej, zobacz [jawne zastępowanie](../windows/explicit-overrides-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

(Nie ma żadnych uwag dla tej funkcji języka, które dotyczą tylko środowiska uruchomieniowego Windows).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

(Nie ma żadnych uwag dla tej funkcji języka, które dotyczą tylko środowiska uruchomieniowego języka wspólnego).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](../windows/component-extensions-for-runtime-platforms.md)