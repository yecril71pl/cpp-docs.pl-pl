---
title: Tworzenie tekstu pliku wbudowanego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dcc27a303e9d03d2e899a76703bcfae5abfd0c04
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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