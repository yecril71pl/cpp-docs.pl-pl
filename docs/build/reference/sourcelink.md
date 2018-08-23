---
title: / SOURCELINK (Sourcelink obejmują pliki w pliku PDB) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/20/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /sourcelink
dev_langs:
- C++
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 876373b5646790f9f8de0042442b2ab56d9d2971
ms.sourcegitcommit: 7f3df9ff0310a4716b8136ca20deba699ca86c6c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "40242842"
---
# <a name="sourcelink-include-sourcelink-file-in-pdb"></a>/ SOURCELINK (Sourcelink obejmują pliki w pliku PDB)

Określa plik konfiguracji SourceLink do uwzględnienia w pliku PDB wygenerowany przez konsolidator.

## <a name="syntax"></a>Składnia

> **/ SOURCELINK:**_nazwy pliku_

## <a name="arguments"></a>Argumenty

*Nazwa pliku*  
Określa sformatowanego JSON konfiguracji pliku, który zawiera prostego mapowanie ścieżki pliku lokalnego do adresów URL, gdzie można pobrać pliku źródłowego do wyświetlenia przez debuger. Aby uzyskać więcej informacji na temat formatu tego pliku, zobacz [schematu JSON Linku źródłowego](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md#source-link-json-schema).

## <a name="remarks"></a>Uwagi

SourceLink jest systemem niezależny od języka i kontroli źródła, zapewniające debugowanie źródła dla danych binarnych. SourceLink jest obsługiwany dla natywnych plików binarnych języka C++, począwszy od programu Visual Studio 2017 w wersji 15.8. Aby zapoznać się z omówieniem SourceLink, zobacz [Linku źródłowego](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md). Informacje na temat sposobu używania SourceLink w swoich projektach i jak można wygenerować pliku SourceLink jako część projektu, zobacz [przy użyciu SourceLink](https://github.com/dotnet/sourcelink#using-sourcelink).

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>Aby ustawić opcję konsolidatora/sourcelink w programie Visual Studio

1. Otwórz **stron właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. W **dodatkowe opcje** Dodaj **/sourcelink:**_filename_ , a następnie wybierz **OK** lub **Zastosuj**Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
- Ta opcja nie ma programowy odpowiednik.

## <a name="see-also"></a>Zobacz także

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)  
[Opcje konsolidatora](../../build/reference/linker-options.md)  
