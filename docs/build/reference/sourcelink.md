---
title: / SOURCELINK (Sourcelink obejmują pliki w pliku PDB)
ms.date: 08/20/2018
f1_keywords:
- /sourcelink
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
ms.openlocfilehash: 1643727d8f556a905eccbfa9626d1aaa8ea63cbf
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816610"
---
# <a name="sourcelink-include-source-link-file-in-pdb"></a>/ SOURCELINK (zawierają Link źródłowy plik w pliku PDB)

Określa Link źródłowy plik konfiguracji do uwzględnienia w pliku PDB wygenerowany przez konsolidator.

## <a name="syntax"></a>Składnia

> **/ SOURCELINK:**_nazwy pliku_

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Określa sformatowanego JSON konfiguracji pliku, który zawiera prostego mapowanie ścieżki pliku lokalnego do adresów URL, gdzie można pobrać pliku źródłowego do wyświetlenia przez debuger. Aby uzyskać więcej informacji na temat formatu tego pliku, zobacz [schematu JSON Linku źródłowego](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md#source-link-json-schema).

## <a name="remarks"></a>Uwagi

Link źródłowy jest systemem niezależny od języka i kontroli źródła zapewniające debugowanie źródła dla danych binarnych. Link źródłowy jest obsługiwana dla natywnych plików binarnych języka C++, począwszy od programu Visual Studio 2017 w wersji 15.8. Aby uzyskać omówienie Linku źródłowego, zobacz [Linku źródłowego](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md). Informacje na temat sposobu używania Linku źródłowego w projektach i jak można wygenerować pliku SourceLink jako część projektu, zobacz [przy użyciu Linku źródłowego](https://github.com/dotnet/sourcelink#using-source-link-in-c-projects).

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>Aby ustawić opcję konsolidatora/sourcelink w programie Visual Studio

1. Otwórz **stron właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. W **dodatkowe opcje** Dodaj **/sourcelink:**_filename_ , a następnie wybierz **OK** lub **Zastosuj**Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Ta opcja nie ma programowy odpowiednik.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
