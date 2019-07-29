---
title: Strony właściwości HLSL
ms.date: 07/24/2019
ms.assetid: 0c65f5ec-a2a5-4f5b-8d4c-fa57113a5a1d
f1_keywords:
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.SuppressStartupBanner
- VC.Project.FXCompilerTool.EntryPointName
- VC.Project.FXCompilerTool.TreatWarningAsError
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.AllResourcesBound
- VC.Project.FXCompilerTool.EnableUnboundedDescriptorTables
- VC.Project.FXCompilerTool.SetRootSignature
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.AdditionalOptionsPage
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.AssemblerOutputFile
- VC.Project.FXCompilerTool.CompileD2DCustomEffect
- VC.Project.FXCompilerTool.MultiProcFXC
ms.openlocfilehash: a45ae433e5adaa8aeaf32215d4af7ad0a247af04
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606399"
---
# <a name="hlsl-compiler-property-pages"></a>Strony właściwości kompilatora HLSL

Korzystając ze stron właściwości kompilatora HLSL (fxc. exe), można skonfigurować sposób kompilowania pojedynczych plików modułu cieniującego HLSL. Można również określić argumenty wiersza polecenia do kompilatora HLSL, używając właściwości **dodatkowe opcje** strony właściwości **wiersza polecenia** . dotyczy to również argumentów, których nie można skonfigurować przy użyciu innych właściwości stron właściwości HLSL. Aby uzyskać informacje na temat kompilatora HLSL, zobacz [efekty — narzędzie kompilatora](https://go.microsoft.com/fwlink/p/?LinkID=258285&clcid=0x409)

## <a name="hlsl-general-property-page"></a>Ogólna strona właściwości HLSL

### <a name="additional-include-directories"></a>Dodatkowe katalogi dołączane

Określa co najmniej jeden katalog do dodania do ścieżki dołączania; Oddzielaj średnikami, jeśli więcej niż jeden. (/I [ścieżka])

### <a name="entrypoint-name"></a>Nazwa punktu wejścia

Określa nazwę punktu wejścia dla programu do cieniowania (/E [nazwa])

### <a name="disable-optimizations"></a>Wyłącz optymalizacje

**Tak (/od)** aby wyłączyć optymalizacje; w przeciwnym razie **nie**. Domyślnie wartość to **Yes (/od)** dla konfiguracji **debugowania** i **nie** dla konfiguracji **wydania** .

Argument wiersza polecenia **/od** do kompilatora HLSL niejawnie stosuje argument wiersza polecenia **/GFP** , ale dane wyjściowe nie mogą być identyczne z danymi wyjściowymi, które są tworzone przez przekazanie argumentów wiersza polecenia **/od** i **/GFP** bezpośredniego.

### <a name="enable-debugging-information"></a>Włącz informacje o debugowaniu

**Tak (/ZI)** , aby włączyć informacje debugowania; w przeciwnym razie **nie**. Domyślnie wartość to **Yes (/ZI)** dla konfiguracji **debugowania** i **nie** dla konfiguracji **wydania** .

### <a name="shader-type"></a>Typ cieniowania

Określa typ cieniowania. Różne rodzaje programów do cieniowania implementują różne części potoku grafiki. Niektóre rodzaje programów do cieniowania są dostępne tylko w nowszych modelach cieniowania (które są określone przez właściwość **model** programu do cieniowania) — na przykład cieniowanie obliczeń zostało wprowadzone w modelu modułu cieniującego 5.

Ta właściwość odpowiada  **\[części typu]** elementu **/t \[Type] _\[model]** argumentu wiersza polecenia do kompilatora HLSL. Właściwość **modele cieniowania** określa część **[model]** argumentu.

**Decyzji**

- **Efekt**
- **Program do cieniowania wierzchołków**
- **Program do cieniowania pikseli**
- **Cieniowanie geometrii**
- **Program do cieniowania kadłuba**
- **Program do cieniowania domeny**
- **Program do cieniowania obliczeń**
- **Biblioteka**
- **Generuj obiekt sygnatury głównej**

### <a name="shader-model"></a>Model programu do cieniowania

Określa model programu do cieniowania. Różne modele cieniowania mają różne możliwości. Ogólnie rzecz biorąc, nowsze modele cieniowania oferują rozszerzone możliwości, ale wymagają bardziej nowoczesnego sprzętu graficznego do uruchamiania kodu programu do cieniowania. Niektóre rodzaje programów do cieniowania (które są określone przez właściwość **Typ** programu do cieniowania) są dostępne tylko w nowszych modelach cieniowania — na przykład cieniowanie obliczeń zostało wprowadzone w modelu modułu cieniującego 5.

Ta właściwość odnosi się do  **\[części model]** argumentu wiersza **polecenia \[/t Type]\[_ model]** do kompilatora HLSL. Właściwość **typu** programu do cieniowania określa część **[Type]** argumentu.

### <a name="all-resources-bound"></a>Powiązano wszystkie zasoby

Kompilator zakłada, że wszystkie zasoby, które mogą odwoływać się do programu do cieniowania, są powiązane i są w dobrym stanie na czas trwania wykonywania programu do cieniowania (/all_resources_bound). Dostępne dla modelu modułu cieniującego 5,1 lub nowszego.

### <a name="enable-unbounded-descriptor-tables"></a>Włącz niepowiązane tabele deskryptorów

Informowanie kompilatora, że program do cieniowania może zawierać deklarację tablicy zasobów z nieograniczonym zakresem (/enable_unbounded_descriptor_tables). Dostępne dla modelu modułu cieniującego 5,1 lub nowszego.

### <a name="set-root-signature"></a>Ustaw sygnaturę główną

Dołącz sygnaturę główną do kodu bajtowego modułu cieniującego (/setrootsignature). Dostępne dla modelu modułu cieniującego 5,0 lub nowszego.

### <a name="preprocessor-definitions"></a>Definicje preprocesora

Dodaje co najmniej jedną definicję symbolu preprocesora, która ma zostać zastosowana do pliku kodu źródłowego HLSL. Użyj średników, aby oddzielić definicje symboli.

Ta właściwość odnosi się do argumentu wiersza polecenia  **\[/d definicje]** do kompilatora HLSL.

### <a name="compile-a-direct2d-custom-pixel-shader-effect"></a>Kompiluj niestandardowy efekt programu do cieniowania pikseli Direct2D

Kompiluj niestandardowy efekt Direct2D, który zawiera cieniowanie pikseli. Nie należy używać dla efektu niestandardowego wierzchołka ani obliczeń.

### <a name="multi-processor-compilation"></a>Kompilacja wieloprocesorowa

Uruchom jednocześnie wiele wystąpień.

## <a name="advanced-property-page"></a>Zaawansowana Strona właściwości

### <a name="suppress-startup-banner"></a>Pomiń transparent startowy

Pomija wyświetlanie transparentu startowego i komunikatu informacyjnego. /nologo

### <a name="treat-warnings-as-errors"></a>Traktuj ostrzeżenia jako błędy

Traktuje wszystkie ostrzeżenia kompilatora jako błędy. W przypadku nowego projektu najlepiej jest używać/WX we wszystkich kompilacjach. rozwiązanie wszystkich ostrzeżeń zapewni najmniejszą możliwą trudną do znalezienia wady kodu.

## <a name="output-files-property-page"></a>Strona właściwości plików wyjściowych

### <a name="header-variable-name"></a>Nazwa zmiennej nagłówka

Określa nazwę zmiennej w pliku nagłówkowym (/vn [nazwa])

### <a name="header-file-name"></a>Nazwa pliku nagłówka

Określa nazwę pliku nagłówkowego zawierającego kod obiektu. (/FH [nazwa])

### <a name="object-file-name"></a>Nazwa pliku obiektu

Określa nazwę pliku obiektu. (/Fo [nazwa])

### <a name="assembler-output"></a>Dane wyjściowe asemblera

Określa zawartość pliku wyjściowego języka asemblera. (/FC,/FX)

**Decyzji**

- **Brak listy** — brak listy.
- **Lista** — plik kodu zestawu
- **Kod zestawu i** kod szesnastkowy oraz plik listy szesnastkowej

### <a name="assembler-output-file"></a>Plik wyjściowy asemblera

Określa nazwę pliku dla pliku listy kodu zestawu

## <a name="see-also"></a>Zobacz także

[C++odwołanie do strony właściwości projektu](property-pages-visual-cpp.md)<br>
[Strony właściwości wiersza polecenia](command-line-property-pages.md)<br>
[Kompilowanie programów do cieniowania](https://go.microsoft.com/fwlink/p/?LinkID=258284&clcid=0x409)
