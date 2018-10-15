---
title: Specyfikatory zastąpienia (C + +/ CLI i C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/12/2018
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
ms.openlocfilehash: 0620bc7045dcb312667cfdfe670e1f19b0545cf2
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327467"
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

[Component Extensions dla platformy .NET i platformy uniwersalnej systemu Windows](../windows/component-extensions-for-runtime-platforms.md)