---
title: Silnych nazwach (podpisywanie zestawów) (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assemblies [C++]
- signing assemblies
- .NET Framework [C++], assembly signing
- assemblies [C++], signing
- linker [C++], assembly signing
- strong-named assemblies [C++]
ms.assetid: c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5d7ae911d2572a35ee8dbb21d5484b4679b64c4d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169195"
---
# <a name="strong-name-assemblies-assembly-signing-ccli"></a>Zestawy o silnych nazwach (podpisywanie zestawów) (C++/CLI)
W tym temacie opisano, jak można podpisać zestawu często określany jako nadanie używanemu zestawowi silną nazwę.  
  
## <a name="remarks"></a>Uwagi  
 Korzystając z języka Visual C++, należy użyć opcji konsolidatora do podpisywania używanego zestawu, aby uniknąć problemów związanych z atrybuty CLR dotyczące podpisywanie zestawu:  
  
-   <xref:System.Reflection.AssemblyDelaySignAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyFileAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyNameAttribute>  
  
 Nie przy użyciu atrybutów przyczyny fakt, że nazwa klucza jest widoczna w metadanych zestawu, który może stanowić zagrożenie bezpieczeństwa, jeśli nazwa pliku zawiera poufne informacje. Ponadto procesu tworzenia używane przez środowisko projektowe Visual C++ spowoduje unieważnienie klucza, z którym zestaw jest podpisany, jeśli można użyć atrybuty CLR, aby nadać silnej nazwy zestawu, a następnie uruchom przetwarzanie końcowe narzędzia, takiego jak mt.exe w zestawie.  
  
 Jeśli kompilacji w wierszu polecenia, użyj opcji konsolidatora do podpisywania używanego zestawu, a następnie uruchom narzędzie przetwarzania końcowego (na przykład mt.exe), konieczne będzie ponowne podpisanie zestawu z sn.exe. Alternatywnie możesz skompilować i opóźnienie Podpisz zestaw z i po uruchomieniu narzędzia przetwarzania końcowego należy zakończyć podpisywania.  
  
 Jeśli używasz podpisywania atrybutów podczas kompilowania w środowisku programistycznym, można pomyślnie Podpisz zestaw jawnie wywołując sn.exe ([Sn.exe (narzędzie silnej nazwy)](/dotnet/framework/tools/sn-exe-strong-name-tool)) w zdarzenia postkompilacyjnego. Aby uzyskać więcej informacji, zobacz [określanie zdarzeń kompilacji](../ide/specifying-build-events.md). Czas kompilacji może być mniejsza, atrybuty i zdarzenia postkompilacyjnego, w porównaniu z użyciem opcji konsolidatora za pomocą.  
  
 Następujące opcje konsolidatora obsługują podpisywanie zestawu:  
  
-   [/DELAYSIGN (Częściowo podpisz zestaw)](../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/KEYFILE (Określ klucz lub parę kluczy, aby podpisać zestaw)](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/KEYCONTAINER (Określ klucz kontenera, aby podpisać zestaw)](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 Aby uzyskać więcej informacji na silne zestawy, zobacz [tworzenie i zestawy Using Strong-Named](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)