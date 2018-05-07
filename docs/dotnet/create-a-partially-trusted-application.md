---
title: 'Porady: tworzenie aplikacji częściowo zaufanej (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- partially trusted applications [C++]
- mixed assemblies [C++], partially trusted applications
- msvcm90[d].dll
- interoperability [C++], partially trusted applications
- interop [C++], partially trusted applications
- /clr compiler option [C++], partially trusted applications
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a4a0a4b8b1045a9107158c6e67ecdfa7939b6a08
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>Porady: tworzenie aplikacji częściowo zaufanej przez usunięcie zależności od biblioteki DLL środowiska CRT
W tym temacie omówiono sposób tworzenia aplikacji środowisko uruchomieniowe języka wspólnego częściowo zaufanej przez usunięcie zależności msvcm90.dll przy użyciu programu Visual C++.  
  
 Skompilowanej za pomocą aplikacji Visual C++ **/CLR** będzie zależy od msvcm90.dll, która jest częścią biblioteki C Runtime. Aplikacji do użycia w środowisku częściowej relacji zaufania, należy CLR będzie wymuszać niektórych reguł zabezpieczeń dostępu kodu na biblioteki DLL. W związku z tym będzie trzeba usunąć tę zależność, ponieważ msvcm90.dll zawiera kodu macierzystego i nie można wymusić zasady zabezpieczeń dostępu kodu na nim.  
  
 Jeśli chcesz usunąć zależności do tej biblioteki w kodzie aplikacji nie korzystać z żadnej funkcji biblioteki C Runtime, trzeba będzie użyć **/NODEFAULTLIB:msvcmrt.lib** — opcja konsolidatora i powiązanie z ptrustm.lib lub ptrustmd.lib. Biblioteki zawierają pliki obiektu inicjowania i uninitialization aplikacji, używane przez kod inicjujący klasy wyjątków i zarządzany kod obsługi wyjątków. Łączenie w jednym z tych bibliotek spowoduje usunięcie jej zależności od msvcm90.dll.  
  
> [!NOTE]
>  Kolejność uninitialization zestawu mogą różnić się w przypadku aplikacji korzystających z bibliotek ptrust. Dla zwykłych aplikacji zestawy są zazwyczaj zwalnianie w odwrotnej kolejności, są one ładowane, ale to nie jest gwarantowana. Dla aplikacje częściowo zaufane zestawy są zazwyczaj zwalnianie w tej samej kolejności, że są załadowane. To, ponadto nie jest gwarantowana.  
  
### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>Do tworzenia częściowo zaufany mieszanego (/ clr) aplikacji  
  
1.  Aby usunąć zależność od msvcm90.dll, należy określić do konsolidatora nie, aby uwzględnić tę bibliotekę przy użyciu **/NODEFAULTLIB:msvcmrt.lib** — opcja konsolidatora. Aby uzyskać informacje o tym, jak to zrobić przy użyciu środowiska programowania Visual Studio lub programowo, zobacz [/nodefaultlib (Ignoruj biblioteki)](../build/reference/nodefaultlib-ignore-libraries.md).  
  
2.  Dodaj jednej z bibliotek ptrustm zależności wejściowe konsolidatora. Użyj ptrustm.lib, jeśli tworzysz aplikację w trybie przygotowania do wydania. Tryb debugowania można użyć ptrustmd.lib. Aby uzyskać informacje o tym, jak to zrobić przy użyciu środowiska programowania Visual Studio lub programowo, zobacz [. Lib pliki jako dane wejściowe konsolidatora](../build/reference/dot-lib-files-as-linker-input.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)   
 [Inicjalizacja zestawów mieszanych](../dotnet/initialization-of-mixed-assemblies.md)   
 [Obsługa bibliotek dla zestawów mieszanych](../dotnet/library-support-for-mixed-assemblies.md)   
 [/link (Przepuść opcje do konsolidatora)](../build/reference/link-pass-options-to-linker.md)   
