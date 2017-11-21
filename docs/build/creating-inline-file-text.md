---
title: Tworzenie tekstu pliku wbudowanego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 174160657e5494f5566fd0828815b3c0f1b3d601
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Pliki wbudowane w pliku reguł programu make](../build/inline-files-in-a-makefile.md)