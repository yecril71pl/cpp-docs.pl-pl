---
title: Specyfikatory zastąpienia (C + +/ CLI i C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
ms.openlocfilehash: 9640270caa50f53c106bb7b970959f0c092a47df
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787294"
---
# <a name="override-specifiers--ccli-and-ccx"></a>Specyfikatory zastąpienia (C + +/ CLI i C + +/ CX)

*Specyfikatory przesłonięć* zmodyfikować sposób dziedziczone typy i członkowie typów dziedziczonych zachowują się w typach pochodnych.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat nadpisania specyfikatorów zobacz:

- [abstract](abstract-cpp-component-extensions.md)

- [New (nowe gniazdo w vtable)](new-new-slot-in-vtable-cpp-component-extensions.md)

- [override](override-cpp-component-extensions.md)

- [sealed](sealed-cpp-component-extensions.md)

- [Zastąpienie specyfikatorów i kompilacji macierzystych](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)

**abstrakcyjna** i **zapieczętowanego** są również prawidłowe w typach deklaracji, gdzie nie działają jak zastępujące specyfikatory.

Aby uzyskać informacje dotyczące jawnego przesyłania funkcji klasy podstawowej, zobacz [jawne zastępowanie](explicit-overrides-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

(Nie ma żadnych uwag dla tej funkcji języka, które dotyczą tylko środowiska uruchomieniowego Windows).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

(Nie ma żadnych uwag dla tej funkcji języka, które dotyczą tylko środowiska uruchomieniowego języka wspólnego).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)