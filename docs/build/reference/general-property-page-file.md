---
title: Ogólna strona właściwości (plik)
ms.date: 08/30/2019
f1_keywords:
- VC.Project.VCFileConfiguration.ExcludedFromBuild
- VC.Project.VCFileConfiguration.Tool
ms.assetid: 26e3711e-9e7d-4e8d-bc4c-2474538efdad
ms.openlocfilehash: 41366e2eae479c3d00f79cc47da9100b22129d50
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218181"
---
# <a name="general-property-page-file"></a>Ogólna strona właściwości (plik)

Ten temat dotyczy projektów systemu Windows. W przypadku projektów z systemem innym niż Windows Zapoznaj się z informacjami na [stronie właściwości systemu Linux C++ ](../../linux/prop-pages-linux.md).

Po kliknięciu prawym przyciskiem myszy **Eksplorator rozwiązań**węzła pliku zostanie otwarta strona właściwości **Ogólne** pod węzłem **Właściwości konfiguracji** . Zawiera następujące właściwości:

- **Wykluczone z kompilacji**

   Określa, czy plik powinien być w kompilacji dla bieżącej konfiguracji.

   Aby programowo uzyskać dostęp do tej właściwości <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.ExcludedFromBuild%2A>, zobacz.

- **Zawartość** (Dotyczy tylko aplikacji platformy UWP). Określa, czy plik zawiera zawartość, która ma zostać uwzględniona w pakiecie aplikacji.

- **Typ elementu**

   **Typ elementu** określa narzędzie, które będzie używane do przetwarzania pliku podczas procesu kompilacji. [Pliki, których rozszerzenie jest znane dla programu Visual Studio](/visualstudio/extensibility/visual-cpp-project-extensibility?view=vs-2019#project-items) , ma wartość domyślną w tej właściwości. Możesz określić niestandardowe narzędzie w tym miejscu, jeśli masz niestandardowy typ pliku lub chcesz przesłonić domyślne narzędzie dla znanego typu plików. Aby uzyskać więcej informacji, zobacz [Określanie niestandardowych narzędzi kompilacji](../specifying-custom-build-tools.md) . Możesz również użyć tej strony właściwości, aby określić, że plik nie jest częścią procesu kompilacji.

   Na poniższej ilustracji przedstawiono stronę właściwości pliku *. cpp* . Domyślnym **typem elementu** tego rodzaju pliku jest **C/C++ kompilator** (*CL. exe*), a strona właściwości udostępnia różne ustawienia kompilatora, które mogą być stosowane tylko do tego pliku.

   ![Ogólna Strona właściwości dla elementu projektu](media/file-general-item-type.png "Opcje typu elementu")

    W poniższej tabeli wymieniono domyślne typy elementów:

    |Rozszerzenie pliku|Typ elementu|Narzędzie domyślne|
    |-|-|-|
    |. appx|Definicja aplikacji XAML|[Pakowarka aplikacji](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |. HLSL,. CSO|Kompilator HLSL|[fxc. exe](/windows/win32/direct3dtools/fxc)|
    |. h|C/C++ nagłówek|[Preprocesor języka C/C++](../../preprocessor/c-cpp-preprocessor-reference.md)|
    |n/d|Nie uczestniczy w kompilacji|n/d|
    |. XML,. XSLT,. xsl|Xml|[Edytor XML](/visualstudio/xml-tools/xml-editor)|
    |. resw,. resjson|Zasób PRI (platformy UWP Apps)|[Pliku MakePRI. exe](/windows/uwp/app-resources/compile-resources-manually-with-makepri)|
    ||Nośnik (platformy UWP)|[Pakowarka aplikacji](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |. xsd|Narzędzie Generator danych XML|[Narzędzie definicji schematu XML (XSD. exe)](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe) (Wymaga obciążenia .NET. Nie dołączono do MSVC.)|
    ||Narzędzie manifestu|[Mt. exe](/windows/win32/sbscs/mt-exe)|
    |. RC|Zasób|[Kompilator zasobów systemu Windows (RC. exe)](/windows/win32/menurc/resource-compiler)|
    |. appxmanifest|Manifest pakietu aplikacji|[Pakowarka aplikacji](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.obj|Obiekt|[C/C++ konsolidator (link. exe)](cl-invokes-the-linker.md)|
    |. ttf|Font|n/d|
    |. txt|Tekst|n/d|
    |n/d|Niestandardowe narzędzie kompilacji|Zdefiniowane przez użytkownika|
    |n/d|Kopiuj plik|n/d|
    |. packagelayout|Układ pakietu aplikacji|[Pakowarka aplikacji](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.resx|Zasób zarządzany przez kompilator|[Resgen.exe (generator pliku zasobów)](/dotnet/framework/tools/resgen-exe-resource-file-generator)|
    |. Natvis|C++Plik wizualizacji debugera|[Struktura Natvis](/visualstudio/debugger/create-custom-views-of-native-objects)|
    |. jpg,. bmp,. ico itd.|Obraz|Kompilator zasobów oparty na typie aplikacji.|
    |.cpp|Kompilator CC++ /|CL. exe|

   Aby programowo uzyskać dostęp do tej właściwości <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.Tool%2A>, zobacz.

Aby uzyskać informacje na temat uzyskiwania dostępu do strony właściwości **ogólnych** w węźle **Właściwości konfiguracji** , zobacz [Ustawianie C++ kompilatora i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

## <a name="see-also"></a>Zobacz także

[C++odwołanie do strony właściwości projektu](property-pages-visual-cpp.md)