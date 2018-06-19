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
ms.openlocfilehash: 7f740030e48a33284a31da4ebd46f0c4d7b6ac7e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368502"
---
# <a name="manifest-generation-at-the-command-line"></a>Generowanie manifestu w wierszu polecenia
Podczas kompilowania aplikacji C/C++ za pomocą nmake lub podobne narzędzia wiersza polecenia, po konsolidator ma przetwarzane wszystkie pliki obiektu i utworzony plik binarny końcowego jest tworzony plik manifestu. Konsolidator zbiera informacje o zestawie zapisanych w plikach obiektu i scala te informacje w końcowym pliku manifestu. Domyślnie konsolidator wygeneruje plik o nazwie < binary_name >. \<rozszerzenia > manifest do opisywania końcowego pliku binarnego. Konsolidator nie można osadzić pliku manifestu w danych binarnych i można generować tylko jako zewnętrzny plik manifestu. Istnieje kilka sposobów osadzanie manifestu w końcowym binarnego, takich jak przy użyciu [narzędziu manifestu (mt.exe)](http://msdn.microsoft.com/library/aa375649) lub kompilowanie manifestu do pliku zasobów. Należy pamiętać, że określone zasady muszą być przestrzegane podczas osadzania manifestu w końcowym pliku binarnego do Włącz takie funkcje jak konsolidowania przyrostowego podpisywanie i Edytuj i Kontynuuj. Te i inne opcje, które zostały omówione w [porady: osadzanie manifestu w aplikacji C/C++](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md) podczas kompilowania w wierszu polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Manifesty](http://msdn.microsoft.com/library/aa375365)   
 [/ INCREMENTAL (łącz stopniowo)](../build/reference/incremental-link-incrementally.md)   
 [Silnych nazwach (podpisywanie zestawów) (C + +/ CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)   
 [Edytuj i Kontynuuj](/visualstudio/debugger/edit-and-continue)   
 [Ogólne informacje o tworzeniu manifestu dla programów C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)