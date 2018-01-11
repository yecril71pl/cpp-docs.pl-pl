---
title: "Składnia nazwy pliku CL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cl
dev_langs: C++
helpviewer_keywords:
- syntax, compiler filename
- paths, CL compiler filename syntax
- cl.exe compiler, filename syntax
- extensions, specifying to compiler
- file names [C++], CL compiler
- file names [C++]
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1fc9ce614cb67bef1904e8dc464402f362b0cbde
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cl-filename-syntax"></a>Składnia nazwy pliku CL
CL akceptuje pliki, których nazwy zgodne z konwencjami systemu plików NTFS, FAT i HPFS nazewnictwa. Nazwy pliku może zawierać ścieżki pełnej lub częściowej. Pełna ścieżka zawiera nazwę dysku i co najmniej jedną nazwę katalogu. CL akceptuje nazw plików rozdzielonych przez ukośników odwrotnych (\\) lub przesyłane ukośnikami (/). Nazwy zawierające spacje muszą być ujęte w znaki podwójnego cudzysłowu. Ścieżka częściowa pomija nazwa dysku CL zakłada się na bieżącym dysku. Jeśli nie określisz ścieżkę CL przyjęto założenie, że plik znajduje się w bieżącym katalogu.  
  
 Rozszerzenie nazwy pliku Określa, jak są przetwarzane pliki. C i C++ pliki, które mają rozszerzenia rozszerzenia c, .cxx lub cpp, są kompilowane. Inne pliki, w tym pliki .obj, bibliotek (lib) i pliki definicji modułu (.def), są przekazywane do konsolidatora bez przetwarzane.  
  
## <a name="see-also"></a>Zobacz też  
 [Składnia wiersza polecenia kompilatora](../../build/reference/compiler-command-line-syntax.md)