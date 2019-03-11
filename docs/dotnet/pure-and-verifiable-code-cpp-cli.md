---
title: Kod czysty i weryfikowalny (C++/CLI)
ms.date: 11/04/2016
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
ms.openlocfilehash: 66f3b5a33791d20297cde6e6223ba65189a99682
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743830"
---
# <a name="pure-and-verifiable-code-ccli"></a>Kod czysty i weryfikowalny (C + +/ CLI)

Podczas programowania .NET, Visual C++ w programie Visual Studio 2017 obsługuje tworzenie zestawów mieszanych, za pomocą [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md) — opcja kompilatora. **/CLR: pure** i **CLR: Safe** opcje są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017. Jeśli Twój kod musi być bezpieczne lub możliwe do zweryfikowania, a następnie zaleca się jej do portu C#.

## <a name="mixed-clr"></a>Mieszany (/ clr)

Zestawy mieszane (skompilowany przy użyciu **/CLR**) zawierać zarówno niezarządzane i zarządzane części, co umożliwia korzystanie z funkcji platformy .NET, ale zawierają kodu natywnego. Dzięki temu aplikacje i składniki można zaktualizować korzystać z funkcji .NET bez konieczności przebudować całego projektu. Za pomocą języka Visual C++ można mieszać kodu zarządzanego i natywnego w ten sposób jest nazywany międzyoperacyjności języka C++. Aby uzyskać więcej informacji, zobacz [zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md) i [natywne i .NET współdziałanie](../dotnet/native-and-dotnet-interoperability.md).

Wywołania z zarządzanych zestawów natywnych bibliotek DLL za pośrednictwem metody P/Invoke zostanie skompilowany, ale może się nie powieść w czasie wykonywania, w zależności od ustawień zabezpieczeń.

Istnieje jeden scenariusz kodowania, który zostanie przekazany kompilator, ale powodującymi nieweryfikowalnego zestawu: wywołanie funkcji wirtualnej za pomocą wystąpienia obiektu za pomocą operatora rozpoznawania zakresu.  Na przykład: `MyObj -> A::VirtualFunction();`.

## <a name="see-also"></a>Zobacz także

- [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
