---
title: Kod czysty i weryfikowalny (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- /clr compiler option [C++], verifiable assemblies
- /clr compiler option [C++], mixed assemblies
- pure MSIL [C++]
- verifiable assemblies [C++]
- verifiably type-safe code [C++]
- /clr compiler option [C++], pure assemblies
- .NET Framework [C++], pure and verifiable code
- assemblies [C++], mixed code
- verifiable assemblies [C++], about verifiable assemblies
- mixed assemblies [C++], about mixed assemblies
- pure MSIL [C++], about pure code
- assemblies [C++], verifiable code
- mixed assemblies [C++]
- assemblies [C++], pure code
ms.assetid: 9050e110-fa11-4356-b56c-665187ff871c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 453bb40e94c1d345adbe22f8792b59d1e584499a
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704831"
---
# <a name="pure-and-verifiable-code-ccli"></a>Kod czysty i weryfikowalny (C + +/ CLI)

Programowania .NET, Visual C++ w programie Visual Studio 2017 obsługuje tworzenie zestawów mieszanych przy użyciu [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md) — opcja kompilatora. **/CLR: pure** i **CLR: Safe** opcje są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r. Jeśli kod musi być bezpieczne lub możliwe do zweryfikowania, następnie zalecamy portu dla C#.

## <a name="mixed-clr"></a>Mieszane (/ clr)

Zestawy mieszane (skompilowane z **/CLR**), zawiera zarówno niezarządzanych i zarządzanych części, co umożliwia korzystanie z funkcji .NET, ale nadal zawierać kodu natywnego. Dzięki temu aplikacje i składniki można zaktualizować funkcji .NET bez konieczności czy ponownego napisania całego projektu. Za pomocą języka Visual C++ do mieszać kodu zarządzanego i natywnego w ten sposób jest nazywany międzyoperacyjności języka C++. Aby uzyskać więcej informacji, zobacz [zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md) i [natywne i .NET współdziałanie](../dotnet/native-and-dotnet-interoperability.md).

Wywołania z zarządzanych zestawów natywnych bibliotek DLL przy użyciu elementu P/Invoke zostanie skompilowany, ale może się nie powieść w czasie wykonywania w zależności od ustawień zabezpieczeń.

Istnieje jeden scenariusz kodowania, które przechodzą przez kompilator, ale który spowoduje w zestawie, do którego nie można zweryfikować: wywołanie funkcji wirtualnych do wystąpienia obiektu przy użyciu operator rozpoznawania zakresów.  Na przykład: `MyObj -> A::VirtualFunction();`.

## <a name="see-also"></a>Zobacz także

- [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

