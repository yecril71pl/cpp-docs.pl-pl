---
title: Określanie pliku wbudowanego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ef2183390b2aca2fb54e1468bd59e697374a355a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-an-inline-file"></a>Określanie pliku wbudowanego
Określ dwa nawiasy (<<) w poleceniu gdzie *filename* ma być wyświetlony. Nawiasu ostrego nie może być rozwinięciu makra.  
  
## <a name="syntax"></a>Składnia  
  
```  
<<[filename]  
```  
  
## <a name="remarks"></a>Uwagi  
 Po uruchomieniu polecenia nawiasu ostrego są zastępowane przez *filename*, jeśli określona wartość, lub o unikatowej nazwie wygenerowany NMAKE. Jeśli zostanie określona, *filename* nawiasy bez spację lub tabulator muszą być zgodne. Ścieżka jest dozwolone. Rozszerzenie nie jest wymagane lub zakłada, że. Jeśli *filename* została określona, plik jest tworzony w bieżącej lub określony katalog, zastępując istniejące plik o takiej nazwie; w przeciwnym razie jest tworzony w katalogu TMP (lub bieżącego katalogu, jeśli zmienna środowiskowa TMP nie zdefiniowano). Jeśli poprzednie *filename* jest używane ponownie, NMAKE zastępuje poprzedniego pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki wbudowane w pliku reguł programu Make](../build/inline-files-in-a-makefile.md)