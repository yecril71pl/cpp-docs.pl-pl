---
title: Zestawy o silnych nazwach (podpisywanie zestawów) (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- assemblies [C++]
- signing assemblies
- .NET Framework [C++], assembly signing
- assemblies [C++], signing
- linker [C++], assembly signing
- strong-named assemblies [C++]
ms.assetid: c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc
ms.openlocfilehash: 762c95c3ecc60995e8d0e6f9e4f7bc95d179c26f
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747504"
---
# <a name="strong-name-assemblies-assembly-signing-ccli"></a>Zestawy o silnych nazwach (podpisywanie zestawów) (C++/CLI)

W tym temacie omówiono, jak zarejestrować zestaw, często nazywane zapewniając zestawu z silną nazwą.

## <a name="remarks"></a>Uwagi

Korzystając z języka Visual C++, użyj opcji konsolidatora się swoim zestawie, aby uniknąć problemów związanych z atrybuty CLR podpisywanie zestawów:

- <xref:System.Reflection.AssemblyDelaySignAttribute>

- <xref:System.Reflection.AssemblyKeyFileAttribute>

- <xref:System.Reflection.AssemblyKeyNameAttribute>

Nie przy użyciu atrybutów przyczyny fakt, że nazwa klucza jest widoczne w metadanych zestawu, który może stanowić zagrożenie bezpieczeństwa, jeśli nazwa pliku zawiera poufne informacje. Ponadto proces kompilacji używany przez środowisko projektowe Visual C++ spowoduje unieważnienie klucz za pomocą którego zestaw jest podpisany, jeśli użyć atrybuty CLR, aby nadać zestawu z silną nazwą, a następnie uruchom narzędzie przetwarzania końcowego, takie jak mt.exe w zestawie.

Jeśli kompilacji w wierszu polecenia, użyj opcji konsolidatora, aby podpisać zestaw, a następnie uruchom narzędzie przetwarzania końcowego (np. mt.exe), należy ponownie podpisać zestaw za pomocą sn.exe. Alternatywnie możesz tworzyć i opóźnić podpisanie zestawu i po uruchomieniu narzędzia przetwarzania końcowego, wykonać podpisywania.

Jeśli używasz atrybutów podpisywania podczas kompilowania w środowisku deweloperskim, można pomyślnie Podpisz zestaw przez jawne wywołanie sn.exe ([Sn.exe (narzędzie silnych nazw)](/dotnet/framework/tools/sn-exe-strong-name-tool)) w zdarzeniu po kompilacji. Aby uzyskać więcej informacji, zobacz [określanie zdarzeń kompilacji](../ide/specifying-build-events.md). Czasy kompilacji może być niższa, jeśli używasz atrybutów i zdarzenie po kompilacji, w porównaniu z użyciem opcji konsolidatora.

Następujące opcje konsolidatora, obsługują podpisywanie zestawów:

- [/DELAYSIGN (Częściowo podpisz zestaw)](../build/reference/delaysign-partially-sign-an-assembly.md)

- [/KEYFILE (Określ klucz lub parę kluczy, aby podpisać zestaw)](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER (Określ klucz kontenera, aby podpisać zestaw)](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

Aby uzyskać więcej informacji na zestawy o silnych zobacz [tworzenie i zestawy Using Strong-Named](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).

## <a name="see-also"></a>Zobacz także

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
