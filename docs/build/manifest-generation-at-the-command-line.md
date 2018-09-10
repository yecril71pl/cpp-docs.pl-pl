---
title: Generowanie manifestu w wierszu polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eaaebf02299f8f3907012ec97e467d137cbd246b
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315486"
---
# <a name="manifest-generation-at-the-command-line"></a>Generowanie manifestu w wierszu polecenia

Podczas kompilowania aplikacji C/C++ z poziomu wiersza polecenia przy użyciu nmake lub podobnego narzędzia, manifest jest generowany po konsolidator jest przetwarzane wszystkie pliki obiektów i wbudowane końcowym pliku binarnym. Konsolidator zbiera informacje o zestawie, przechowywane w plikach obiektowych i łączy te informacje do końcowego pliku manifestu. Domyślnie konsolidator wygeneruje plik o nazwie *binary_name*. *rozszerzenie*manifest do opisania końcowym pliku binarnym. Konsolidator nie można osadzić pliku manifestu wewnątrz pliku binarnego i może generować jedynie jako zewnętrznego pliku manifestu. Istnieje kilka sposobów osadzanie manifestu w końcowym pliku binarnym, takiej jak [narzędziu manifestu (mt.exe)](https://msdn.microsoft.com/library/aa375649) lub kompilowanie manifestu do pliku zasobów. Należy pamiętać, że określone zasady muszą być przestrzegane podczas osadzania manifestu w końcowym pliku binarnym, aby umożliwić takie funkcje jak łączenie przyrostowe podpisywania, i Edytuj i Kontynuuj. Te i inne opcje, które zostały omówione w [porady: osadzanie manifestu w aplikacji C/C++](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md) podczas kompilowania w wierszu polecenia.

## <a name="see-also"></a>Zobacz też

[Manifesty](https://msdn.microsoft.com/library/aa375365)<br/>
[/INCREMENTAL (Łącz stopniowo)](../build/reference/incremental-link-incrementally.md)<br/>
[Zestawy o silnych nazwach (podpisywanie zestawów) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)<br/>
[Edytuj i kontynuuj](/visualstudio/debugger/edit-and-continue)<br/>
[Ogólne informacje o tworzeniu manifestu dla programów C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)<br/>
