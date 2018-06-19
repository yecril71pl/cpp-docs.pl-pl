---
title: Składnia nazwy pliku CL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- syntax, compiler filename
- paths, CL compiler filename syntax
- cl.exe compiler, filename syntax
- extensions, specifying to compiler
- file names [C++], CL compiler
- file names [C++]
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 121cd8971be65e15ad6445cb347baf478046bf3e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370465"
---
# <a name="cl-filename-syntax"></a>Składnia nazwy pliku CL
CL akceptuje pliki, których nazwy zgodne z konwencjami systemu plików NTFS, FAT i HPFS nazewnictwa. Nazwy pliku może zawierać ścieżki pełnej lub częściowej. Pełna ścieżka zawiera nazwę dysku i co najmniej jedną nazwę katalogu. CL akceptuje nazw plików rozdzielonych przez ukośników odwrotnych (\\) lub przesyłane ukośnikami (/). Nazwy zawierające spacje muszą być ujęte w znaki podwójnego cudzysłowu. Ścieżka częściowa pomija nazwa dysku CL zakłada się na bieżącym dysku. Jeśli nie określisz ścieżkę CL przyjęto założenie, że plik znajduje się w bieżącym katalogu.  
  
 Rozszerzenie nazwy pliku Określa, jak są przetwarzane pliki. C i C++ pliki, które mają rozszerzenia rozszerzenia c, .cxx lub cpp, są kompilowane. Inne pliki, w tym pliki .obj, bibliotek (lib) i pliki definicji modułu (.def), są przekazywane do konsolidatora bez przetwarzane.  
  
## <a name="see-also"></a>Zobacz też  
 [Składnia wiersza polecenia kompilatora](../../build/reference/compiler-command-line-syntax.md)