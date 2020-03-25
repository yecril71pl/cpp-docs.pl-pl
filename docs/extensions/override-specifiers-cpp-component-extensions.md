---
title: Specyfikatory przesłonięciaC++( C++/CLI i/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
ms.openlocfilehash: 410fe9ecc48b92c68132f7b1b8057c2549c8afcf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181905"
---
# <a name="override-specifiers--ccli-and-ccx"></a>Specyfikatory przesłonięciaC++( C++/CLI i/CX)

*Specyfikatory przesłonięcia* modyfikują sposób, w jaki dziedziczone typy i elementy członkowskie dziedziczonych typów zachowują się w typach pochodnych.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat specyfikatorów zastąpienia, zobacz:

- [abstract](abstract-cpp-component-extensions.md)

- [new (nowe gniazdo w vtable)](new-new-slot-in-vtable-cpp-component-extensions.md)

- [override](override-cpp-component-extensions.md)

- [sealed](sealed-cpp-component-extensions.md)

- [Specyfikatory przesłonięcia i kompilacje natywne](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)

**abstrakcyjne** i **zapieczętowane** są również prawidłowe dla deklaracji typu, gdzie nie działają jako specyfikatory przesłonięcia.

Aby uzyskać informacje na temat jawnego przesłaniania funkcji klasy podstawowej, zobacz [jawne przesłonięcia](explicit-overrides-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

(Nie ma żadnych uwag dla tej funkcji języka, które mają zastosowanie tylko do środowisko wykonawcze systemu Windows).

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

(Nie ma żadnych uwag dla tej funkcji języka, które mają zastosowanie tylko do środowiska uruchomieniowego języka wspólnego).

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/clr`

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)
