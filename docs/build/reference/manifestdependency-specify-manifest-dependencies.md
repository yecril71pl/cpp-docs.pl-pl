---
title: /MANIFESTDEPENDENCY (Określ zależności manifestu)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalManifestDependencies
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
ms.openlocfilehash: 43239efe70cc555d1a7e03c5d67e99e40ccd480e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492708"
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY (Określ zależności manifestu)

```
/MANIFESTDEPENDENCY:manifest_dependency
```

## <a name="remarks"></a>Uwagi

/MANIFESTDEPENDENCY umożliwia określenie atrybutów, które zostaną umieszczone w \<sekcji zależności > pliku manifestu.

Aby uzyskać informacje na temat sposobu tworzenia pliku manifestu, zobacz [/manifest (Tworzenie manifestu zestawu side-by-Side)](manifest-create-side-by-side-assembly-manifest.md) .

Aby uzyskać więcej informacji na \<temat zależności > w pliku manifestu, zobacz [pliki konfiguracji wydawcy](/windows/win32/SbsCs/publisher-configuration-files).

Informacje/MANIFESTDEPENDENCY można przesłać do konsolidatora na jeden z dwóch sposobów:

- Bezpośrednio w wierszu polecenia (lub w pliku odpowiedzi) z/MANIFESTDEPENDENCY.

- Za pomocą [](../../preprocessor/comment-c-cpp.md) dyrektywy pragma komentarza.

Poniższy przykład pokazuje komentarz/MANIFESTDEPENDENCY przekazana za pośrednictwem dyrektywy pragma.

```cpp
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")
```

co spowoduje, że w pliku manifestu zostanie umieszczony następujący wpis:

```xml
<dependency>
  <dependentAssembly>
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />
  </dependentAssembly>
</dependency>
```

Te same Komentarze/MANIFESTDEPENDENCY można przesłać w wierszu polecenia w następujący sposób:

```cmd
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"
```

Konsolidator będzie zbierać Komentarze/MANIFESTDEPENDENCY, eliminować zduplikowane wpisy, a następnie dodać otrzymany ciąg XML do pliku manifestu.  Jeśli konsolidator znajdzie wpisy powodujące konflikt, plik manifestu zostanie uszkodzony i aplikacja nie zostanie uruchomiona (można dodać wpis do dziennika zdarzeń, wskazując Źródło błędu).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz pozycję **Właściwości** > konfiguracji Strona właściwości**pliku manifestu** **konsolidatora** > .

1. Zmodyfikuj **dodatkową właściwość zależności manifestu** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
