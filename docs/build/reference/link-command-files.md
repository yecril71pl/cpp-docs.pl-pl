---
title: Pliki poleceń LINK | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- syntax, LINK command files
- command files [C++]
- LINK tool [C++]
- text files, passing arguments to LINK
- LINK tool [C++], command-line syntax
- command files [C++], LINK
ms.assetid: 7154511c-32b9-4e5b-a515-3922fa9de48e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8934758d8aa406ea7b7c959b1fc535cde32195b1
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894684"
---
# <a name="link-command-files"></a>Wiersze poleceń LINK

Argumenty wiersza polecenia można przekazać do LINKU w formie pliku polecenia. Aby określić plik poleceń do konsolidatora, użyj następującej składni:

> **ŁĄCZE \@**  <em>commandfile</em>

*Commandfile* to nazwa pliku tekstowego. Nie spacji lub tabulatorów jest dozwolone między znakiem (**\@**) i nazwę pliku. Nie ma rozszerzenia domyślną; należy określić pełną nazwę pliku, łącznie z dowolnym rozszerzeniem. Nie można używać symboli wieloznacznych. Można określić ścieżkę bezwzględną lub względną nazwę pliku. ŁĄCZE nie używa zmiennej środowiskowej, aby wyszukać ten plik.

W pliku poleceń argumenty mogą być oddzielone tabulacji lub spacji (jak w wierszu polecenia) i znaki nowego wiersza.

Całość lub część wiersza polecenia można określić w pliku poleceń. Można użyć więcej niż jeden plik polecenia za pomocą polecenia łącza. LINK akceptuje dane wejściowe plik poleceń tak, jakby zostały określone w tej lokalizacji, w wierszu polecenia. Pliki poleceń nie mogą być zagnieżdżone. LINK funkcją zawartość plików poleceń, chyba że [/nologo](../../build/reference/nologo-suppress-startup-banner-linker.md) określono opcję.

## <a name="example"></a>Przykład

Następujące polecenie, aby tworzyć biblioteki DLL przekazuje nazwy plików obiektów i bibliotek w plikach osobne polecenie i używa innego polecenia w pliku Specyfikacja opcji/EXPORTS:

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
[Opcje konsolidatora](../../build/reference/linker-options.md)