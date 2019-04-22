---
title: Specyfikatory zastąpienia (C++sposób niezamierzony i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
ms.openlocfilehash: c1e8e7db2879b0226eaff562f5b5b826bce14caf
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029932"
---
# <a name="override-specifiers--ccli-and-ccx"></a>Specyfikatory zastąpienia (C++sposób niezamierzony i C++/CX)

*Specyfikatory przesłonięć* zmodyfikować sposób dziedziczone typy i członkowie typów dziedziczonych zachowują się w typach pochodnych.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat nadpisania specyfikatorów zobacz:

- [abstract](abstract-cpp-component-extensions.md)

- [new (nowe gniazdo w vtable)](new-new-slot-in-vtable-cpp-component-extensions.md)

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

## <a name="see-also"></a>Zobacz także

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)