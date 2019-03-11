---
title: 'Instrukcje: Tworzenie aplikacji częściowo zaufanej (C + +/ CLI)'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- partially trusted applications [C++]
- mixed assemblies [C++], partially trusted applications
- msvcm90[d].dll
- interoperability [C++], partially trusted applications
- interop [C++], partially trusted applications
- /clr compiler option [C++], partially trusted applications
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
ms.openlocfilehash: afdfb8ca11753d7def9d7da6f431082b1a90c345
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743762"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>Instrukcje: Tworzenie aplikacji częściowo zaufanej przez usunięcie zależności biblioteki DLL środowiska CRT

W tym temacie omówiono sposób tworzenia częściowo zaufanych aplikacji środowiska uruchomieniowego języka wspólnego przy użyciu języka Visual C++ przez usunięcie zależności od msvcm90.dll.

Aplikacji Visual C++ skompilowanych przy użyciu **/CLR** ma zależności od msvcm90.dll, który jest częścią biblioteki środowiska uruchomieniowego C. Aplikacja ma być używany w środowisku częściowej relacji zaufania, należy środowiska CLR będzie wymuszać biblioteki DLL niektóre zasady zabezpieczeń dostępu kodu. W związku z tym będzie trzeba usunąć tę zależność, ponieważ msvcm90.dll zawiera kod natywny, a nie można wymusić zasady zabezpieczeń dostępu kodu na nim.

Jeśli aplikacja nie używa żadnych funkcji biblioteki środowiska uruchomieniowego C i chcesz usunąć zależność tej biblioteki z kodu, będą musieli używać **/NODEFAULTLIB:msvcmrt.lib** — opcja konsolidatora i Połącz z biblioteką ptrustm.lib lub ptrustmd.lib. Biblioteki zawierają pliki obiektów do inicjowania i anulowania inicjowania aplikacji, klasy wyjątków używane przez kod inicjowania i zarządzanego kodu obsługi wyjątków. Łączenie w jednym z tych bibliotek spowoduje usunięcie wszelkich zależności od msvcm90.dll.

> [!NOTE]
>  Kolejność anulowania inicjowania zestawu mogą się różnić w przypadku aplikacji korzystających z bibliotek ptrust. Dla zwykłych aplikacji zestawy są zazwyczaj pozostaną niezaładowane w odwrotnej kolejności są one ładowane, ale nie jest to gwarantowane. W przypadku aplikacji częściowej relacji zaufania zestawy są zwykle pozostaną niezaładowane w tej samej kolejności, że są ładowane. W efekcie również nie jest gwarantowana.

### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>Do tworzenia częściowo zaufanych mieszany (/ clr) aplikacji

1. Aby usunąć zależności od msvcm90.dll, należy określić, aby konsolidator nie zawierają tej biblioteki za pomocą **/NODEFAULTLIB:msvcmrt.lib** — opcja konsolidatora. Aby uzyskać informacje o tym, jak to zrobić przy użyciu środowiska programistycznego Visual Studio lub programowo, zobacz [/nodefaultlib (Ignoruj biblioteki)](../build/reference/nodefaultlib-ignore-libraries.md).

1. Dodanie jednego z biblioteki ptrustm zależności wejściowe konsolidatora. Jeśli tworzysz aplikację w trybie wydania, należy użyć ptrustm.lib. Tryb debugowania można użyć ptrustmd.lib. Aby uzyskać informacje o tym, jak to zrobić przy użyciu środowiska programistycznego Visual Studio lub programowo, zobacz [. Pliki lib — wejście konsolidatora](../build/reference/dot-lib-files-as-linker-input.md).

## <a name="see-also"></a>Zobacz także

[Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[Inicjowanie zestawów mieszanych](../dotnet/initialization-of-mixed-assemblies.md)<br/>
[Obsługa bibliotek dla zestawów mieszanych](../dotnet/library-support-for-mixed-assemblies.md)<br/>
[/link (Przepuść opcje do konsolidatora)](../build/reference/link-pass-options-to-linker.md)
