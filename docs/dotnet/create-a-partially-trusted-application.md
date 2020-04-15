---
title: 'Jak: Tworzenie częściowo zaufanej aplikacji (C++/CLI)'
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
ms.openlocfilehash: 9df3a751f4073472b9495425599aaf43878db99a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364401"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>Porady: tworzenie aplikacji częściowo zaufanej przez usunięcie zależności od biblioteki DLL środowiska CRT

W tym temacie omówiono sposób tworzenia częściowo zaufanej aplikacji wspólnego środowiska uruchomieniowego języka przy użyciu języka Visual C++ przez usunięcie zależności od pliku msvcm90.dll.

Aplikacja Visual C++ zbudowana z **/clr** będzie miała zależność od pliku msvcm90.dll, która jest częścią biblioteki C-Runtime. Jeśli chcesz, aby aplikacja była używana w środowisku częściowego zaufania, środowisko CLR wymusi pewne reguły zabezpieczeń dostępu do kodu na biblioteki DLL. W związku z tym konieczne będzie usunięcie tej zależności, ponieważ msvcm90.dll zawiera kod macierzysty i nie można wymusić na niej zasad zabezpieczeń dostępu do kodu.

Jeśli aplikacja nie korzysta z żadnych funkcji biblioteki C-Runtime i chcesz usunąć zależność od tej biblioteki z kodu, należy użyć **/NODEFAULTLIB:msvcmrt.lib** linker opcji i połączyć z ptrustm.lib lub ptrustmd.lib. Biblioteki te zawierają pliki obiektów do inicjowania i uninitialization aplikacji, klasy wyjątków używane przez kod inicjowania i kod obsługi wyjątków zarządzanych. Łączenie w jednej z tych bibliotek spowoduje usunięcie wszelkiej zależności od pliku msvcm90.dll.

> [!NOTE]
> Kolejność niezainicjalizacji zestawu może się różnić w przypadku aplikacji korzystających z bibliotek ptrust. W przypadku zwykłych aplikacji zestawy są zwykle zwalniane w odwrotnej kolejności, w jakiej są ładowane, ale nie jest to gwarantowane. W przypadku aplikacji częściowego zaufania zestawy są zwykle zwalniane w tej samej kolejności, w jakiej są ładowane. To również nie jest gwarantowane.

### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>Aby utworzyć częściowo zaufaną aplikację mieszaną (/clr)

1. Aby usunąć zależność od pliku msvcm90.dll, należy określić konsolidator, aby nie dołączał tej biblioteki przy użyciu opcji **/NODEFAULTLIB:msvcmrt.lib.** Aby uzyskać informacje na temat tego, jak to zrobić za pomocą środowiska programistycznego programu Visual Studio lub programowo, zobacz [/NODEFAULTLIB (Ignoruj biblioteki).](../build/reference/nodefaultlib-ignore-libraries.md)

1. Dodaj jedną z bibliotek ptrustm do zależności wejściowych konsolidatora. Użyj ptrustm.lib, jeśli budujesz aplikację w trybie zwalniania. W trybie debugowania należy użyć pliku ptrustmd.lib. Aby uzyskać informacje na temat tego, jak to zrobić przy użyciu środowiska programistycznego programu Visual Studio lub programowo, zobacz [. Lib Files as Linker Input](../build/reference/dot-lib-files-as-linker-input.md).

## <a name="see-also"></a>Zobacz też

[Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[Inicjowanie zespołów mieszanych](../dotnet/initialization-of-mixed-assemblies.md)<br/>
[Obsługa bibliotek dla zestawów mieszanych](../dotnet/library-support-for-mixed-assemblies.md)<br/>
[/link (Przepuść opcje do konsolidatora)](../build/reference/link-pass-options-to-linker.md)
