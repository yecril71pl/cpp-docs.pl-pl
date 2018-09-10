---
title: Specyfikatory zastąpienia (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bcbc46ea12dd053c0c0cf5066173ea2a28857452
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316123"
---
# <a name="override-specifiers--c-component-extensions"></a>Specyfikatory zastąpienia (C++ Component Extensions)

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

[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)