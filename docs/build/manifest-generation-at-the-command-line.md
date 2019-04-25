---
title: Generowanie manifestu w wierszu polecenia
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
ms.openlocfilehash: 37036ceedc59e20374fd1106a051ab2a66edd143
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273779"
---
# <a name="manifest-generation-at-the-command-line"></a>Generowanie manifestu w wierszu polecenia

Podczas kompilowania aplikacji C/C++ z poziomu wiersza polecenia przy użyciu nmake lub podobnego narzędzia, manifest jest generowany po konsolidator jest przetwarzane wszystkie pliki obiektów i wbudowane końcowym pliku binarnym. Konsolidator zbiera informacje o zestawie, przechowywane w plikach obiektowych i łączy te informacje do końcowego pliku manifestu. Domyślnie konsolidator wygeneruje plik o nazwie *binary_name*. *rozszerzenie*manifest do opisania końcowym pliku binarnym. Konsolidator nie można osadzić pliku manifestu wewnątrz pliku binarnego i może generować jedynie jako zewnętrznego pliku manifestu. Istnieje kilka sposobów osadzanie manifestu w końcowym pliku binarnym, takiej jak [narzędziu manifestu (mt.exe)](https://msdn.microsoft.com/library/aa375649) lub kompilowanie manifestu do pliku zasobów. Należy pamiętać, że określone zasady muszą być przestrzegane podczas osadzania manifestu w końcowym pliku binarnym, aby umożliwić takie funkcje jak łączenie przyrostowe podpisywania, i Edytuj i Kontynuuj. Te i inne opcje, które zostały omówione w [jak: Osadzanie manifestu w aplikacji C/C++](how-to-embed-a-manifest-inside-a-c-cpp-application.md) podczas kompilowania w wierszu polecenia.

## <a name="see-also"></a>Zobacz także

[Manifesty](/windows/desktop/sbscs/manifests)<br/>
[/INCREMENTAL (Łącz stopniowo)](reference/incremental-link-incrementally.md)<br/>
[Zestawy o silnych nazwach (podpisywanie zestawów) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)<br/>
[Edytuj i kontynuuj](/visualstudio/debugger/edit-and-continue)<br/>
[Ogólne informacje o tworzeniu manifestu dla programów C/C++](understanding-manifest-generation-for-c-cpp-programs.md)<br/>
