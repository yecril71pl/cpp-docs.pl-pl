---
title: Tworzenie tekstu pliku wbudowanego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ab1154935ac4eb8b0595c84ba8d75a9ca13e4d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="creating-inline-file-text"></a>Tworzenie tekstu pliku wbudowanego
Pliki śródwierszowe są tymczasowe i stałe.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      inlinetext  
.  
.  
.  
<<[KEEP | NOKEEP]  
```  
  
## <a name="remarks"></a>Uwagi  
 Określ *inlinetext* w pierwszym wierszu po poleceniu. Oznacz elementu end z podwójne nawiasy (<<) na początku w osobnym wierszu. Plik zawiera wszystkie *inlinetext* przed rozdzielające nawiasy kwadratowe. *Inlinetext* mogą mieć rozwinięcia makra są i podstawień, ale nie dyrektywy lub komentarze pliku reguł programu make. Spacje, tabulatory i znaki nowego wiersza są traktowane jako literału.  
  
 Plik tymczasowy istnieje podczas sesji i mogą być ponownie używane przez inne polecenia. Określ **zachować** po zamykającego nawiasu ostrego zachowania plik po sesji NMAKE; bez nazwy pliku jest zachowywany na dysku z nazwą wygenerowanego pliku. Określ **NOKEEP** lub Brak pliku tymczasowego. **Zachowaj** i **NOKEEP** nie jest uwzględniana wielkość liter.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki wbudowane w pliku reguł programu Make](../build/inline-files-in-a-makefile.md)