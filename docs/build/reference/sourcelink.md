---
title: /SOURCELINK (Uwzględnij plik Sourcelink w pliku PDB)
description: Przewodnik po opcji /SOURCELINK w programie Microsoft C++.
ms.date: 03/31/2020
f1_keywords:
- /sourcelink
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
ms.openlocfilehash: bde55c401e17f7b3c84ffcdad29dda2badcc260b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336068"
---
# <a name="sourcelink-include-source-link-file-in-pdb"></a>/SOURCELINK (dołącz plik łącza źródłowego w PDB)

Określa plik konfiguracyjny łącza źródłowego do uwzględnienia w pliku PDB wygenerowanym przez konsolidator.

## <a name="syntax"></a>Składnia

> **`/SOURCELINK:`**_`filename`_

## <a name="arguments"></a>Argumenty

*Pod nazwą*<br/>
Określa plik konfiguracyjny w formacie JSON, który zawiera proste mapowanie lokalnych ścieżek plików do adresów URL plików źródłowych do wyświetlenia w debugerze. Aby uzyskać więcej informacji na temat formatu tego pliku, zobacz [Schemat JSON łącza źródłowego](https://github.com/dotnet/designs/blob/master/accepted/2020/diagnostics/source-link.md#source-link-json-schema).

## <a name="remarks"></a>Uwagi

Source Link to system niezależny od kontroli języka i źródła do dostarczania debugowania źródłowego dla plików binarnych. Źródło Łącze jest obsługiwany dla natywnych plików binarnych języka C++, począwszy od programu Visual Studio 2017 w wersji 15.8. Aby uzyskać omówienie łącza źródłowego, zobacz [Łącze źródłowe](https://github.com/dotnet/designs/blob/master/accepted/2020/diagnostics/source-link.md). Aby uzyskać informacje na temat używania łącza źródłowego w projektach i sposobu generowania pliku SourceLink w ramach projektu, zobacz [Korzystanie z łącza źródłowego](https://github.com/dotnet/sourcelink#using-source-link-in-c-projects).

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>Aby ustawić opcję /SOURCELINK w programie Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** dla projektu. Aby uzyskać więcej informacji, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Wybierz stronę właściwości**wiersza polecenia wiersza**  > **konsolidatora** >  **właściwości konfiguracji.**

1. W polu **Dodatkowe** opcje **`/SOURCELINK:`** _`filename`_ dodaj, a następnie wybierz pozycję **OK** lub **Zastosuj,** aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Ta opcja nie ma odpowiednika programowego.

## <a name="see-also"></a>Zobacz też

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
