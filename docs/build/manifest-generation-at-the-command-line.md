---
title: Generowanie manifestu w wierszu polecenia
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
ms.openlocfilehash: 381406213422e286dd9aba26adcdbd6caff7bfe3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493203"
---
# <a name="manifest-generation-at-the-command-line"></a>Generowanie manifestu w wierszu polecenia

Podczas kompilowania aplikacji C/C++ z wiersza polecenia przy użyciu NMAKE lub podobnych narzędzi, Manifest jest generowany po przetworzeniu wszystkich plików obiektów i skompilowaniu końcowego pliku binarnego przez konsolidator. Konsolidator zbiera informacje zestawu przechowywane w plikach obiektów i łączy te informacje w końcowy plik manifestu. Domyślnie konsolidator generuje plik o nazwie *binary_name*. *Extension*. manifest, aby opisać końcowy plik binarny. Konsolidator nie osadza pliku manifestu wewnątrz danych binarnych i może generować tylko manifest jako plik zewnętrzny. Istnieje kilka sposobów osadzenia manifestu w końcowym pliku binarnym, na przykład przy użyciu [narzędzia manifestu (Mt. exe)](/windows/win32/sbscs/mt-exe) lub kompilowania manifestu w plik zasobów. Należy pamiętać, że po osadzeniu manifestu w końcowym pliku binarnym należy przestrzegać określonych reguł, aby umożliwić takie funkcje jak łączenie przyrostowe, podpisywanie i edytowanie i kontynuowanie. Te i inne opcje zostały omówione w temacie [: osadzanie manifestu w aplikacji C/C++](how-to-embed-a-manifest-inside-a-c-cpp-application.md) podczas kompilowania w wierszu polecenia.

## <a name="see-also"></a>Zobacz też

[Manifesty](/windows/win32/sbscs/manifests)<br/>
[/INCREMENTAL (Łącz stopniowo)](reference/incremental-link-incrementally.md)<br/>
[Zestawy o silnych nazwach (podpisywanie zestawów) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)<br/>
[Edytuj i Kontynuuj](/visualstudio/debugger/edit-and-continue)<br/>
[Ogólne informacje o tworzeniu manifestu dla programów C/C++](understanding-manifest-generation-for-c-cpp-programs.md)<br/>
